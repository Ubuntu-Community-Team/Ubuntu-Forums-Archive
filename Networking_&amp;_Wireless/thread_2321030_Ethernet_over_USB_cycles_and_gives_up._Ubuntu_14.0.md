---
title: "Ethernet over USB cycles and gives up. Ubuntu 14.04 LTS"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by edwin31 on 2016-04-19
Wired Ethernet over USB cycles and stops. Although wireless is working, wired ethernet is preferred. Fail to understand why it only works for a little time after reboot and gives up.

rebooting frequently to get the wired connection going. 

Created a new thread after a lot of search on forum turned up empty.  All steps from "Before posting in Networking & Wireless" completed and wireless-info.tar.gz attached along all eht0 lines from dmesg.

I'm fairly savvy and can investigate/debug - please point or help appreciated. thanks in advance

<code>
dmesg | grep eth0
[    1.691350] r8152 2-2:1.0 eth0: v1.08.1 (2015/07/28)
[    2.191689] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.739635] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   46.208109] r8152 2-2:1.0 eth0: Stop submitting intr, status -71
[   47.030635] r8152 2-2:1.0 eth0: v1.08.1 (2015/07/28)
[   47.113678] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.661245] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   65.965027] r8152 2-2:1.0 eth0: Stop submitting intr, status -71
[   66.592612] r8152 2-2:1.0 eth0: v1.08.1 (2015/07/28)
[   66.687689] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.210208] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   87.065707] r8152 2-2:1.0 eth0: Stop submitting intr, status -71
[   87.704322] r8152 2-2:1.0 eth0: v1.08.1 (2015/07/28)
[   87.787727] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   90.342876] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  122.522010] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:7c:03:d8:b9:fd:2e:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  164.813410] r8152 2-2:1.0 eth0: Stop submitting intr, status -71
[  165.446889] r8152 2-2:1.0 eth0: v1.08.1 (2015/07/28)
[  165.530912] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  168.058657] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  247.502224] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:7c:03:d8:b9:fd:2e:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  259.966542] r8152 2-2:1.0 eth0: Stop submitting intr, status -71
</code>

---

### Post by edwin31 on 2016-05-06
Solved:   Problem was with usb-2-ethernet adapter - Insignia USB 3.0-to-Gigabit Ethernet Adapter. Changed to j5 create - USB 3.0-to-Gigabit Ethernet Adapter and it works fine out of the box. Did not have to update any drivers or do anything.

---

