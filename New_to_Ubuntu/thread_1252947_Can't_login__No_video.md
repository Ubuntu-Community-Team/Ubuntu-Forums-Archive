---
title: "Can't login / No video"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by marcgh on 2009-08-29
Hi,
Sice some time I am using 8.04 and was verypleased with it.
Few days ago my old harddisk died (probably from old age)
Installed a new HDD, dual boot XP / Ubuntu 9.04

I was very happy that my video card ATI Radeon 4850 recognised my 2 monitors and I was able to set for each of the the correct resolution.

This morning I installed a simple game and got a very low framerate - no problem I was thinking - install EnvyNG.

Followed the instructions, downloaded the recommended stuf, restarted and suddenly I was in hell!

On both screens I can see the Ubuntu load indicator then the main screen goes black (no signal) and the 2nd screen has a very distorted picture. 
NO login possible.
Reset button is the only way out.

Any help would be highly appreciated.
Marc

---

### Post by marcgh on 2009-08-29
Well, finally got back to login - did so many 'things' that I can't tell how.

But still many problems:

1. Simple games are running at very low frame rate
2. Trying GLXGEARS is giving error messages and n running gears.

any help?
Thanks

---

### Post by halitech on 2009-08-29
Have you checked System - Admin - Hardware drivers to see if there is anything there?

If not, try the ATI drivers
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

---

### Post by NoaHall on 2009-08-29
ATI drivers are poorly supported due to ati hating Open source. I think you will have to remove the drivers and reinstall them.

sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

---

### Post by marcgh on 2009-08-30
Hi everyone,

Just to tell you that my problems with the ATI RADEON as solved.
I followed this instructions: 

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

