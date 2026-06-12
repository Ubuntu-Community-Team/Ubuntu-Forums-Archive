---
title: "Scan for wireless networks -- no results"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by smooveg on 2008-01-26
I know there are a ton of posts about this, but I just can't seem to get my wireless card to recognize any available wireless networks.

I've done everything in the book, scanned for networks (using iwlist scan) and still nothing:

ndiswrapper -l (driver installed, device present with alt. driver ath_pci listed)
iwconfig (shows wlan0 as 802.11g etc....)
ifconfig (shows eth0, lo, wlan0, wlan0:ava) -- what is wlan0:ava????
ifconfig wlan0 up (no scan results after the up)
/etc/modules (shows ndiswrapper at startup)
lshw -C network (shows Atheros card with ndiswrapper+net5211 as driver)
modprobe ndiswrapper (no scan results after reloading module)

I think I've lost it!! If I could configure the card to at least recognize then devices, then I can deal with configuring it either with terminal or a front-end, but this is crazy.

Any advice or other tests to perform would be greatly appreciated!

---

### Post by kevdog on 2008-01-26
Its

sudo ifconfig wlan0 up
iwlist scan


Just a side question -- why are you using ndiswrapper when you could be using the madwifi driver (ath_pci)?

---

### Post by smooveg on 2008-01-26
> **kevdog said:**
> Its

sudo ifconfig wlan0 up
iwlist scan


Just a side question -- why are you using ndiswrapper when you could be using the madwifi driver (ath_pci)?

Good point -- I tried to compile madwifi and the install didn't work right. I'm not sure -- it it is a repository?

I did do the -- sudo ifconfig wlan0 up -- and no results as before.

---

### Post by kevdog on 2008-01-26
Under synaptic, search for linux-restricted-package or just restricted.  You want to install the linux-restricted package that is specific to your kernel version.

Your kernel version can be found by typing:
uname -r 
at the Command Line.

If it successfully installs, make you you either blacklist ndiswrapper or remove or comment out the ndiswrapper line inside the /etc/modules file.

Try rebooting once the driver is installed and see if it is associated with the ath_pci driver (can check with lshw -C network)

---

### Post by smooveg on 2008-01-26
Kevdog,
I think I was diagnosing this with one of your other excellent posts! Give me a chance to run this tonight and get back with you tomorrow....

---

### Post by smooveg on 2008-01-26
By the way -- is there a general file that I would check/edit for all wireless drivers installed? I want to make sure that I blacklist everything that could possibly cause a conflict.

---

