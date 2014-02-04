https://graphite.mozilla.org/render?from=-60days&until=-59days&width=1800&height=900&target=stacked(sumSeries(hosts.bld-linux64-ec2-*_build_releng_*_mozilla_com.cpu.0.cpu.user))&target=stacked(sumSeries(hosts.bld-linux64-ec2-*_build_releng_*_mozilla_com.cpu.0.cpu.idle))

https://graphite.mozilla.org/render?from=-60days&until=-59days&width=1800&height=900&target=stacked(scale(sum(exclude(hosts.bld-linux64-ec2-0[0-9]*_build_releng_*_mozilla_com.cpu.*.cpu.*, "(idle|wait)")),0.25))&target=stacked(scale(sum(hosts.bld-linux64-ec2-0[0-9]*_build_releng_*_mozilla_com.cpu.*.cpu.idle), 0.125))&target=stacked(scale(sum(hosts.bld-linux64-ec2-0[0-9]*_build_releng_*_mozilla_com.cpu.*.cpu.wait), 0.125))

bld:
https://graphite.mozilla.org/render?from=-24hours&until=now&width=1800&height=900&target=stacked(scale(sum(exclude(hosts.bld-linux64-ec2-0[0-9]*_build_releng_*_mozilla_com.cpu.*.cpu.*, "(idle|wait)")),0.00250))&target=stacked(scale(sum(hosts.bld-linux64-ec2-0[0-9]*_build_releng_*_mozilla_com.cpu.*.cpu.idle), 0.00250))&target=stacked(scale(sum(hosts.bld-linux64-ec2-0[0-9]*_build_releng_*_mozilla_com.cpu.*.cpu.wait), 0.00250))

spot:
https://graphite.mozilla.org/render?from=-24hours&until=now&width=1800&height=900&target=stacked(scale(sum(exclude(hosts.try-linux64-spot-0[0-9]*_try_releng_*_mozilla_com.cpu.*.cpu.*, "(idle|wait)")),0.00250))&target=stacked(scale(sum(hosts.try-linux64-spot-0[0-9]*_try_releng_*_mozilla_com.cpu.*.cpu.idle), 0.00250))&target=stacked(scale(sum(hosts.try-linux64-spot-0[0-9]*_try_releng_*_mozilla_com.cpu.*.cpu.wait), 0.00250))

#WTF....steal is usually 2x overreported
#machine efficiency: number of slaves vs their efficiency
# subtract steal/idle/wait to see how much resources we are using more or less productively
#tests
https://graphite.mozilla.org/render?from=-24hours&until=now&width=1800&height=900&target=alias(scale(sum(sum(groupByNode(exclude(hosts.tst-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal)"), 1, "sum")),sum(groupByNode(scale(hosts.tst-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5),1,"sum"))),0.01), "number of slaves")&target=alias(stacked(avg(groupByNode(exclude(hosts.tst-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal|idle|wait)"), 1, "sum"))), "cpu busy")&target=alias(stacked(avg(groupByNode(hosts.tst-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.idle, 1, "sum"))), "idle")&target=alias(stacked(avg(groupByNode(scale(hosts.tst-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5), 1, "sum"))), "ec2 steal")&target=alias(stacked(avg(groupByNode(hosts.tst-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.wait, 1, "sum"))), "IO wait")&title=m1.medium(spot) tester efficiency 24hours


https://graphite.mozilla.org/render?from=-24hours&until=now&width=1800&height=900&target=alias(scale(sum(sum(groupByNode(exclude(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal)"), 1, "sum")),sum(groupByNode(scale(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5),1,"sum"))),0.01), "number of slaves")&target=alias(stacked(avg(groupByNode(exclude(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal|idle|wait)"), 1, "sum"))), "cpu busy")&target=alias(stacked(avg(groupByNode(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.idle, 1, "sum"))), "idle")&target=alias(stacked(avg(groupByNode(scale(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5), 1, "sum"))), "ec2 steal")&target=alias(stacked(avg(groupByNode(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.wait, 1, "sum"))), "IO wait")&title=m3.medium(ondemand) tester efficiency 24hours


# from 2months ago
https://graphite.mozilla.org/render?from=-60days&until=-59days&width=1800&height=900&target=alias(scale(sum(sum(groupByNode(exclude(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal)"), 1, "sum")),sum(groupByNode(scale(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5),1,"sum"))),0.01), "number of slaves")&target=alias(stacked(avg(groupByNode(exclude(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal|idle|wait)"), 1, "sum"))), "cpu busy")&target=alias(stacked(avg(groupByNode(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.idle, 1, "sum"))), "idle")&target=alias(stacked(avg(groupByNode(scale(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5), 1, "sum"))), "ec2 steal")&target=alias(stacked(avg(groupByNode(hosts.tst-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.wait, 1, "sum"))), "IO wait")&title=m1.medium tester efficiency 2months ago


#builds
# subtract steal/idle/wait to see how much resources we are using more or less productively
https://graphite.mozilla.org/render?from=-24hours&until=now&width=1800&height=900&target=alias(scale(sum(sum(groupByNode(exclude(hosts.try-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal)"), 1, "sum")),sum(groupByNode(scale(hosts.try-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5),1,"sum"))),0.01), "number of slaves")&target=alias(stacked(avg(groupByNode(exclude(hosts.try-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal|idle|wait)"), 1, "sum"))), "cpu busy")&target=alias(stacked(avg(groupByNode(hosts.try-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.idle, 1, "sum"))), "idle")&target=alias(stacked(avg(groupByNode(scale(hosts.try-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5), 1, "sum"))), "ec2 steal")&target=alias(stacked(avg(groupByNode(hosts.try-linux64-spot-0*_*_releng_*_mozilla_com.cpu.*.cpu.wait, 1, "sum"))), "IO wait")&title=m3.xlarge(spot) builder efficiency 24hours


https://graphite.mozilla.org/render?from=-24hours&until=now&width=1800&height=900&target=alias(scale(sum(sum(groupByNode(exclude(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal)"), 1, "sum")),sum(groupByNode(scale(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5),1,"sum"))),0.01), "number of slaves")&target=alias(stacked(avg(groupByNode(exclude(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal|idle|wait)"), 1, "sum"))), "cpu busy")&target=alias(stacked(avg(groupByNode(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.idle, 1, "sum"))), "idle")&target=alias(stacked(avg(groupByNode(scale(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5), 1, "sum"))), "ec2 steal")&target=alias(stacked(avg(groupByNode(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.wait, 1, "sum"))), "IO wait")&title=c3.xlarge(ondemand) builder efficiency 24hours


# from 2months ago
# WTF iowait AND idle is 2x overreported 2 months ago
https://graphite.mozilla.org/render?from=-60days&until=-59days&width=1800&height=900&target=alias(stacked(avg(groupByNode(exclude(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.*, "(steal|idle|wait)"), 1, "sum"))), "cpu busy")&target=alias(stacked(avg(groupByNode(scale(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.idle,0.5), 1, "sum"))), "idle")&target=alias(stacked(avg(groupByNode(scale(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.steal,0.5), 1, "sum"))), "ec2 steal")&target=alias(stacked(avg(groupByNode(scale(hosts.bld-linux64-ec2-0*_*_releng_*_mozilla_com.cpu.*.cpu.wait,0.5), 1, "sum"))), "IO wait")&title=m3.xlarge builder efficiency 2months ago(number of slaves broken due to doublecounting)



