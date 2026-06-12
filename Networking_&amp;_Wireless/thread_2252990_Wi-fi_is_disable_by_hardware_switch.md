---
title: "Wi-fi is disable by hardware switch"
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by brino_nugraha on 2014-11-16
please help me.
when finished installing Ubuntu LTS 14:04, can be connected to an ethernet network, whereas when attempting a wireless connection.
Enable Wi-Fi facilities are black writing and can not be connected because it says disabled by hardware switching.
my pc:
Lenovo G40-30.

---

### Post by jeremy31 on 2014-11-16
> **brino_nugraha said:**
> please help me.
when finished installing Ubuntu LTS 14:04, can be connected to an ethernet network, whereas when attempting a wireless connection.
Enable Wi-Fi facilities are black writing and can not be connected because it says disabled by hardware switching.
my pc:
Lenovo G40-30.

A quick shot in the dark since it is Lenovo ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
```

If it doesn't work, follow the instruction in stickied post "Before posting in Networking and Wireless" to run the wireless script and attach results

---

### Post by grahammechanical on 2014-11-16
Do you have a user manual? What does that say about activating wireless? If you have Windows 8 installed have you disabled/switched off wireless in Windows 8? That will likely prevent Ubuntu from using wireless as Ubuntu is not able to override that Windows 8 setting. Check out page 30 of this Lenovo guide. You may have Airplane Mode activated. That will switch off all devices that transmit in any way. It will also save battery power.

[http://download.lenovo.com/consumer/mobiles_pub/lenovo_g_z_40_series_hmm.pdf](http://download.lenovo.com/consumer/mobiles_pub/lenovo_g_z_40_series_hmm.pdf)

Regards.

---

### Post by praseodym on 2014-11-16
Check this one:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

