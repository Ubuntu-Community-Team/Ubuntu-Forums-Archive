---
title: "Is WEP support buggy (Ralink RT2500)?"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by bluedalmatian on 2008-08-22
Is WEP support (using RT2500 driver) on Linux buggy?  Because I cannot get any of my Linux machines running Ubuntu 7 & 8 to authenticate to a Wifi network with WEP 64 or 128 bit.

If I turn WEP off on the basestations and make it an open network it connects OK and with WEP on our Macs & Windows machines can connect OK but not Ubuntu.

I was wondering if it might be a problem related to Apple Airport basestations in particular and would be interested to know has anyone else had any success or failure with an Apple Airport based WiFi network?

Im contemplating dumping the Apple access points for Netgear ones as Ive had other problems with them in the past.

---

### Post by pastalavista on 2008-08-22
I use a Linksys 54G router and WEP 64-bit hex-key security and it works fine with my Atheros-wireless Acer laptop. Sometimes, when I first boot up, the Atheros driver will be mysteriously disabled and I have to enable it manually in the restricted drivers applet and reboot. I don't know why it is being disabled, but I suppose bugginess is an appropriate diagnosis. When I had Gutsy (before upgrading to Hardy) it never failed to work properly.

never mind... it has nothing to do with your problem, does it?

---

### Post by coffeecat on 2008-08-22
I can't answer your question as I don't have a ralink wireless NIC, But have you seen [this howto]("http://ubuntuforums.org/showthread.php?t=564419")? The second post links to a 62-page (and counting. :( ) thread on the RT2500. I hope you can find what you need somewhere in there. Good luck.

---

### Post by tangibleorange on 2008-08-22
i have an RT2500 USB adaptor, and it works fine with WEP and WPA. i'm not sure what the problem might be. when you say its buggy, what exactly is wrong? network manager has never worked happily with Ralink...

---

