---
title: "I upgraded and my internet doesn't work"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by sqeelurgle on 2008-07-11
I recently upgraded from 7.04 to 7.10.  Now my internet doesn't work.  When I right click on the connection icon on the toolbar, it says "no network device detected" in the menu that pops up.  As far as I can tell, the ethernet card is enabled.  When I go into network tools, it shows the NIC sending and receiving packets.  I can't ping anywhere.  It worked fine under 7.04, and works fine when I boot the box to windows.  What should I try next?

Thanks

---

### Post by AliTabuger7 on 2008-07-11
What brand is the connection device? You may have to install proprietary drivers.

---

### Post by sqeelurgle on 2008-07-11
> **AliTabuger7 said:**
> What brand is the connection device? You may have to install proprietary drivers.

There is the onboard NIC (ASUS K8N motherboard with nVidia chipset) into a motorola ADSL modem.  The whole setup worked perfectly under 7.04.  I wonder if there was a config setting that didn't transfer properly or something?

Thnaks

---

### Post by sqeelurgle on 2008-07-11
OK, it's wierd, but the network still says it can't find a network device, but the internet is in fact working fine.  I just downloaded some patches, and this is being typed on the Ubuntu install.  I guess if it says it's broken, but actually works then I can live with that.  It's strange though

Thanks

---

### Post by AliTabuger7 on 2008-07-12
I actually had one of those motherboards.

Theres one thing you really need to know about it. My K8NSC-939 hid the Aperture size from me, but set it too small. X ran into all sorts of trouble. Theres a weird hotkey combination you have to use in the bios to access "advanced features" or something. I think it was ALT and an F* key. You will know if you need to do this if your Splash (ubuntu logo during boot) does not work right.

---

