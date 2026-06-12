---
title: "Malfunction wireless (AR242x)"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Sir Boss on 2008-08-11
I recently bought a brand-new hp computer and installed Hardy Heron...everything works great, except my wireless card.  My computer informed me that "restricted drivers" had been installed and were running, my card itself showed the blue "go" light, and lsmod showed loaded modules (ath_hal, ath_pci, wlan).  But my wireless device doesn't show up in ifconfig or iwconfig, or in the Network Manager of gnome.  Any ideas?

---

### Post by dca on 2008-08-11
The version of MadWifi used needs to be patched, I used this how-to:
 
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)
 
Towards bottom of first post, it starts with this:
 
"The following are simple steps to compile and install the driver:"

---

### Post by dca on 2008-08-11
Not that it matters but it's the same card I have in my Acer laptop.  It's a mini-PCIe card from Ambit.  It uses Atheros AR5BXB63 chip set, you can confirm by popping off the cover underneath your laptop and a sticker should be sitting next to the antennae leads.
 
It shows up in Windows XP as: AR5006EG
Linux kernel prior to 2.6.23:  AR5007EG
Windows Vista & post 2.6.23: AR242x
 
...the only distro that allows for usage with no patching is using Mandriva and it's packaged MadWifi.  I guess it's because they make a distro that works out of the box for the Asus eeeeeeeeeeeeeePC laptop dealie, so their MadWifi is pre-patched properly.

---

