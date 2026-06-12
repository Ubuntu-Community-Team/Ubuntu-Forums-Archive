---
title: "broadcom 4311 trouble"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Higgy76 on 2008-11-14
Im new to ubuntu and I need to figure out how to get my wireless working. I have a broadcom 4311 in my laptop and how to get it to work with ubuntu if you could help me i would appreciate it thanks

---

### Post by Ayuthia on 2008-11-14
> **Higgy76 said:**
> Im new to ubuntu and I need to figure out how to get my wireless working. I have a broadcom 4311 in my laptop and how to get it to work with ubuntu if you could help me i would appreciate it thanks

Have you tried going to System->Administration->Hardware Drivers and activating the Broadcom STA (wl) option?  If you have a wired connection, you can also try the open source b43 version.  You only need to activate one, not both.

---

### Post by dedyisn on 2008-11-14
> **Higgy76 said:**
> Im new to ubuntu and I need to figure out how to get my wireless working. I have a broadcom 4311 in my laptop and how to get it to work with ubuntu if you could help me i would appreciate it thanks

Try to Open this link
:guitar:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Higgy76 on 2008-11-14
Ok i did all that in the link but the thing is ubuntu dosent even see the broadcom on my computer right now. How would i make it visable

---

### Post by Ayuthia on 2008-11-15
Can you go into the Terminal and post the results of:
```
lshw -C network
```
It will help give some information about what you wireless card is doing.

---

### Post by Higgy76 on 2008-11-15
I got it working thanks for the help

---

### Post by buccaneere on 2008-11-15
Cool!

We won't get mad if you post up the solution. :)

---

### Post by Higgy76 on 2008-11-15
Well i had it working i followed the steps in the link above but after i shut down for the night and turned it back on today it wont work. So I need to no how to keep it from going back to the other settings

---

### Post by Ayuthia on 2008-11-15
> **Higgy76 said:**
> Well i had it working i followed the steps in the link above but after i shut down for the night and turned it back on today it wont work. So I need to no how to keep it from going back to the other settings

You can try the following:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
echo wl | sudo tee -a /etc/modules
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo update-initramfs -u

```
That will blacklist the b43 and ssb modules and add wl to load on reboot after the kernel modules have loaded.  The update-initramfs will help prevent the b43 module from loading when the kernel is getting things set up on reboot.

Hope that works.

---

