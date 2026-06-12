---
title: "ATI SAPPHIRE RADEON HD4850 driver"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by marcgh on 2009-01-03
I was running Ubuntu on this machine and with this video card for the past week without any problem.

Today a friend visited me and messed everything up via the Terminal( I know I should be more selective in my friendship!)

I used Bootitng to delete all Ubuntu partitions - resized my XP partition and restored the MBR.

Install went flawless bu I can't get my video card running at 1440x900.
Whenever I install and restart the screen goes black and that is it. Only way out is to reboot Ubuntu in safe mode, restore Xorg(not sure about the name) and restart in this 1024 x 768 resolution.

This are the commands I used (as I did a week ago when all worked) :

sudo -s                  (i entered my password)
cd /usr/share/ati
sh ./fglrx-uninstall.sh  (to uninstall any previous ati drivers)
cd ~/Desktop             (that's where I put the driver file)
sh ./ati-driver-installer-8-10-x86.x86_64.run

After that install ATI runs and finish.
I have tried this now 3 times with as much reboots but to no avail.

What am I doing wrong this time?
Thanks i advance for your help.

---

