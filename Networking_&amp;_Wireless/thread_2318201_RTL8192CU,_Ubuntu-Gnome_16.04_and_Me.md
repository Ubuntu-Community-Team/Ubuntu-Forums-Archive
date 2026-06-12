---
title: "RTL8192CU, Ubuntu-Gnome 16.04 and Me"
date: 2016-03-23
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2016-03-23
I hadn't broken anything lately and figured I was past due. I haven't been using wifi much lately so figured I'd find out how my old standbys get along with Ubuntu-Gnome 16.04. I plugged in a generic adapter using a RealTek 8192CU chipset. It worked for a few minutes and stopped responding. It showed connected but no ping. Hmmm, some things never change.


Well, let's see if my old standby still works.
```
https://github.com/pvaret/rtl8192cu-fixes

```I had to restart network-manager a couple times to download everything but got it installed. Restart and -- it appears to still be using the old driver. "lsmod" showed this: 


rtl8xxxu


and cfg811 was using it. That's a new one on me.  Added "rtl8xxxu" to the blacklist, restarted and 8192CU device was working as expected. 'Nuther 'gotcha' in  the wild and wonderful world of Linux WiFi.

---

### Post by lotharmat on 2016-03-24
Thanks for this! I've got an RTL8192e (PCi) card which plays nice under 32bit Ubuntu but I really want Chrome (netflix and Videostream) so I need 64bit Ubuntu (aforementioned card doesn't play nice at all).. Debating getting a usb WiFi dongle - What would you recommend?

---

### Post by kurt18947 on 2016-03-24
> **lotharmat said:**
> Thanks for this! I've got an RTL8192e (PCi) card which plays nice under 32bit Ubuntu but I really want Chrome (netflix and Videostream) so I need 64bit Ubuntu (aforementioned card doesn't play nice at all).. Debating getting a usb WiFi dongle - What would you recommend?

If you want an 802.11AC adapter I have no experience so no recommendation. My favorite 'just plug it in and it works' are adapters based on RealTek RTL8192**SU** chipsets such as TrendNet TEW-649UB. It's risky recommending models because some manufacturers change chipsets while keeping the model.D-Link seems notorious for this.  Linux compatibility is based on chip set, not make & model. Realtek RTL-8192**CU** are much more common and require disabling the default driver and installing a patched driver. That's what I was doing that prompted my original post.

---

### Post by guimaster on 2016-12-12
Does your fix still work with kernel 4.4.0-53-generic?

---

### Post by brik2 on 2017-01-25
It works and solve my wifi connection problem !

Thank you !
:D

---

