---
title: "ndiswrapper troubles"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by sava6e on 2008-10-26
Hello, I installed hardy on my machine today and everything but my wireless nic card works great. I installed ndiswrapper as well as the driver but when I go to connect to the network it doe not work. Also when I was in live cd it popped up and asked me to install proprietary drivers but now that its installed the proprietary driver option the soem sort of firmware cutter program isn't an option...

Help!

---

### Post by Ayuthia on 2008-10-26
> **sava6e said:**
> Hello, I installed hardy on my machine today and everything but my wireless nic card works great. I installed ndiswrapper as well as the driver but when I go to connect to the network it doe not work. Also when I was in live cd it popped up and asked me to install proprietary drivers but now that its installed the proprietary driver option the soem sort of firmware cutter program isn't an option...

Help!

Can I have some information about your computer?  Can you go into the Terminal and post the results of:
```
lspci -nn
uname -a
ndiswrapper -l
```
It sounds like you might have a Broadcom wireless card, but I would like to verify that and also see the make and model of your wired card (There might be a conflict that we need to work around).

---

### Post by sava6e on 2008-10-28
I have a wmp54g v 1.2 card

Its kind of hard to post the results of those commands since I'm on a different computer. As for my wired nic card it's integrated. My motherboard is a gf7050v-m7.

When I did that ndiswrapper command it said that there was an alternate driver (bcm43xx). I can get more into detail if you really need me to do so.

Thanks for your help thus far...

---

### Post by Ayuthia on 2008-10-28
> **sava6e said:**
> I have a wmp54g v 1.2 card

Its kind of hard to post the results of those commands since I'm on a different computer. As for my wired nic card it's integrated. My motherboard is a gf7050v-m7.

When I did that ndiswrapper command it said that there was an alternate driver (bcm43xx). I can get more into detail if you really need me to do so.

Thanks for your help thus far...
You can try the following to see if the ndiswrapper driver will work:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo iwlist scan
```
If it returns wireless sites, then it is working.  If it does work and you are able to connect, please post the results of:
```
cat /etc/modprobe.d/blacklist | grep -e bcm43xx -e b4 -e ssb -e ndis -e wl
cat /etc/modules | grep -e bcm43xx -e b4 -e ssb -e ndis -e wl
```
It will help us determine what needs to be blacklisted and loaded.

---

