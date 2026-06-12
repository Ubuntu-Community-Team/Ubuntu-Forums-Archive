---
title: "Wireless card can see network but doesn't always connect"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by limitedmage on 2008-08-26
Hi,

I have an Intel 3945 wireless card on my Dell Inspiron 1420 laptop. I can use it perfectly under Windows and can connect to any network without a problem.

Under Linux, I've had a few problems connecting to wireless networks. My home network, which is unsecure (I know, it's not a good idea), won't connect at all. The network on my college campus connects -- sometimes.

I have no problem scanning networks, only connecting.

I have removed Network Manager and installed Wicd. Things have improved a little, but my home network still won't connect.

Other wireless devices, including my computer with Windows booted, my Nintendo DS and my neighbor's iPhone, have no problem connecting.

Does anybody have any ideas what I can do to improve this?

Thanks in advance.

---

### Post by Sam Lars on 2008-08-26
Could you post
```
lspci | grep Network
```

Have you done anything to get the card working, or did it work out of the box?

---

### Post by limitedmage on 2008-08-26
Here you go:
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

The card has worked out of the box. The only thing I've modified is that I removed Network Manager and installed Wicd.

---

### Post by Sam Lars on 2008-08-26
I would suggest at least trying Ndiswrapper
```
sudo apt-get install ndisgtk
```

---

### Post by limitedmage on 2008-08-26
Ok, I tried ndiswrapper, downloaded Windows XP drivers from Intel's website, loaded them into ndiswrapper and restarted my machined. No network detected AT ALL now.

So I disabled ndiswrapper and just switched back to the Linux driver, iwl3945

Any other ideas?

---

### Post by Sam Lars on 2008-08-26
I guess you could try running
```
tail -f /var/log/syslog
```
and then trying to connect at home and then at school.  There should be some hints in syslog as to what is going wrong at home or right at school.

---

### Post by limitedmage on 2008-08-27
At school, the output of the command is
```

Aug 27 07:41:39 julip-laptop avahi-daemon[5394]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.48.53.127.
Aug 27 07:41:39 julip-laptop avahi-daemon[5394]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 07:41:39 julip-laptop avahi-daemon[5394]: Registering new address record for 10.48.53.127 on wlan0.IPv4.
Aug 27 07:41:39 julip-laptop dhclient: bound to 10.48.53.127 -- renewal in 2328 seconds.
Aug 27 07:41:47 julip-laptop kernel: [   96.605088] wlan0: no IPv6 routers present
Aug 27 07:43:17 julip-laptop avahi-daemon[5394]: Withdrawing address record for 10.48.53.127 on wlan0.
Aug 27 07:43:17 julip-laptop avahi-daemon[5394]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.48.53.127.
Aug 27 07:43:17 julip-laptop avahi-daemon[5394]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 07:43:17 julip-laptop dhclient: receive_packet failed on wlan0: Network is down
Aug 27 07:43:17 julip-laptop avahi-daemon[5394]: Withdrawing address record for fe80::21f:3cff:fe4f:52a9 on wlan0.
Aug 27 07:43:26 julip-laptop kernel: [  166.785526] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 27 07:43:26 julip-laptop kernel: [  166.797801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 27 07:43:26 julip-laptop kernel: [  166.901969] wlan0: Initial auth_alg=0
Aug 27 07:43:26 julip-laptop kernel: [  166.901975] wlan0: authenticate with AP 00:1e:7a:a7:e2:80
Aug 27 07:43:26 julip-laptop kernel: [  166.903177] wlan0: RX authentication from 00:1e:7a:a7:e2:80 (alg=0 transaction=2 status=0)
Aug 27 07:43:26 julip-laptop kernel: [  166.903182] wlan0: authenticated
Aug 27 07:43:26 julip-laptop kernel: [  166.903185] wlan0: associate with AP 00:1e:7a:a7:e2:80
Aug 27 07:43:26 julip-laptop kernel: [  166.905538] wlan0: RX ReassocResp from 00:1e:7a:a7:e2:80 (capab=0x421 status=0 aid=5)
Aug 27 07:43:26 julip-laptop kernel: [  166.905543] wlan0: associated
Aug 27 07:43:26 julip-laptop kernel: [  166.907994] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 27 07:43:26 julip-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 6580
Aug 27 07:43:26 julip-laptop dhclient: removed stale PID file
Aug 27 07:43:26 julip-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 27 07:43:26 julip-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 27 07:43:26 julip-laptop dhclient: All rights reserved.
Aug 27 07:43:26 julip-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 27 07:43:26 julip-laptop dhclient: 
Aug 27 07:43:26 julip-laptop dhclient: wmaster0: unknown hardware address type 801
Aug 27 07:43:27 julip-laptop dhclient: wmaster0: unknown hardware address type 801
Aug 27 07:43:27 julip-laptop dhclient: Listening on LPF/wlan0/00:1f:3c:4f:52:a9
Aug 27 07:43:27 julip-laptop dhclient: Sending on   LPF/wlan0/00:1f:3c:4f:52:a9
Aug 27 07:43:27 julip-laptop dhclient: Sending on   Socket/fallback
Aug 27 07:43:27 julip-laptop dhclient: DHCPREQUEST of 10.48.53.127 on wlan0 to 255.255.255.255 port 67
Aug 27 07:43:27 julip-laptop dhclient: DHCPACK of 10.48.53.127 from 1.1.1.1
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Registering new address record for fe80::21f:3cff:fe4f:52a9 on wlan0.*.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.48.53.127.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Registering new address record for 10.48.53.127 on wlan0.IPv4.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Withdrawing address record for 10.48.53.127 on wlan0.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.48.53.127.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.48.53.127.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 07:43:28 julip-laptop avahi-daemon[5394]: Registering new address record for 10.48.53.127 on wlan0.IPv4.
Aug 27 07:43:28 julip-laptop dhclient: bound to 10.48.53.127 -- renewal in 2488 seconds.
Aug 27 07:43:37 julip-laptop kernel: [  173.823367] wlan0: no IPv6 routers present

```

I'll post the output at home this afternoon.

---

### Post by limitedmage on 2008-08-27
Here is the output at home:
```

Aug 27 21:24:24 julip-laptop kernel: [  740.841069] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 27 21:24:24 julip-laptop kernel: [  740.855217] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 27 21:24:24 julip-laptop kernel: [  740.890567] wlan0: Initial auth_alg=0
Aug 27 21:24:24 julip-laptop kernel: [  740.890573] wlan0: authenticate with AP 00:0d:72:8a:c7:91
Aug 27 21:24:24 julip-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 6969
Aug 27 21:24:24 julip-laptop dhclient: removed stale PID file
Aug 27 21:24:24 julip-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 27 21:24:24 julip-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 27 21:24:24 julip-laptop dhclient: All rights reserved.
Aug 27 21:24:24 julip-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 27 21:24:24 julip-laptop dhclient: 
Aug 27 21:24:24 julip-laptop dhclient: wmaster0: unknown hardware address type 801
Aug 27 21:24:24 julip-laptop kernel: [  740.892548] wlan0: RX authentication from 00:0d:72:8a:c7:91 (alg=0 transaction=2 status=0)
Aug 27 21:24:24 julip-laptop kernel: [  740.892553] wlan0: authenticated
Aug 27 21:24:24 julip-laptop kernel: [  740.892555] wlan0: associate with AP 00:0d:72:8a:c7:91
Aug 27 21:24:25 julip-laptop kernel: [  741.048676] wlan0: associate with AP 00:0d:72:8a:c7:91
Aug 27 21:24:25 julip-laptop kernel: [  741.196838] wlan0: associate with AP 00:0d:72:8a:c7:91
Aug 27 21:24:25 julip-laptop kernel: [  741.346839] wlan0: association with AP 00:0d:72:8a:c7:91 timed out
Aug 27 21:24:25 julip-laptop dhclient: wmaster0: unknown hardware address type 801
Aug 27 21:24:25 julip-laptop dhclient: Listening on LPF/wlan0/00:1f:3c:4f:52:a9
Aug 27 21:24:25 julip-laptop dhclient: Sending on   LPF/wlan0/00:1f:3c:4f:52:a9
Aug 27 21:24:25 julip-laptop dhclient: Sending on   Socket/fallback
Aug 27 21:24:28 julip-laptop dhclient: DHCPREQUEST of 10.48.46.15 on wlan0 to 255.255.255.255 port 67
Aug 27 21:24:37 julip-laptop last message repeated 2 times
Aug 27 21:24:51 julip-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 27 21:24:58 julip-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Aug 27 21:25:13 julip-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Aug 27 21:25:22 julip-laptop dhclient: No DHCPOFFERS received.
Aug 27 21:25:22 julip-laptop dhclient: Trying recorded lease 10.48.46.15
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.48.46.15.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Registering new address record for 10.48.46.15 on wlan0.IPv4.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Withdrawing address record for 10.48.46.15 on wlan0.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.48.46.15.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.48.46.15.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 21:25:22 julip-laptop avahi-daemon[5378]: Registering new address record for 10.48.46.15 on wlan0.IPv4.
Aug 27 21:25:25 julip-laptop avahi-daemon[5378]: Withdrawing address record for 10.48.46.15 on wlan0.
Aug 27 21:25:25 julip-laptop avahi-daemon[5378]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.48.46.15.
Aug 27 21:25:25 julip-laptop avahi-daemon[5378]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 21:25:25 julip-laptop avahi-autoipd(wlan0)[13753]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 27 21:25:25 julip-laptop avahi-autoipd(wlan0)[13753]: Successfully called chroot().
Aug 27 21:25:25 julip-laptop avahi-autoipd(wlan0)[13753]: Successfully dropped root privileges.
Aug 27 21:25:25 julip-laptop avahi-autoipd(wlan0)[13753]: Starting with address 169.254.6.26
Aug 27 21:25:30 julip-laptop avahi-autoipd(wlan0)[13753]: Callout BIND, address 169.254.6.26 on interface wlan0
Aug 27 21:25:30 julip-laptop avahi-daemon[5378]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.26.
Aug 27 21:25:30 julip-laptop avahi-daemon[5378]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 21:25:30 julip-laptop avahi-daemon[5378]: Registering new address record for 169.254.6.26 on wlan0.IPv4.
Aug 27 21:25:34 julip-laptop avahi-autoipd(wlan0)[13753]: Successfully claimed IP address 169.254.6.26
Aug 27 21:25:34 julip-laptop dhclient: No working leases in persistent database - sleeping.

```

So, basically, my router and my computer can't decide on DHCP, I guess.

Unfortunately, my router is not a standard one. My ISP, TelMex, provides it with the plan and I share it with other people in my building, so I can't modify anything. :(

Is there any way I can fix the problem on my side, without touching the router?

---

