---
title: "Ubuntu 14.04 won't use Broadcom BCM4318 on HP dv8000"
date: 2014-05-18
forum: Networking &amp; Wireless
---

### Post by Connor_Schulz on 2014-05-18
Please help...

I've been at this for 3 days now. I have scoured every forum I think the internet has to offer (to no avail) and the Ubuntu documentation site, which is: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The lowdown:
- Using 14.04 trusty tahr
- No WiFi LED light
- installed proper firmware using terminal (instructions from documentation)
- was listed under additional drivers, now isn't
- lspci gives me 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
- modprobe -r wl gives me wl is in use
- rfkill list all displays no results
- ethernet connection works fine

I'm stuck, and honestly do not have a deep understanding of linux commands. I can follow instructions however lol. Can anyone advise? 

I do not believe the WiFi card itself is faulty because the computer would not be able to identify it, right? The port of the computer is tested to be good, since it quickly disables the computer every time I use an Intel card (thanks a lot HP, world's best manufacturer).

Thank you kindly,
Connor

---

### Post by freewarelover on 2014-05-18
Do you see your router listed when you click on the wireless button in the taskbar?

---

### Post by wildmanne39 on 2014-05-18
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by Connor_Schulz on 2014-05-19
Freewarelover

I do not see my router listed. No wireless options whatsoever actually.


Wild Man

I am following your instruction now and I'll post the outcome soon.

---

### Post by Connor_Schulz on 2014-05-19
Thank you Wild Man! It's working great. That was most definitely the solution I needed!

---

### Post by wildmanne39 on 2014-05-19
Your welcome! glad it is working.

---

### Post by Michael_Riese on 2014-08-27
Hi Wild Man.
Thank you for this instructions. It was helpfull for my problem with a laptop ASUS A6000.
It's working fine.

Greetings Michael

---

### Post by kemal2 on 2014-11-24
I get an invalid operation after my password aUTHENTICATION

---

### Post by gsolari2 on 2015-07-24
Please after install linux-firmware-nonfree:

1. install b43-fwcutter 
2. download [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2) end extract3. run: b43-fwcutter -w /lib/firmware   broadcom-wl-5.100.138/linux/wl_apsta.o
4. reboot

This worked for me...

---

