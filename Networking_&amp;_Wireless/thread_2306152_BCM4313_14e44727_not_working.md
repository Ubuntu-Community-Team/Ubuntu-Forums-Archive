---
title: "BCM4313 14e4:4727 not working"
date: 2015-12-12
forum: Networking &amp; Wireless
---

### Post by badwheel on 2015-12-12
Hello,

I just installed Ubuntu 14.04 on an ASUS 1215n with a BCM4313 14e4:4727 wireless card.  I am a complete Ubuntu novice and  have tried for several hours to get this card working with no luck.

Things I have tried: 

Mounting the Ubuntu iso file as a cd and trying to install the proprietary Brodcomm drivers from the software&updates tool.  Result: The tool says it is installing the drivers but seems to hang (I have waited 10 min plus to no avail).

I have tried the "special case 1" instructions under this thread, which I believe are most appropriate for my situation: ubuntuforums.org/forumdisplay.php?f=336
I entered all of the commands, but the settings menu still indicates that the wifi is disabled by the hardware switch.  I have tried the fn+f2 combination and the little wifi button on the laptop to no avail.

---

### Post by Hadaka on 2015-12-12
Hi, do you have a wired connection? if so please go here
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
post the wireless-info.txt file.
thanks.

---

### Post by dellboy56 on 2015-12-12
Hello there you could try with your bootable cd/usb u made and go to pools/main/d/dkms then pools/main/restricted/bcmwl?

---

### Post by badwheel on 2015-12-12
Attached is the wirelessinfo.txt

> **dellboy56 said:**
> Hello there you could try with your bootable cd/usb u made and go to pools/main/d/dkms then pools/main/restricted/bcmwl?

I deleted the bootable drive so I could copy the iso back onto it and update from there.  I can turn it back into a bootable drive though.  Afterwards, you want me to boot from the drive, select try Ubuntu and try to navigate to those directories?  Am i looking for something in particular?

---

### Post by Hadaka on 2015-12-12
Hi please COPY  and paste...
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf
sudo rfkill unblock all
```
boot and test

*If the wireless isnt working try pressing fn/f2 one time
thanks.
report back



* @dellboy6, your suggestion will get the wrong driver for this card,please read the sticky to determine the driver

---

### Post by badwheel on 2015-12-12
> **Hadaka said:**
> Hi please COPY  and paste...
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf
sudo rfkill unblock all
```
boot and test

*If the wireless isnt working try pressing fn/f2 one time
thanks.
report back



* @dellboy6, your suggestion will get the wrong driver for this card,please read the sticky to determine the driver

It worked! I am sending this message form a wireless connection!  Just for reference is that command in a sticky somewhere?  I may convert a few more laptops and would like to be more self sufficient.

---

### Post by Hadaka on 2015-12-12
Hi, glad that worked for you. yes its the same sticky you reffered to in this post,
the command is formatted differently in the sticky, but it does the exact same thing
and that was to blacklist, the b43 and the ssb driver modules.
thanks.

---

