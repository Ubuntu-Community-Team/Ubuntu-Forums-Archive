---
title: "System chaning ip by it self..??!?!?"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by mrazster on 2006-08-05
Lo fellas....got my self a wierd problem with my networking.

I'm running Dapper 6.06 Xubuntu with 2.6.17 686 kernel.

1. Now my first problem is..almost everytime I restar/reboot the system I get no ip and my network settings and my NIC is deactivated in *Menu/System/Networking*. And sometimes it says  activated but I still can't connect to internet. So I have to deactivate it and then activate it again and it's all fine.

2. When I get it all up and running and using my comp as usual.. surfing,listening to webbradio e.t.c...suddenly it changes my ip number with no reason at all. It changes betwen two numbers, one ending with 169 and the other ending 170....and it keeps changing back and forward between thoose 2. And every time it changes my gaim, radio streams and DC e.t.c gets borked. This ip changing occurs between every 20min to 4h.

Everything is set up with a computer running as router with "smooth wall" installed and a switch for extending numer of ports.Network is configuerd with DHCP.
The other computers connected in the network is running winXP and don't have thoose problems at all.

I have tried to disable and remove all settings and the reeanble it again. I have also tried to "save session" when rebooting but still the same problem.

I have no clue even where to start....help is much appreciated..!!!!!

---

### Post by mrazster on 2006-08-06
Got both of my problems sorted with help from [THIS](http://www.ubuntuforums.org/showthread.php?p=1346944#post1346944) thread, and the post made by *Mark Ferguson*

This is what I did:

> **Mark Ferguson said:**
> I think I have found a solution to this problem, well it's fixed things for me.

I have posted a full explanation of how I found the fix on the launchpad site. [https://launchpad.net/distros/ubuntu/+bug/50099](https://launchpad.net/distros/ubuntu/+bug/50099)

Here is the cut down version.

I found a problem in the /etc/udev/rules.d/85-ifupdown.rules file.

FIX to /etc/udev/rules.d/85-ifupdown.rules: Remove unnecessary "--" from ifup and ifdown cmds.
 /***********************************************************************/
 SUBSYSTEM!="net", GOTO="net_end"
# Bring devices up and down only if they're marked auto.
 # Use start-stop-daemon so we don't wait on dhcp
 ACTION=="add", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup --allow auto $env{INTERFACE}"
 ACTION=="remove", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown --allow auto $env{INTERFACE}"
LABEL="net_end"
 /*********************************************************************/

---

