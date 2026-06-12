---
title: "Big problems with ATI drivers"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-08-01
Hello all,
For 3 hours I am trying to make my laptop work.
I wanted to install the fglrx-amdcccle drivers and after i've installed it the display doesn't want to work anymore.
I have tried a lot of things:
dpkg-reconfigure xserver-xorg  doesn't work.
I've unistalled the fglrx-amdcccle and modified the xorg.conf!

Can anyone help me step by step to resolve this problem?

I can work only from Safe Mode with CLI.
After 
```
lspci | grep VGA
```
I have ATI RC410 Radeon Express 200M


Can i install from scratch the video drivers?And how?

---

### Post by RomeReactor on 2009-08-01
Hi. How did you install the drivers--downloaded from AMD's website, or from the Hardware Drivers application? Have you tried booting in Recovery mode and using XFIX?

---

### Post by halitech on 2009-08-01
It's not listed here but I think your card has been moved to legacy support which means trying to use the newer driver with 9.04 won't work so if you had it working with the open source driver, chances are thats the best you will get.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

---

### Post by vasiauvi on 2009-08-01
OK.
I've resolved the problem with this :
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) 

Offf, it's working!
After 3 hours of searching, the answer was on Ubuntu official page. 
Stupid me!!!

At least I've learned an other thing with linux.Don't loose your faith ! :)

---

### Post by vasiauvi on 2009-08-01
> **halitech said:**
> It's not listed here but I think your card has been moved to legacy support which means trying to use the newer driver with 9.04 won't work so if you had it working with the open source driver, chances are thats the best you will get.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)
Thank you!
I will let just like it was and it is now!
I wanted to install ATI Catalyst to make a dual monitor, but now my dreams are over on this.
I will be satisfied with just what I have!

Thank you for helping me!

---

### Post by 3rdalbum on 2009-08-01
> **vasiauvi said:**
> At least I've learned an other thing with linux.Don't loose your faith ! :)

Another thing that's good to learn for computing in general: Read the release notes :-)

It's a pity you've got a laptop. (I assume it's a laptop due to the Mobile graphics?). I have a computer with the desktop version of that chipset, and if I want to I could buy an AGP graphics card that is supported by the ATI or Nvidia graphics driver.

---

### Post by vasiauvi on 2009-08-01
I see now that after I've modified xorg.conf my internet connection doesn't work!
That's wearied!

Ok! A restart worked out!

---

