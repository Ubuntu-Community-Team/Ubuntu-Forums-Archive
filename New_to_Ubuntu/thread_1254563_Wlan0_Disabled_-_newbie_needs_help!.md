---
title: "Wlan0 Disabled - newbie needs help!"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by supercarl on 2009-08-31
Hi all,

Just installed Ubuntu 9.04 as tired of Vista. Unfortunately my wireless card is "DISABLED".

I have checked the restricted drivers and it's not there.

Does anyone have any suggestions? The chipset is Ralink RT61 I believe, and it is registered as wlan0 on the system. I have been searching and trying for hours now!!

Thanks in advance (PS I am an absolute beginner and the extent of my terminal use is following instructions on the internet - Sorry!)

---

### Post by supercarl on 2009-08-31
ps it is not a laptop, so no physical "off" button, it is a pci card.

---

### Post by mapes12 on 2009-08-31
I also have a Ralink. This is the line from ```
lspci
``` for my adapter > 00:0f.0 Network controller: RaLink RT2561/RT61 802.11g PCIMine works faultlessly. Does your adaptor look the same as mine in lspci?

---

### Post by supercarl on 2009-08-31
Exactly the same, but with the address 02:05.0 at the start.

---

### Post by supercarl on 2009-08-31
Sorry about multiple posts, working on two computers so that I have internet access, and trying to post all relavent info.

Attempting :

sudo ifconfig wlan0 up 

Results in:

SIOCSIFFLAGS: Device or resource busy

---

### Post by gchand7 on 2009-08-31
This may be too simple. Have you right clicked on the internet icon and checked the box for enable wireless internet. Usually UBUNTU installs everything. Hope this helped

---

### Post by supercarl on 2009-08-31
Hi, yes the boxes are both ticked (Wired and Wireless), but wireless is greyed out in the main menu (when you left click)

Also, to clarify, it hasn't been disabled in bios, and the pci card worked previously in Windows

---

### Post by supercarl on 2009-08-31
Delighted to say that perhaps the simplest fix has worked. Take apart computer, remove PCI card, boot. Reinstall card, boot. Job done (and posting from my new linux desktop as opposed to my linux netbook now!)

Thanks for the help along the way

---

