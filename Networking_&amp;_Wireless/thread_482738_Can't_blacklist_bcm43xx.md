---
title: "Can't blacklist bcm43xx"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by Drate on 2007-06-24
I am currently using Ubuntu Studio, and had one previous attempt at standard Feisty in which I ran into similar problems as I'm about to describe.

I have put the "blacklist bcm43xx" line in /etc/modprobe.d/blacklist file, but ndiswrapper is still using it as an "alternative driver" and therefore won't let my card function properly... why am I havin this problem in Feisty when the blacklisting worked wondermously in Edgy?

WTF mate?

---

### Post by Drate on 2007-06-30
Bump

---

### Post by kevdog on 2007-06-30
Hello

If you type lsmod at the command line it will show if the driver is actually loaded.

Also if you type:
sudo modprobe -l | grep bcm43

Mine shows:
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

If you physically want to remove the module then type
sudo modprobe -r bcm43xx.ko

---

### Post by Drate on 2007-07-02
I believe that did it... except are you sure that command shouldn't read "sudo modprobe -r bcm43xx"?  Cuz your way it gave me some "I cain't find it!" error, then I tried it without the ".ko" at the end and I got no error, restarted, and though ndiswrapper still has bcm43xx as an "alternate driver" I seem to not be getting the conflicts anymore... so, yay!  And thanks.

---

### Post by kevdog on 2007-07-02
Yes, you were right about the syntax, sorry about that.  

Two things, if you do a 
lsmod | grep bcm
at the command line, and bcm43xx isnt listed, then the module isnt currently loaded.

If you do a
modprobe -l | grep bcm
and the bcm43xx module isnt listed, then its impossible that the module could become loaded.

I have bcm43xx listed as an alternate driver, but this doesnt cause any problems at least for me!

---

