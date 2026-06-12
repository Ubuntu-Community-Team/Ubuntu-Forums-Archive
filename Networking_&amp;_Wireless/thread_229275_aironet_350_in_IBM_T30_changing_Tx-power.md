---
title: "aironet 350 in IBM T30 changing Tx-power"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by aka5ha on 2006-08-04
Hi All,

Everything works great in my T30.  I see that the aironet 350 Wi-Fi card is running at the highest power, 100 mW, and in CAM mode (continuous aware mode - no power savings).  In XP you can select 20 mW Tx-power and power saving PSP mode (power save polling), which works just fine, and increases battery life a lot.  

Any gurus know how to control the card parameters, which are listed in /proc/driver/aironet Config?  I am not experienced enough to know what to do.  Cannot $sudo edit Config or even $sudo cp Config Config.bak due to no permissions.  

Thanks in advance!

---

### Post by aka5ha on 2006-08-04
Hi,  

I have an update.  I can view the possible txpower states using iwlist eth1 power.  I can then set it using iwconfig eth1 power.  So now I am running 7mW instead of 100mW.  

Remaining question is how would I enable power management for the aironet 350, or change it from CAM to Max PSP?

Thanks!

---

