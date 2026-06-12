---
title: "installation problem toshiba satellite L300d"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by jamesvar_70 on 2009-01-20
hi,
i tried to install ubuntu 8.04 64 bit on a toshiba satellite L300d , amd turion x2, 64 bit, 3 gb, 160 gb 5400 rpm, sata hard disk, while trying to install/using the live session option it gives error message as udevd-event (1494) run_program: /sbin/modprobe abnormalexit Busybox v1.1.3...and i am nto able to install it

plz help
thanks in advance
james

---

### Post by aheckler on 2009-01-20
I have seen a lot of these BusyBox errors popping up lately. While I'm not aware of the solution, you might try searching the forums, someone may have figured it out by now.

---

### Post by jamesvar_70 on 2009-01-23
now i cud figure it out, here is the solution as reported by many
thanks

james

[Bug 225749] Re: Ubuntu 8.04 LiveCD fails to boot when RTL8102E LAN chip is enabled - with modprobe abnormal exit on ICH8M laptop

carlo82
Sat, 14 Jun 2008 08:20:34 -0700

Great! thanks everybody! Thanks Esa! I tried your suggestions and my LAN works!
Just to make it clear for anybody who could have similar problem, I'm posting 
exactly what I did:

My notebook is a toshiba L300-11A (PSLB0E)

NB: please read the whole thread before following this how-to to make
sure you have the same problem as I had

1) disable your LAN from the bios
2) install ubuntu 8.4
3) download the files from the links above and copy to your pc (home folder, 
desktop....don't think that's relevant)

NB: numbers here may change with new releases...don't panic just look
for similar files (also be careful locating the ones that match your
hardware configuration) and everything will be ok. (mail me if you want
the files I used)

4) install linux-headers-2.6.24-19_2.6.24-19.33ubuntu11_all.deb (simply 
double-click and give your sudo password)
5) install linux-image-2.6.25-2-686_2.6.25-4_i386.deb
6) install 
linux-backports-modules-2.6.24-19-generic_2.6.24-19.18ubuntu3_i386.deb
7) install linux-ubuntu-modules-2.6.24-19-generic_2.6.24-19.28ubuntu3_i386.deb

8) reboot, enable your lan from the bios.
9) at grub prompt choose kernel 2.6.25-2 (it should be the first option)
10) have a beer, and enjoy your lan working!

I used the latest files found following links provided above, so thanks
everybody, great job!

to find the latest linux-image as ESA said, I just googled for 
linux-image-2.6.25 deb

hope anything is clear now also for a beginner!

carlo

---

