---
title: "UK Speedtouch ADSL - at boot"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Torrbrook on 2007-11-15
I am absolutely new to Ubuntu.  I have installed Gutsy 7.10.  I then successfully installed my Speedtouch 330 USB modem, in accordance with UKSpeedtouchDSLHowTo.  To get it to connect I have to enter pon adsl at the command line.  I really need the modem to connect at boot.  There is a guide UsbAdslModem/SpeedTouch which shows how to write and install a bootscript, but I fear that the two documents are describing different methods of installation and that mixing them could cause me much grief.  If anybody could show me an answer related to the UKSpeedtouchDSLHowTo method I'd be most grateful.

Torrbrook

---

### Post by spd106 on 2007-11-16
I don't use a speedtouch modem, but I think you can be fairly confident in using the same bootscript as on the [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) page.

Obviously, you'll change pon speedtch to pon adsl instead. But other than that there shouldn't to be any changes. All it does is run that command on startup, rather than make you do it manually afterwards. 

As far as I know upstart is still compatible with this method, though it's probably not the preferred method these days.

---

### Post by Torrbrook on 2007-11-17
Thank you very much, spd106 - totally successful.

Torrbrook

---

