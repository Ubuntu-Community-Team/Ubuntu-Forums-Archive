---
title: "Help needed with rt73 device"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by 99Elite on 2007-10-29
I have tried to install a driver for a Edimax 7318Ug usb wireless card. It  uses Ralink rt73 firmware and its device id is 148f:2573 (checked with Device manager in XP). So I used instructions in this topic and source code referred in the topic to install the driver :
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

I recently installed Linux Mint Cassandra and am somewhat of a noob with unix.

Only had a few problems with the install, /etc/modprobe.config didn't exist and I had to use nano of gedit to change the blacklist, but didn't experience other problems. 

The alias didn't work out but I worked around that.

My problem with the driver is it cannot connect to my router and the OS thinks the device is a wired connection. Autorun indicated the driver was invalid..

I've included the content of dmegs, ifconfig and iwconfig if that helps. 

Any ideas what can be done?

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):

[http://www.len.ro/work/tools/old-new-i8000-2]("http://www.len.ro/work/tools/old-new-i8000-2")

---

### Post by wieman01 on 2008-01-18
You could try my own Ralink tutorial... See signature. Please post either here or over there if you need support.

---

