---
title: "Bluetooth connection problem in V. 14.04 LTE 64 bit"
date: 2015-07-27
forum: Networking &amp; Wireless
---

### Post by Malcolm_Brown on 2015-07-27
I have a Toshiba Satellite Pro C50-A-1K9 running a new installation of Ubuntu 14.04 LTE 64 bit.  I use a USB dongle.  Here is the output from 'lsusb'

lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b41a Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 013: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have disabled wireless from the keyboard, but the dongle appears ok.
Here is the output from rfkill.....
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



I am trying to link to a Bose SounLlink Mini using Bluetooth.  No success.  The USB dongle works fine on a 32 bit installation of 14.04 LTE on an older computer.

Any ideas?

Thanks.

---

### Post by jeremy31 on 2015-07-27
Delete the pairing
```
sudo pactl load-module module-bluetooth-discover
```
Then pair with the audio device again

---

### Post by Malcolm_Brown on 2015-07-28
Thank you for replying.

Unfortunately it had no effect - still no pairing with the audio device.

I have used the options under the bluetooth icon in the top screen line.  I have also installed Bluetooth Manager - still no joy.

If you have any further ideas, I would be happy to try them.  Thanks.

---

### Post by Malcolm_Brown on 2015-07-28
I now believe that the audio device I am trying to pair with has an intermittent fault in the electronics, as I have linked this computer successfully to a mobile phone.

Intermittent faults are the worst! Fortunately the audio device is still within its warranty period.  

Thanks for your help.

---

