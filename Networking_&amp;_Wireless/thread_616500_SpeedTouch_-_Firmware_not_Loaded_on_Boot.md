---
title: "SpeedTouch - Firmware not Loaded on Boot"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Tsarevich on 2007-11-18
I have a speedtouch 330 ADSL modem and I use the speedtouchconf.sh script to get connected. But my main reason to switch from Fedora was that there were start-on-boot prolblems with this script. So here I have Ubuntu Gutsy Gibbon. Firmware does not start on boot and not surprisingly I cannot connect using:

```
sudo pppd call adsl
```

Help.

---

### Post by Torrbrook on 2007-11-18
I have just been helped with a similar problem - see thread UK Speedtouch ADSL - at boot. I think the PPP over ATM section of the document [https://help.ubuntu.com/community/UKSpeedTouchDSLHowTo](https://help.ubuntu.com/community/UKSpeedTouchDSLHowTo) has been updated with a simple method of installing both the firmware and the bootscript.  I hope it will work in Pakistan.

Torrbrook

---

### Post by Torrbrook on 2007-11-18
Sorry - the link should be [https://help.ubuntu.com//community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com//community/UsbAdslModem/SpeedTouch)

---

