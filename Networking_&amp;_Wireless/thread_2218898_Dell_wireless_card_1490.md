---
title: "Dell wireless card 1490"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by josdb on 2014-04-22
After upgrading to Ubuntu 14.05 my Dell wireless card 1490 doesn't work anymore. I know this topic has been handled before, but none of the solutions offered there worked. I must say that up till now (Ubuntu 12.04, Ubuntu 13.10) it always worked perfectly, no problem. One of the solutions previously offered was, ironically, upgrading to 14.04! I have a Dell Latitude D531. Thanks for any help.

---

### Post by chili555 on 2014-04-23
In those previous threads, we always needed:```
lspci -nn | grep 0280
```If it is a Broadcom, please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by josdb on 2014-04-24
The result of lspci -nn | grep 0280

is:
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

But  then, according to the link you mention, which was one of the  discussions I consulted, I proceeded to install linux-firmware-nonfree  and was told that it was already installed.

I got it working by  installing ndiswrapper and then using the Dell driver for Windows. But I  find that disappointing: to be forced to use a Windows thingy while it  should work purely under Linux. It worked perfectly before under Ubuntu  12.04 and 13.10, without a Windows driver, so it should work again now.  Only, however I tried, I couldn't find the method again I used under  12.04 to get it working. I only remember that it was a Ubuntu package  from Broadcom's website. Apparently it's gone.

To be able to use the Windows driver with ndiswrapper I had to blacklist bcm43xx in /etc/modprobe.d

I would rather have used another, pure Linux method, but as they say: if it works, don't touch it, and it works now, so I guess I'm stuck with it.

Thanks!

---

### Post by chili555 on 2014-04-24
> so I guess I'm stuck with it.Not at all. We can fix it easily and quickly if you're ready.>  I had to blacklist bcm43xx in /etc/modprobe.dThere is no module bcm43xx since a looonnnngggg time ago. ```
chili@T410:~$ modinfo bcm43xx
modinfo: ERROR: Module bcm43xx not found.
```

---

### Post by josdb on 2014-04-24
> Not at all. We can fix it easily and quickly if you're ready.

So tell me...

> There is no module bcm43xx since a looonnnngggg time ago.

Ha ha! Then I found a very old solution from a loooooooooooooonnngg time ago. But it was the only one that worked for me.

Thanks!

---

### Post by chili555 on 2014-04-24
First, verify that you have the correct firmware:```
sudo dpkg -s linux-firmware-nonfree | head -n5
```If it isnt installed, get it:```
sudo apt-get install linux-firmware-nonfree
```Now remove the usually conflicting package:```
sudo apt-get purge bcmwl-kernel-source  [COLOR="#FF0000"]<--this is the step that many miss[/COLOR]
```And the same for ndiswrapper:```
sudo apt-get purge ndiswrapper*
```Check your blacklists:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```If b43 or ssb is blacklisted, remove the line(s). Proofread carefully, save and close gedit. 

Check what modules are forced to be loaded:```
gksudo gedit /etc/modules
```If wl or ndiswrapper is listed, remove them. Proofread carefully, save and close gedit. 

Reboot. How is your wireless working?

---

### Post by josdb on 2014-04-25
> Reboot. How is your wireless working?

Perfect! Thanks a lot! Could it be that "purge bcmwl-kernel" made all the difference?

---

### Post by chili555 on 2014-04-25
> **josdb said:**
> > Reboot. How is your wireless working?

Perfect! Thanks a lot! Could it be that "purge bcmwl-kernel" made all the difference?Yes, exactly. Purge, baby, purge!

---

