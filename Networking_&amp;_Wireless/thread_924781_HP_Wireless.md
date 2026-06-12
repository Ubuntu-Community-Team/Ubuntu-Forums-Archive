---
title: "HP Wireless"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Prominence on 2008-09-19
My HP can't detect the wireless, but I have a feeling it can somehow. Everything else is perfect, what do you guys think? I only ran it out of the disk if that helps any.

---

### Post by Ayuthia on 2008-09-19
> **Prominence said:**
> My HP can't detect the wireless, but I have a feeling it can somehow. Everything else is perfect, what do you guys think? I only ran it out of the disk if that helps any.

Can you provide some information about your wireless card?  If you go into the Terminal you can find your wireless card information by typing:
```
lspci -nn
```Look for somehting that says Ethernet Controller or Network Controller.  If you find it, can you post the results.  You can also check for your network cards by doing (also in the Terminal):
```
lshw -C network
```

Most likely your wireless will work, but it might be a matter of installing a driver or firmware to get it to work.

---

### Post by Prominence on 2008-09-19
Is there a way to do this in windows? I don't feel like starting it up in a CD boot just to do that.

---

### Post by Ayuthia on 2008-09-19
> **Prominence said:**
> Is there a way to do this in windows? I don't feel like starting it up in a CD boot just to do that.

There should be a way to find it in windows.  I think you have to go into Administration and somewhere in there you have to find device manager.  You will then have to find your wireless card and click on properties.  There should be a series of tabs and I think that one of them is driver info.  You will then have to go through the dropdowns and look for the pci id. 

Unfortunately, I don't use Windows very often and I can't remember the exact names for where it is exactly.

---

### Post by Prominence on 2008-09-20
Broadcom 802.11b/g WLAN

---

### Post by Ayuthia on 2008-09-20
There are a few options:
b43:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

ndiswrapper:
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)

wl:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

wl (using a kernel from hardy-proposed):
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

The ndiswrapper and wl drivers are ones where you are going to need more information about your card.  When you have a chance to look into Ubuntu and grab the model of the Broadcom card, you will be able to determine what windows drivers your need for ndiswrapper or if the wl driver will work for your card.

So if you are just wondering if the Broadcom card will work, it should.  You can always go the Wubi route if you are still not comfortable.  It won't give you the performance, but it does not require you to partition your hard drive to make it work.  You can also remove it if you are not happy (and not mess with trying to rebuilding everything if you don't like Ubuntu)

---

