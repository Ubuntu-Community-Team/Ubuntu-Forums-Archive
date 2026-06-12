---
title: "cisco/aironet 340 series wlan card stopped working."
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by crankcaller on 2005-04-12
I've a cisco/aironet 340 series pci wifi card in my pc.
It works fine under windows and did work fine under an install of hoary that i'd updated via apt-get from a warty install.

I had loads of rubbish on my drive so i did a clean install from a Hoary iso download.
my card is detected:

crankcaller@crankbox1:~$ lspci -v
<<SNIP>>

0000:00:0c.0 Network controller: AIRONET Wireless Communications Cisco Aironet 340 802.11b Wireless LAN Adapter/Aironet PC4800 (rev 01)
        Flags: medium devsel, IRQ 16
        Memory at cfffc680 (32-bit, non-prefetchable) [size=128]
        I/O ports at dc00 [size=128]
        I/O ports at d800 [size=64]

But i can't make it work. It  doesn't even grab an IP from the router.

I've a backup of my old working hoary install. Can I just take the config file or whatever makes the wifi work and copy it across?

If so, what file?

Loving ubuntu so far.  Can see me deleting my windows partition soon as i've got most of my day to day needs already installed.

---

### Post by crankcaller on 2005-04-12
I sorted this out.
Turned off the wep on the router from windows.
Reinstalled Hoary with wep off.  Got it working, re-added wep.

thanks anyone who read my post.

---

