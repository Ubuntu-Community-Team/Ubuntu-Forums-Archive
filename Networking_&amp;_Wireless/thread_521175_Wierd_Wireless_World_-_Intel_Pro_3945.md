---
title: "Wierd Wireless World - Intel Pro 3945"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by BC7333 on 2007-08-09
Background: [http://ubuntuforums.org/showthread.php?t=514792](http://ubuntuforums.org/showthread.php?t=514792)

Still have some problems connecting.  Can boot, turn on wireless using Fn-F8 but need to be exactly 20 feet, line of sight from router to connect.  Not closer, not farther.  Also when wireless attempting to connect I get KrazyKursor syndrome.. when moving mouse around it hops here and there and is quite uncontrollable.

Attached is a kernel log.  Strange things I found:


> Aug  9 09:28:12 brian-flybook avahi-daemon[4894]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.118.
Aug  9 09:28:12 brian-flybook avahi-daemon[4894]: New relevant interface wlan0.IPv4 for mDNS.
Aug  9 09:28:12 brian-flybook avahi-daemon[4894]: Registering new address record for 192.168.1.118 on wlan0.IPv4.
Aug  9 09:28:13 brian-flybook avahi-daemon[4894]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug  9 09:28:13 brian-flybook avahi-daemon[4894]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.118.
Aug  9 09:28:13 brian-flybook avahi-daemon[4894]: Withdrawing address record for 192.168.1.118 on wlan0.
[B]
REPEATS SEVERAL TIMES, THINK BEFORE WIRELESS TURNED ON[/B]



> Aug  9 09:28:47 brian-flybook kernel: [  153.848000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  9 09:28:47 brian-flybook avahi-daemon[4894]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.118.
Aug  9 09:28:47 brian-flybook avahi-daemon[4894]: New relevant interface wlan0.IPv4 for mDNS.
Aug  9 09:28:47 brian-flybook avahi-daemon[4894]: Registering new address record for 192.168.1.118 on wlan0.IPv4.
Aug  9 09:28:50 brian-flybook kernel: [  156.684000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Aug  9 09:28:58 brian-flybook kernel: [  164.280000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Aug  9 09:29:03 brian-flybook ntpdate[6198]: can't find host ntp.ubuntu.com 
Aug  9 09:29:03 brian-flybook ntpdate[6198]: no servers can be used, exiting

**THINK THIS WITH WIRELESS TURNED ON USING Fn F8**

Wireless light blinking crazy.. Mouse going Krazy, trying to connect, move laptop away 20 feet from router and it connects.

> Aug  9 09:30:37 brian-flybook kernel: [  263.092000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Aug  9 09:30:38 brian-flybook kernel: [  264.208000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Aug  9 09:30:38 brian-flybook kernel: [  264.412000] psmouse.c: resync failed, issuing reconnect request
Aug  9 09:30:44 brian-flybook kernel: [  270.696000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Aug  9 09:30:45 brian-flybook kernel: [  271.796000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Aug  9 09:30:45 brian-flybook kernel: [  271.996000] psmouse.c: resync failed, issuing reconnect request
Aug  9 09:30:52 brian-flybook kernel: [  278.304000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Aug  9 09:30:59 brian-flybook kernel: [  285.924000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Aug  9 09:31:04 brian-flybook kernel: [  290.860000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  9 09:31:06 brian-flybook avahi-daemon[4894]: Registering new address record for fe80::219:d2ff:febb:5059 on wlan0.*.
Aug  9 09:31:14 brian-flybook anacron[7002]: Anacron 2.3 started on 2007-08-09
Aug  9 09:31:14 brian-flybook anacron[7002]: Will run job `cron.daily' in 5 min.
Aug  9 09:31:14 brian-flybook anacron[7002]: Jobs will be executed sequentially
Aug  9 09:31:15 brian-flybook kernel: [  301.104000] wlan0: no IPv6 routers present
Aug  9 09:36:14 brian-flybook anacron[7002]: Job `cron.daily' started
Aug  9 09:36:15 brian-flybook anacron[7140]: Updated timestamp for job `cron.daily' to 2007-08-09



Now wireless stable, can move around house and garden without problems and navigate..

Any suggestions what might really be happening here?  Is the network card when searching for the router somehow taking up memory space that the mouse is using, forcing it 'out of sync'?

Once connected, mouse problem disappears.

Attached full log.

Many thanks from this newbie!

---

### Post by walkerk on 2007-08-09
Thanks buddy. We are very excited new parents :).

I just looked over your network log and I'm not sure whats going on. Hopefully one of these guys with an ip3945 card have a clue. I'll give the net a look to see if I can find anything..

---

