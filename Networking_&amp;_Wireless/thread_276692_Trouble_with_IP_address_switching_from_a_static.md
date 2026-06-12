---
title: "Trouble with IP address switching from a static"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by closer9 on 2006-10-13
Hello all... im having issues with my network IP being switched from static to DHCP very randomly.

I have my /etc/network/interfaces file setup as the following:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 216.176.xxx.xx
        netmask 255.255.255.248
        gateway 216.176.xxx.xx
```

Of course I hide the address above, but anyways... So when i start up my network (either manually or by boot-up) I do get my static IP just fine. But hours later (20/24) The IP changes from the static to a DHCP IP (DHCP is provided on that connection also). This is a brand new dapper server install, its done this 2 of 2 days :-P

When I run "sudo ifdown eth0" while it has this DHCP IP i get "SIOCDELRT: No such process". Then i "sudo ifup eth0" and everything is fine again, static IP and all.

Here are some stats. If you need my whole dmesg I can post that too.
```
Linux version 2.6.15-23-server (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Tue May 23 15:10:35 UTC 2006
CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
eth0: RealTek RTL8139 at 0xf88ac000, 00:0f:ea:3e:f7:b8, IRQ 209
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present
```

Something weird I noticed was when I checked my IP with "netstat -ie"... the inet6 address was the same for both IPs but everything else was different (IP, broadcast, netmask). weird.

---

### Post by closer9 on 2006-10-13
Looking through my syslog I notice a few things that are weird. dhclient seems to be requesting an IP quite often.

Here is an example:
```
Oct 13 08:43:23 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:43:38 neg9 proftpd[27194]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session opened.
Oct 13 08:43:42 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:44:20 neg9 last message repeated 4 times
Oct 13 08:44:56 neg9 last message repeated 3 times
Oct 13 08:45:01 neg9 proftpd[27213]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session opened.
Oct 13 08:45:01 neg9 proftpd[27213]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - no such user 'anonymous'
Oct 13 08:45:01 neg9 proftpd[27213]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session closed.
Oct 13 08:45:01 neg9 proftpd[27214]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session opened.
Oct 13 08:45:01 neg9 proftpd[27214]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - no such user 'anonymous'
Oct 13 08:45:01 neg9 proftpd[27214]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session closed.
Oct 13 08:45:14 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:45:53 neg9 last message repeated 3 times
Oct 13 08:46:58 neg9 last message repeated 6 times
Oct 13 08:47:16 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:47:19 neg9 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 13 08:47:19 neg9 dhclient: DHCPOFFER from 216.176.xxx.81
Oct 13 08:47:19 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:47:19 neg9 dhclient: DHCPACK from 216.176.xxx.81
Oct 13 08:47:19 neg9 dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Oct 13 08:47:19 neg9 dhclient: bound to 216.176.xxx.152 -- renewal in 35597 seconds.
Oct 13 08:55:02 neg9 proftpd[27122]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP no transfer timeout, $
Oct 13 08:55:02 neg9 proftpd[27122]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session closed.
Oct 13 08:55:06 neg9 proftpd[27121]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP no transfer timeout, $
Oct 13 08:55:06 neg9 proftpd[27121]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session closed.
Oct 13 08:55:15 neg9 proftpd[27194]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP no transfer timeout, $
Oct 13 08:55:15 neg9 proftpd[27194]: neg9.com.com (wirefall.netnitco.net[216.176.xxx.xxx]) - FTP session closed.
Oct 13 08:57:38 neg9 ntpdate[27259]: step time server 82.211.81.145 offset -0.647044 sec
Oct 13 09:17:01 neg9 /USR/SBIN/CRON[27373]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct 13 09:45:34 neg9 -- MARK --
```

Now at 8:47 is when I noticed it did it again, so it seems it is trying to renew a lease for some reason. It seems to try every minute or so.

Here is another example from that same hour:
```
Oct 13 08:17:01 neg9 /USR/SBIN/CRON[27018]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct 13 08:17:08 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:17:49 neg9 last message repeated 2 times
Oct 13 08:18:54 neg9 last message repeated 5 times
Oct 13 08:19:47 neg9 last message repeated 4 times
Oct 13 08:20:59 neg9 last message repeated 5 times
Oct 13 08:21:46 neg9 last message repeated 4 times
Oct 13 08:23:02 neg9 last message repeated 5 times
Oct 13 08:23:58 neg9 last message repeated 3 times
Oct 13 08:24:55 neg9 last message repeated 5 times
Oct 13 08:26:01 neg9 last message repeated 6 times
Oct 13 08:26:56 neg9 last message repeated 4 times
Oct 13 08:27:55 neg9 last message repeated 5 times
Oct 13 08:28:45 neg9 last message repeated 3 times
Oct 13 08:29:56 neg9 last message repeated 4 times
Oct 13 08:30:59 neg9 last message repeated 5 times
Oct 13 08:31:58 neg9 last message repeated 5 times
Oct 13 08:32:58 neg9 last message repeated 6 times
Oct 13 08:33:53 neg9 last message repeated 4 times
Oct 13 08:34:47 neg9 last message repeated 4 times
Oct 13 08:36:02 neg9 last message repeated 5 times
Oct 13 08:36:58 neg9 last message repeated 4 times
Oct 13 08:37:44 neg9 last message repeated 3 times
Oct 13 08:38:45 neg9 last message repeated 3 times
```

What im wondering is why its even trying to request a new lease? Am I forgetting to configure my static somewhere? I thought that /etc/network/interfaces was where you specify a static, but not im not so sure.

```
This part seems to be where it is having trouble:
Oct 13 08:47:19 neg9 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 13 08:47:19 neg9 dhclient: DHCPACK from 216.176.xxx.81
Oct 13 08:47:19 neg9 dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Oct 13 08:47:19 neg9 dhclient: bound to 216.176.xxx.152 -- renewal in 35597 seconds.
```

My Static is suposed to be 81... but grabs a DHCP address of 152. Thanks for any help you guys can provide.

-Scott

---

### Post by dannyboy79 on 2006-10-13
well, i am pretty sure that's the file that gets updated with the static ip but why don't you for the heck of it, go to system, admin, networking, then for the interface you want, hit properties, and enter all your info for the static ip. that's the way i set up mine for sure and it doesn't change like yours does. give that a shot and let me know. good lcuk

---

### Post by Iowan on 2006-10-13
Check (in a terminal)```
ps ax
```
see if dhclient is (still) running.  Dunno if something in **sessions** might be (re)starting it cuz it did once.

---

### Post by closer9 on 2006-10-13
> **dannyboy79 said:**
> well, i am pretty sure that's the file that gets updated with the static ip but why don't you for the heck of it, go to system, admin, networking, then for the interface you want, hit properties, and enter all your info for the static ip. that's the way i set up mine for sure and it doesn't change like yours does. give that a shot and let me know. good lcuk
I'd love to do that but I set this up as a headless system. :(

> **Iowan said:**
> Check (in a terminal)```
ps ax
```
see if dhclient is (still) running.  Dunno if something in **sessions** might be (re)starting it cuz it did once.
Cool... yeah dhclient is running:

dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

Ill go ahead and kill it and see if it does this again. Probably left over from the install for some reason. Thanks alot!

---

### Post by dannyboy79 on 2006-10-13
> **closer9 said:**
> I'd love to do that but I set this up as a headless system. :(
That shouldn't stp you from going thru the gui! If I had a hedless system I would still want some sort of a gui and remote desktop with ubuntu is fairly easy to setup since I believe it's already got a form of remote desktop installed by default.

---

