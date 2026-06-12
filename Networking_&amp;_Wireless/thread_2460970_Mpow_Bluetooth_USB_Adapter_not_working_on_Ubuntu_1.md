---
title: "Mpow Bluetooth USB Adapter not working on Ubuntu 18.04"
date: 2021-04-21
forum: Networking &amp; Wireless
---

### Post by hong2 on 2021-04-21
Hi,

I bought [this]("https://www.amazon.com/gp/product/B08L4V9W29/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1") Mpow 5.1 Bluetooth USB Adapter from Amazon, and I am trying to set it up on my Ubuntu 18.04 desktop.

I first tried following the linux driver and instructions provided by Mpow ([here]("https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz")). The installation was not successful. Then I found [this]("https://ubuntuforums.org/showthread.php?t=2448259") post in our forum, which is for the same adapter and on Ubuntu 20.04. I have followed all the instructions in that post but I am still having errors loading the bluetooth adapter. Since my error output is different than the ones in that post, I decided to open a new thread for discussion.

[COLOR=#000000]Currently I've copied, and renamed the[/COLOR][COLOR=#000000][COLOR=#000000] rtl8761a_config file following instructions in the other thread, and also [/COLOR][/COLOR][COLOR=#000000]rtk_btusb is loaded properly on my system. However, bluetooth is still not working properly on my end.[/COLOR]

[COLOR=#000000]The output of dmesg | tail :[/COLOR]
```
[COLOR=#000000]
dmesg | tail                                     
[ 2370.151683] usb 1-1: Manufacturer: Realtek
[ 2370.151685] usb 1-1: SerialNumber: A09F10C04B1A
[ 2370.153785] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 2370.153788] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 2370.153789] rtk_btusb: patch_add
[ 2370.153791] rtk_btusb: auto suspend is disabled
[ 2370.153793] rtk_btusb: pid = 0x2550
[ 2370.153795] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 2370.153805] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 2370.154081] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[/COLOR]
```[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Output of sudo modprobe rtk_btusb && dmesg | grep rtk:[/COLOR]
[COLOR=#000000]```

sudo modprobe rtk_btusb && dmesg | grep rtk            
[  221.030926] rtk_btusb: Realtek Bluetooth USB driver ver 3.1.897f3bb.20201202-173003
[  221.030926] rtk_btcoex: rtk_btcoex_init: version: 1.2
[  221.030926] rtk_btcoex: create workqueue
[  221.030952] rtk_btcoex: alloc buffers 1792, 2432 for ev and l2
[  221.030965] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[  221.030965] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[  221.030965] rtk_btusb: patch_add
[  221.030966] rtk_btusb: auto suspend is disabled
[  221.030966] rtk_btusb: pid = 0x2550
[  221.030966] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[  221.030968] rtk_btusb: probe of 1-1:1.0 failed with error -1
[  221.030971] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[  221.030981] usbcore: registered new interface driver rtk_btusb
[  289.057396] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[  289.057399] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[  289.057400] rtk_btusb: patch_add
[  289.057402] rtk_btusb: auto suspend is disabled
[  289.057403] rtk_btusb: pid = 0x2550
[  289.057405] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[  289.057415] rtk_btusb: probe of 1-1:1.0 failed with error -1
[  289.057726] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[  748.193232] rtk_btusb: rtk_btusb: btusb_exit
[  748.193233] usbcore: deregistering interface driver rtk_btusb
[  748.193256] rtk_btcoex: rtk_btcoex_exit: destroy workqueue
[ 1121.977548] rtk_btusb: Realtek Bluetooth USB driver ver 3.1.897f3bb.20201202-173003
[ 1121.977549] rtk_btcoex: rtk_btcoex_init: version: 1.2
[ 1121.977550] rtk_btcoex: create workqueue
[ 1121.977579] rtk_btcoex: alloc buffers 1792, 2432 for ev and l2
[ 1121.977595] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 1121.977595] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 1121.977595] rtk_btusb: patch_add
[ 1121.977596] rtk_btusb: auto suspend is disabled
[ 1121.977596] rtk_btusb: pid = 0x2550
[ 1121.977596] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 1121.977599] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 1121.977602] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[ 1121.977624] usbcore: registered new interface driver rtk_btusb
[ 1280.653855] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 1280.653858] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 1280.653859] rtk_btusb: patch_add
[ 1280.653861] rtk_btusb: auto suspend is disabled
[ 1280.653862] rtk_btusb: pid = 0x2550
[ 1280.653864] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 1280.653874] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 1280.654158] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1
[ 1965.395564] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 0
[ 1965.395567] rtk_btusb: btusb_probe can_wakeup 1, may wakeup 0
[ 1965.395569] rtk_btusb: patch_add
[ 1965.395570] rtk_btusb: auto suspend is disabled
[ 1965.395572] rtk_btusb: pid = 0x2550
[ 1965.395574] rtk_btusb: get_patch_entry =NULL, can not find device pid in patch_table
[ 1965.395583] rtk_btusb: probe of 1-1:1.0 failed with error -1
[ 1965.395877] rtk_btusb: btusb_probe intf->cur_altsetting->desc.bInterfaceNumber 1

```
[/COLOR]
[COLOR=#000000]I have tried all the methods I found online, and I am running out of ideas. Any help is highly appreciated.[/COLOR]

---

### Post by poor.boy on 2021-04-24
I have exactly the same problem on ubuntu 20.04.
Also my bluez daemon not running and I can't get it up and working.

---

### Post by meavydev on 2021-04-24
The problem is that they don't have a PID of 0x2550 in the fw_patch_table in the driver source rtk_misc.c.
We need an update from Realtek...

---

### Post by meavydev on 2021-04-24
Ah a quick hack and at least it shows up in hciconfig...
I should say I don't know what the correct settings are, I just guessed.
However I edited rtk_misc.c and added this line to fw_patch_table:
    {0x2550, 0x8761, "mp_rtl8761b_fw", "rtl8761bu_fw", "rtl8761b_config", NULL, 0},    /* RTL8761BU only */

This is what shows up in hciconfig:
pi@raspberrypi:~/20201202_LINUX_BT_DRIVER/usb $ hciconfig -a
hci1:	Type: Primary  Bus: USB
	BD Address: A0:9F:10:C0:1E:55  ACL MTU: 1021:6  SCO MTU: 255:12
	UP RUNNING 
	RX bytes:683 acl:0 sco:0 events:43 errors:0
	TX bytes:738 acl:0 sco:0 commands:43 errors:0
	Features: 0xff 0xff 0xff 0xfe 0xdb 0xfd 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'raspberrypi #2'
	Class: 0x480000
	Service Classes: Capturing, Telephony
	Device Class: Miscellaneous, 
	HCI Version:  (0xa)  Revision: 0x99a
	LMP Version:  (0xa)  Subversion: 0x2885
	Manufacturer: Realtek Semiconductor Corporation (93)

---

### Post by esperie on 2021-08-06
I have the same MPOW adaptor (BH519A) with Realtek chipset RTL8761BU. My kernel version is 5.11 on ubuntu 20.04. Exhausted every solution I can find on the internet and only the one posted by @meavydev worked.

To be precise, 
1. Go to the downloaded linux driver folder (20201202_LINUX_BT_DRIVER/usb/bluetooth_usb_driver)
2. edit rtk_misc.c.
3. Look for the code block: static patch_info fw_patch_table[]
4. Add the line: {0x2550, 0x8761, "mp_rtl8761b_fw", "rtl8761bu_fw", "rtl8761b_config", NULL, 0},    /* RTL8761BU only */
5. Save and close the file.
6. Run sudo make install INTERFACE=usb from 20201202_LINUX_BT_DRIVER/usb.
7. hciconfig will now show the device and bluetooth works as intended after that.

> **meavydev said:**
> Ah a quick hack and at least it shows up in hciconfig...
I should say I don't know what the correct settings are, I just guessed.
However I edited rtk_misc.c and added this line to fw_patch_table:
    {0x2550, 0x8761, "mp_rtl8761b_fw", "rtl8761bu_fw", "rtl8761b_config", NULL, 0},    /* RTL8761BU only */

This is what shows up in hciconfig:
pi@raspberrypi:~/20201202_LINUX_BT_DRIVER/usb $ hciconfig -a
hci1:    Type: Primary  Bus: USB
    BD Address: A0:9F:10:C0:1E:55  ACL MTU: 1021:6  SCO MTU: 255:12
    UP RUNNING 
    RX bytes:683 acl:0 sco:0 events:43 errors:0
    TX bytes:738 acl:0 sco:0 commands:43 errors:0
    Features: 0xff 0xff 0xff 0xfe 0xdb 0xfd 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'raspberrypi #2'
    Class: 0x480000
    Service Classes: Capturing, Telephony
    Device Class: Miscellaneous, 
    HCI Version:  (0xa)  Revision: 0x99a
    LMP Version:  (0xa)  Subversion: 0x2885
    Manufacturer: Realtek Semiconductor Corporation (93)

---

### Post by eduardp2 on 2021-08-25
Thank you, that worked for me.

---

