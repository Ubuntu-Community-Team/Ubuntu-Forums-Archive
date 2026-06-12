---
title: "Download wireless drives before installation?"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by PaulHA2 on 2011-07-18
I'm about to install 10.10 on a Dell Vostro 1400. I booted the machine up from the USB key, and realised that the driver for the wireless needs to be installed. Problem is, I don't have easy access to a hard-wired connection. Is there a way to download the driver now, save it on a key, and then install it from that key after I install, as opposed to through a hard connection? Many thanks.

---

### Post by _0R10N on 2011-07-18
I'm not getting you, maybe. If you don't have the drivers for your wireless card, and you don't have a wired connection, neither; how do you intend to download the wireless driver?. Anyway, you could download the driver, store it wherever you want and install it later on, using dpkg

```
# dpkg -i <your_driver_package>
```

Regards!

---

### Post by wojox on 2011-07-18
I agree with _0R10N. Are you dual booting?

---

### Post by PaulHA2 on 2011-07-18
I want to download the wireless driver over a wireless network using either the machine in question (which is running Windows) or my own Ubuntu machine before I install Ubuntu on the Dell -- once I install Ubuntu on the Dell, I'll have no way to it connect to the internet unless I have a hard copy of the appropriate wireless driver. I'll try your solution and let you know what happens. Thanks!

---

### Post by gandaran on 2011-07-18
> **PaulHA2 said:**
> I'm about to install 10.10 on a Dell Vostro 1400. I booted the machine up from the USB key, and realised that the driver for the wireless needs to be installed. Problem is, I don't have easy access to a hard-wired connection. Is there a way to download the driver now, save it on a key, and then install it from that key after I install, as opposed to through a hard connection? Many thanks.
you can install the drivers from the live cd and even after having ubuntu installed already by enabling the cd repository in software sources.
if you happen to need broadcom drivers you can follow this guide
[http://ubuntuforums.org/showthread.php?t=1767919](http://ubuntuforums.org/showthread.php?t=1767919)

---

### Post by 1clue on 2011-07-18
Have you booted from the installation image already in 'try it' mode and verified that the wireless doesn't exist?  If so, and if you can find the proper driver, you should be able to download it and save it on the same or a different usb storage device.

---

### Post by _0R10N on 2011-07-18
Well, it should be quite easy, if you've already found the driver on the net. You can download it and install it after you installed ubuntu. There should be no problem, since Linux comes out-of-the-box with all the tools required for installing software in offline mode.

---

### Post by PaulHA2 on 2011-07-18
> **1clue said:**
> Have you booted from the installation image already in 'try it' mode and verified that the wireless doesn't exist?  If so, and if you can find the proper driver, you should be able to download it and save it on the same or a different usb storage device.

1. Yes, I have. 2. Yes -- what I need to know is HOW to do that.

---

### Post by gandaran on 2011-07-18
> **PaulHA2 said:**
> 1. Yes, I have. 2. Yes -- what I need to know is HOW to do that.
lets see what driver you will need to install, type in terminal 
```
lspci
```
for internal devices
and
```
lsusb
```
for usb adapters
post the output

---

### Post by PaulHA2 on 2011-07-18
Gandaran, your first solution worked perfectly -- it "downloaded" the driver from the USB key, got online just fine. Many thanks!

---

