---
title: "Broadcom 4306"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by DevNull11 on 2006-10-25
I've tried to install my broadcom 4306 wireless card on my compaq laptop using this guide [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) . 
I got to the part where I would go to the  System -> Administration -> Networking to disable eht0 and enable wlan0 however wlan0 is not there :( . 

If I run: 
ndiswrapper -l 
I get: 
> Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl5.sys      invalid driver!

I tryed it with and without bcmwl5.sys

Here is iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



---

### Post by DevNull11 on 2006-10-26
bump

---

### Post by cvmostert on 2006-10-27
did you remove the bcmwl5.sys and try 
sudo modprobe ndiswrapper ?

my problem is ndiswrapper does not want to load as module...

---

### Post by DevNull11 on 2006-10-27
Yes, I even try other device drivers, is there a way to extract a .exe file so that I can try the drivers that came with my laptop.

---

### Post by worldgnat on 2007-01-28
There is in fact a way to extract data from an exe file. install something called cab-extract (I don't know if it's in the ubuntu repository). It should get you what you need from the exe. However, there's a tgz file somewhere on the net that has drivers bcm43xx on windows that work perfectly well with ndiswrapper. I don't remember where it is, but try doing some more googling.

-Peter

---

