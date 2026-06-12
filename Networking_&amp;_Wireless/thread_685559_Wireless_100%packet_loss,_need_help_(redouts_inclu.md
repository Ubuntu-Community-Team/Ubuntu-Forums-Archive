---
title: "Wireless 100%packet loss, need help (redouts included)"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by wahr on 2008-02-02
From my configuration and readouts, i'm very confused, and clueless as to how to fix this.

I have an IP address and established connection to my router, which uses a passive permit mac address list rather than encryption to prevent intrusion.

```
plasmacutter@Ryo-ohki:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:f2:4d:37:c0
Sending on   LPF/ath0/00:17:f2:4d:37:c0
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPOFFER from 192.168.2.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.3 -- renewal in 13230437 seconds.

```

The problem is pinging produces 100% packet loss.
I made 2 ping attempts, one for my router and one to google.com  (in case the router doesnt respond for security purposes)

```
plasmacutter@Ryo-ohki:~$ ping -c 4 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.4 icmp_seq=1 Destination Host Unreachable
From 192.168.2.4 icmp_seq=2 Destination Host Unreachable
From 192.168.2.4 icmp_seq=3 Destination Host Unreachable
From 192.168.2.4 icmp_seq=4 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3009ms
, pipe 3
plasmacutter@Ryo-ohki:~$ ping -c 4 www.google.com
ping: unknown host www.google.com                        
```

Just in case ping doesn't try to resolve DNS, I used wget on google as well, and received unknown host errors.
```
plasmacutter@Ryo-ohki:~$ wget www.google.com
--10:48:32--  http://www.google.com/
           => `index.html'
Resolving www.google.com... failed: Name or service not known.

```

Is this something I can fix, or a fundamental driver issue?:confused:
What command do I use to completely restart the network daemon (I read somewhere this problem may be due to an error in the network stack, and would like to reset it)

---

### Post by wahr on 2008-02-02
bumping for any advice?

---

### Post by Guilden_NL on 2008-02-03
Same problem here, same wireless in an Acer.  I ran Ubuntu on this laptop for 9 months with no problems.  Then my son wanted to try SUSE so I loaded it and it hosed the Grub and loads of Ubuntu things as well.  Had to reinstall Ubuntu seven times in the past week. Every single time I have had to use a different way to get the NDISwrapper to load and work.  I've now banned SUSE from our home, it's 1000% more evil than anything from Microsoft.

I am pretty upset with the Ubuntu distro as well, there doesn't seem to be a good way to fix it short of reformatting the partition where it resides.  I am going to do this in the second half of the Super Bowl.  Will monitor this thread to see if anyone has any ideas.  My son's laptop worked just fine (no wifi0) last night.  When he fired it up this morning, now there is a wifi0 even though I can't find any mention of it in the normal config files. ](*,)

---

