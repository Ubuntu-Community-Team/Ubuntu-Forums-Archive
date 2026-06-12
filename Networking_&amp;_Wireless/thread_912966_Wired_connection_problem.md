---
title: "Wired connection problem"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by atlas2003 on 2008-09-07
Hello everybody!
A friend of mine, give me his laptop in order to install Ubuntu (8.04.1) on it. As if just want to test it, I've installed it under windows.

The install work well (just have to add acpi=off in the menu.lst).
The first boot was ok: all worked perfectly (the wired network too). I have installed all the update, and reboot the computer.
Since: The wired networking don't work anymore.

I have try a lot of thing, but wihthout good result.

BUT, when i start Ubuntu in "recovery mode", the wired network work very well.. I don't understant why? And when I reboot in "normal mode", it's stop working...

The laptop is pluged on my router. In fact I have 2 computers connected on it. The first one work very well. So i have switch the rj45 between computer but it's same result: the laptop didn't work.

I have checked this on the two computer:
sudo route -n
The result is the same on the 2 computers

resolv.conf is also the same on the 2 computers

sudo dhclient eth0 is working on my computer
But on the laptop, it don't work. I have:
no dhcp offers received

I don't know what to try now :(

---

### Post by atlas2003 on 2008-09-07
up? :(

---

### Post by tbehrens on 2008-09-09
> If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers. It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one. In the meantime, config linux not to use it by:

1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/blacklist
3. In the gedit window at the end of the file, type: blacklist ipv6
4. Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

I had all kinds of problems IPV6 screwing things up.  It is the first thing I would try.  GL

---

