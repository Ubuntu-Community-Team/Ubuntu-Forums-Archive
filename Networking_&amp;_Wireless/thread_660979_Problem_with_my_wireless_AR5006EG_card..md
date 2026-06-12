---
title: "Problem with my wireless AR5006EG card."
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by edward fish on 2008-01-07
So I'm running an Acer Aspire 5100 lap top. 
It came with Vista, which is gross... so I've been trying to get my 
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01) card to work on Ubuntu 7.10

With now luck, I have the ndiswrapper installed, and the "correct" driver net5211
Still no luck

My iwconfig:
edward@Christmas2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

So now I'm confused, it worked for a second last night, I rebooted and turned on and of my wireless card via the little switch on the front of my lappy.

Then I turn it off for the night, reboot to Vista this morning, then back to Ubuntu and I have no wireless card again...

Help?

This might help:
edward@Christmas2:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

---

### Post by edward fish on 2008-01-07
Bump for help :confused:

---

### Post by Digger78 on 2008-01-07
you need to enable the function keys/buttons so that you can enable your card.

[http://ubuntuforums.org/showpost.php?p=4086196&postcount=27](http://ubuntuforums.org/showpost.php?p=4086196&postcount=27)

---

### Post by ugm6hr on 2008-02-03
Sorry, haven't read the whole thread, just trying to put AR5006/7 users in touch with potential solutions.

This may be of relevance:

[http://ubuntuforums.org/showpost.php?p=4259805&postcount=14](http://ubuntuforums.org/showpost.php?p=4259805&postcount=14)

---

### Post by lswest on 2008-02-03
also, have you blacklisted the alternate driver? under um /etc/modprobe.d/blacklist append ```
blacklist ath_pci
``` to the file.  Then reboot.  That's usually the problem i had, that the 2 conflicting drivers sort of cancelled each other out.

also, did you modprobe ndiswrapper?
```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
gksudo gedit /etc/modules
``` and on the last file add "ndiswrapper" to the end of the file.

---

### Post by phyz on 2008-02-13
is there any one could find for this problem solution of atheros AR5006EG wifi card?

does upcoming new version of 8.04LTS will solve this kind of problem too?

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i80

blacklist ath_pci
```

but it still won't work

---

### Post by dca on 2008-05-01
I used this:
 
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

