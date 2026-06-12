---
title: "Gobi un2400 (3g modem) doesn't appear in network manager"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by quina on 2014-06-17
hello!
I have a problem because i can not use my integrated 3g modem (gobi un2400) in my laptop (hp6730b). I always had problem to make this modem working (12.04, 12.10), but in the end it was working. But not know on 14.04.

What I did:
installed gobi-loader and put in /lib/firmware/gobi these files: amss.mbn, apps.mbn, uqcn.mbn (extracted from windows driver)

then
**rfkill unblock wwan && lsusb**

```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b059 Chicony Electronics Co., Ltd CKF7037 HP webcam
Bus 001 Device 004: ID 03f0:201d Hewlett-Packard un2400 Gobi Wireless Modem (QDL mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**dmesg |grep modem**

```

[    4.174689] usbserial: USB Serial support registered for Qualcomm USB modem
[    4.175796] qcserial 1-2:1.0: Qualcomm USB modem converter detected
[    4.175878] usb 1-2: Qualcomm USB modem converter now attached to ttyUSB0
[    7.338098] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[   50.834906] qcserial 1-2:1.0: Qualcomm USB modem converter detected
[   50.835008] usb 1-2: Qualcomm USB modem converter now attached to ttyUSB0

```

I also used:
**/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi && restart network-manager**

Now  when I open network-manager I dont see this device. When I creating new conection, choosing broadband, under "create conection for device:" there is nothinf to choose.

Any ideas?

---

### Post by Gartral on 2014-07-23
hey, I'm having a very similar issue, however I can't get gobi-loader to actually.. load.. the firmware to the card, it just hangs! or it's taking a retarded amount of time, how long does it take for you?

---

### Post by hibr-list on 2014-08-24
> Bus 001 Device 004: ID 03f0:201d Hewlett-Packard un2400 Gobi Wireless Modem (QDL mode)

"QDL-Mode" shows that your firmware was not loaded properly. As far as I see did you do everything correct.

Furthermore the command "nmcli d" should show the wwan device. The paket "modemmanager" should be installed, too.

I am here on Mint 17 (based on Ubuntu 14.04) on an Thinkpad T-series and can not get Gobi 2000 working. It is not available in the network manager. But i was recognized in Mint 16. 

I have not QDL mode but nmcli and the GUI does not show my wwan. Strange.

That is what I hate on Gnu/Linux: After an upgrade, things do not work anymore which did work before.

Hani

---

