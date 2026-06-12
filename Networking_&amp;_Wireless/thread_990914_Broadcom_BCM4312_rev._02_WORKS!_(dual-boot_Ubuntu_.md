---
title: "Broadcom BCM4312 rev. 02 WORKS! (dual-boot Ubuntu v8.10 &amp; Vista)"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Joe2Shoe on 2008-11-23
I hope this helps those installing v8.10 using the Broadcom BCM4312 rev. 02 wifi card.

I just did a fresh install of Ubuntu v8.10 (Intrepid Ibex) on my HP dv9000z.
My wifi card is the Broadcom BCM4312 rev. 02.
I did not use NDISwrapper or FWcutter.
I used the driver Ubuntu provided in System/Administration/Hardware Drivers.
It is listed as "Broadcom STA wireless driver".  I clicked on it and 'activated' it, now my wireless connection works, using "WPA & WPA2 Personal".
I am dual-booting Ubuntu v8.10 and Vista.
My wireless works in both.

I installed the Windows Broadcom drivers (bcmwl6.sys and bcmwl6.inf) for my card using NDISwrapper just to see if they worked, and they did NOT!  I had to uninstall them and go back to the "Broadcom STA wireless driver".

I downloaded/installed 89 Security Updates, rebooted, and it still works.

Tallyho,
Joe2Shoe.

---

### Post by Ayuthia on 2008-11-23
> **Joe2Shoe said:**
> 
I installed the Windows Broadcom drivers (bcmwl6.sys and bcmwl6.inf) for my card using NDISwrapper just to see if they worked, and they did NOT! 
Vista drivers (bcmwl6) do not work with NDISwrapper.  You have to use a bcmwl5 driver with NDISwrapper.  They can come from XP, Win2000, or older.

---

