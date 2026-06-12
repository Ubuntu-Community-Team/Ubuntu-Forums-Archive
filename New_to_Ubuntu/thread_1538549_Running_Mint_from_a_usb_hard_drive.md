---
title: "Running Mint from a usb hard drive"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by at2smithjason on 2010-07-25
I have an older computer that I am using for all of my internet needs right now and I would like to have a version of linux on it.  But heres the catch.  I want to install mint on my usb hdd and use that as the primary drive.  I dont want to get rid of windows, because my girlfriend and her son use this computer also.  Is this something that I can do?

---

### Post by Paddy Landau on 2010-07-25
This type of question has been asked many times. I found the following answers, but I haven't tried them myself yet.

[http://ubuntuforums.org/showthread.php?t=1478020](http://ubuntuforums.org/showthread.php?t=1478020)
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

HTH

---

### Post by Zimmer on 2010-07-25
First Make sure your BIOS will boot from an external USB drive..

I have 10.04 loaded on a Verbatim 320gb USB drive.
I have Vista and 8.04 on my laptop internal HDD. (Boot there is covered by EasyBCD and GRUB 1.)

I partitioned the USB drive how I wanted it with gparted (10.04 live CD) then installed 10.04 to a partition on the USB drive and installed GRUB to the MBR of the USB drive.

With the BIOS set to look for CD drive first , then USB, then HDD  I can now Boot with the USB drive plugged in using GRUB2 (on the USB drive MBR) which gives me the options of all the OS's.

If the drive is unplugged I get my usual Boot options for my HDD only.

There is more advice on the community documentation pages under Installation.

---

### Post by oldfred on 2010-07-25
It is mentioned in the links posted above, but it is very important to use the advanced button on the last partition screen to make sure you install grub2 to the external drive.

Install karmic Screens shown with advanced button
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

