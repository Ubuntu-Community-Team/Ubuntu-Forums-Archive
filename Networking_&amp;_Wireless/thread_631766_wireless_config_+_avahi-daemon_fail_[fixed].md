---
title: "wireless config + avahi-daemon fail [fixed]"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Thiago Cesar Vieira on 2007-12-04
Hi friends!

It's my first post here. After using Slack and Gentoo, Ubuntu is my default SO now. I hope to help many friends here, who could have the same problems that I!!

Well, yesterday a had a problem after starting my **wireless network**. After searching the solution in forums/blogs and others, I'd like to show you how I solved this problem.

The description of a friend problem is similar to mine:
"Any network access freezes the console or desktop that attempts it. I have a boot failure with Avahi DNS daemon."
[http://ubuntuforums.org/showthread.php?t=416520&highlight=avahi-daemon+fail](http://ubuntuforums.org/showthread.php?t=416520&highlight=avahi-daemon+fail)

Description: I attempted to get up my new wireless network adapter (D-Link AirPlus G+ DWL-G520+), I saw a list of networks, click on mine, selected **WAP password** type and, when I finished configuration and clicked to up this one, the problems started. The **window had frozen**, I couldn't open any window (neither console). I had to restart manualy.

After that, in **reboot**, I had this message:
[I]Starting avahi mDNS/DNS-SD Daemon avahi-daemon
Timeout reached wating for return value
Could not receive return value from daemon process[/I]

After login window, **Gnome doesn't start**.

I could open virtual terminals, but when I run **ifconfig**, crash again...

When I **shutdown/restart** my machine::
*Stoping avahi-daemon fail*
Skip this, but not here:
*Stopping wpa-supplicant interfaces*

I tried to start in **recovery mode**, but has the same problem.


After searching a lot, I found a reference that tell to comment lines with configuration of wlan in file */etc/network/intefaces*. It worked for me, because I could open my Gnome normaly, but still without wireless.
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287)

After that I tried to reconfigure my adapter changing wireless security: **WEP key (ascii)** worked fine!! But I only noted this when I rebooted.
So, unfortunately, WAP security mode crashed my SO! It's not safe...
After I week I [saw]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") a list of wireless supported cards, that has a message for my adapter with alert "*Does not work with WPA.*"


Other helpful references:
[http://ubuntuforums.org/showthread.php?t=388891](http://ubuntuforums.org/showthread.php?t=388891) - tels what avahi does.
[http://ubuntuforums.org/showthread.php?t=485053](http://ubuntuforums.org/showthread.php?t=485053) - same problem: problem in avahi after configure WiFi

I went to **D-Link** homepage to find a driver to my adapter, but only Windows drivers are available.
[http://www.dlink.com/products/?pid=12](http://www.dlink.com/products/?pid=12)



Thanks a lot making Ubuntu better.

---

### Post by csat on 2007-12-04
> **Thiago Cesar Vieira said:**
> Hi friends!

Well, yesterday a had a problem after starting my **wireless network**. After searching the solution in forums/blogs and others, I'd like to show you how I solved this problem.



Have you considered place it to "Tutorials & Tips" provided that you've already solved your problem?

---

### Post by Thiago Cesar Vieira on 2007-12-04
Hello carioca!
Don't you think that it's much simple to put it in a HOW-TO? And, also, my text is disorderly, and my English is worst!

Bye!

---

### Post by asbesto on 2008-01-03
> **csat said:**
> Have you considered place it to "Tutorials & Tips" provided that you've already solved your problem?

ehm, no, because he haven't solved anything. His hack is a workaround, not a solution, because WPA is still not working :(

---

