---
title: "ndiswrapper + bcm driver causing lockups"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by stldirty on 2008-06-13
ok i have an hpdv6000 running hardy 64 bit and i had the restricted wireless card drivers enabled.  my internet was going extremely slow and i wasn't able to figure out why so i figured i'd try the tutorial [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc") that has worked for me in the past.  ever since i've done this, however, my computer has been experiencing random freezes.  is there anyway to either stop these freezes or revert back to what i had before and fix the slow wireless internet? thanks in advance!

---

### Post by Ayuthia on 2008-06-13
> **stldirty said:**
> ok i have an hpdv6000 running hardy 64 bit and i had the restricted wireless card drivers enabled.  my internet was going extremely slow and i wasn't able to figure out why so i figured i'd try the tutorial [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc") that has worked for me in the past.  ever since i've done this, however, my computer has been experiencing random freezes.  is there anyway to either stop these freezes or revert back to what i had before and fix the slow wireless internet? thanks in advance!
You could try going to [www.hp.com](www.hp.com) and see if you can get the XP driver for your laptop.  Or you can try this [one]("ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe").  I have a dv6338se and this one works for mine.

If you want to go back, you will need to edit /etc/modprobe.d/blacklist and add:
```
blacklist ndiswrapper
```
and remove any lines that contain the following:
```
blacklist b43
blacklist b43legacy
blacklist ssb
```
You will also need to edit /etc/modules and add the following:
```
b43
```
and remove:
```
ndiswrapper
```
You will need to edit the files in admin mode (sudo).  An example:
```
gksu gedit /etc/modprobe.d/blacklist
```
If you used version 0.3, then you are set.  If you used a script that goes into /etc/rc.local or /etc/init.d, then you will need to comment out the lines in the script.

To see if the b43 driver works without rebooting:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
```and that should turn on your wireless.

---

### Post by stldirty on 2008-06-14
wuts the difference between ur method and the method that caused it to freeze in the first place?

oh and thanks for helpin me revert back to what i had before.

---

### Post by stldirty on 2008-06-14
double post...

---

### Post by Ayuthia on 2008-06-14
> **stldirty said:**
> wuts the difference between ur method and the method that caused it to freeze in the first place?

oh and thanks for helpin me revert back to what i had before.

I was just saying that if you tried a different driver, it might fix your freezing problem.  Sometimes the problem with freezing could be the driver or else it is a bug in the ndiswrapper code.  If a different driver does not work, you could always try compiling the most recent version of ndiswrapper (which is 1.53 as of today).

The driver that I think that you used (34152?) was the driver that I used in Gutsy, but the driver that I recommended was the XP driver for my laptop that I retrieved from the HP site.

---

### Post by stldirty on 2008-06-14
you kno what.  im starting to thing that the problem is with my router.  i just connected to another router and the restricted driver seems to be working much better now.  i'm gonna do a little bit more testing before i make in conclusions though.  i'll try that driver also and report back.  thanks again for the quick response!

---

