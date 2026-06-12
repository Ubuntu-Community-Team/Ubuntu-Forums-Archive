---
title: "Ubuntu 20.04 static connection doesn't get search domain after boot."
date: 2021-01-24
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2021-01-24
Upgraded from 18.04 where everything worked just fine. After reboot, don't see local computers. Checked /etc/resolv.conf, there is no search domain. Checked Network Manager configuration, search domain is there. After a bit of tinkering, tried to restart systemd-resolved. Well, it fixed the problem, /etc/resolv.conf has a search domain. This problem is not happening on laptop with DHCP Wi-Fi connection.
So far I made a script which runs on cron every half an hour and restarts resolved if there is no search domain. Any better solution?

I should say I'm disappointed. With Ubuntu since 5.04, networking always worked perfectly, didn't have to do anything except setup.
Separate issue is netplan on servers, I don't have any nice words for this thing.

---

### Post by TheFu on 2021-01-24
Don't use systemd-resolved?
Or resolvconf
Or network-manager

The manually modified /etc/resolv.conf works perfectly, just like it has since the mid-1990s.  All the extra complexities aren't needed.

Count yourself lucky of you've not run into network issues with Ubuntu.  Since 12.04, I've been fighting with whatever new pushed thing Canonical decides was "best" for normal people to get a working solution.  Since I run a DNS server on my network, I don't need any local caching and certainly don't need/want mDNS or Avahi.

Netplan took about a year ago to work for my needs. I don't use IPv6 at all. It is disabled in the kernel for all my systems where I can do that. My router blocks all IPv6 traffic and Teredo tunneling attempts. I'm just not ready to deal with all the security aspects that IPv6 includes.

---

### Post by Alex_Filonov on 2021-07-25
Last update invalidated my fix. Don't know why, but restart of resolver doesn't work anymore. It doesn't put search line  in /etc/resolv.conf,. Yes, Network Manager still has domain search defined right.
I changed my cron script to add search line to resolv.conf if it's not there. Crude but effective.

---

### Post by Alex_Filonov on 2022-02-06
Well, another fix: put a line:
Domain=<Domain name>
in /etc/resolved.conf
Working so far.

---

### Post by TheFu on 2022-02-06
I'm a little surprised that changing/creating  /etc/resolved.conf has any impact at all.   
resolved.conf goes into /etc/systemd/ directory.

/etc/resolv.conf is the name of the real file that actually controls name resolution without any front-end. No need for network-manager, systemd-resolved, resolvconf or anything else.   

/etc/resolv.conf is where the network layer of every Unix-like OS looks. In fact, if resolv.conf has the 2 lines needed to make it work, that's all we need.

Details matter.

---

### Post by Alex_Filonov on 2022-11-26
Now fix on /etc/resolved.conf doesn't work. 
New fix:
in /etc/systemd/resolved.conf
Domains=<your domain>

Also works in 22.04

---

### Post by Alex_Filonov on 2023-06-11
Additional info, found out when installing 22.04 fresh. You just can't enter search domain for a static connection anymore. There is no field in settings. So, /etc/systemd/resolv.conf is the only place that works.

---

