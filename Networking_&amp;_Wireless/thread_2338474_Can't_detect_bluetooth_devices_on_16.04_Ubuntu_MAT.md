---
title: "Can't detect bluetooth devices on 16.04 Ubuntu MATE"
date: 2016-09-28
forum: Networking &amp; Wireless
---

### Post by ian49 on 2016-09-28
I recently installed Ubuntu MATE 16.04 on a Lenovo G70 laptop.  Everything appears to be working fine as far as I can determine apart from bluetooth.

I have the bluetooth icon on the top panel and it appears to suggest that bluetooth is on. However when I select "Setup new device..." it never finds anything. I've not actually used bluetooth before so there may be something obvious I'm missing. Any help or constructive suggestions would be very welcome.

---

### Post by jeremy31 on 2016-09-29
Please post results for ```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

---

### Post by ian49 on 2016-09-29
Here they are:

```
lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3819]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
    Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: A0:D3:7A:5C:4F:7B  ACL MTU: 1021:5  SCO MTU: 96:6
    UP RUNNING 
    RX bytes:1978 acl:0 sco:0 events:123 errors:0
    TX bytes:1881 acl:0 sco:0 commands:120 errors:0
    Features: 0xff 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'ian-Lenovo-G70-80'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0xf00
    LMP Version: 4.0 (0x6)  Subversion: 0xf00
    Manufacturer: Intel Corp. (2)

[    0.158835] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.691518] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x594f03)
[    8.171734] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
[    8.213245] Bluetooth: Core ver 2.21
[    8.213266] Bluetooth: HCI device and connection manager initialized
[    8.213271] Bluetooth: HCI socket layer initialized
[    8.213275] Bluetooth: L2CAP socket layer initialized
[    8.213289] Bluetooth: SCO socket layer initialized
[    8.424248] iwlwifi 0000:03:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    8.593773] Bluetooth: hci0: read Intel version: 3707100100012d0d25
[    8.593776] Bluetooth: hci0: Intel device is already patched. patch num: 25
[   15.406546] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.406550] Bluetooth: BNEP filters: protocol multicast
[   15.406555] Bluetooth: BNEP socket layer initialized
[   31.900918] Bluetooth: RFCOMM TTY layer initialized
[   31.900927] Bluetooth: RFCOMM socket layer initialized
[   31.900933] Bluetooth: RFCOMM ver 1.11
```

---

### Post by jeremy31 on 2016-09-29
I don't see anything wrong in the output, we use code tags for terminal commands and terminal output as it preserves the format and prevents smilies- see link in my signature.

Since you admit to never using bluetooth before, what bluetooth device do you want to connect to?  If you have a bluetooth mouse, keyboard, or headphones you will need to look at the devices operation manual to find out how to put it in discoverable or pairing mode.  If you have another computer, tablet or smartphone, either the Ubuntu computer or the other device needs to be visible(discoverable) and then you can find it while scanning for devices.  I don't use the MATE desktop but the bluetooth setting dialog should allow you to make your Ubuntu bluetooth visible and there is likely a button to add new devices.  Making your Ubuntu machine visible and scan can also be done in terminal
```
bluetoothctl
``` This gives bluetooth control through terminal and will list the MAC address of the computers bluetooth device [controller] along with its bluetooth name and may list devices and their MAC addresses that have been paired with
```
scan on
``` To enable scanning any visible/discoverable device should be found
```
discoverable on
``` Makes the computer discoverable by other devices

If you find the device you want to pair with after turning scan on then
```
pair
``` then enter the first 2 digits of the MAC address(case sensitive) and press TAB to autocomplete the MAC address entry, press enter and do the same for the ```
trust
``` command and then use connect command to finish, then use CTRL + d to quit bluetoothctl.

If MATE uses gnome-bluetooth the bluetooth manager might look like [http://zdnet3.cbsistatic.com/hub/i/r/2016/02/24/25ab5140-af7e-41b1-9cb4-a5d3ca331fd4/resize/270xauto/c3b1ac390df01fc417afe73dd641c1b8/bluetooth.png](http://zdnet3.cbsistatic.com/hub/i/r/2016/02/24/25ab5140-af7e-41b1-9cb4-a5d3ca331fd4/resize/270xauto/c3b1ac390df01fc417afe73dd641c1b8/bluetooth.png) and you can make the computer visible with the slider and use the + under the device window to scan, if a device is found click on it and it should give you pairing options

---

### Post by ian49 on 2016-09-29
Thanks for getting back to me.

I've done a little further research since my last post.  The device I'm trying to connect to is a small portable bluetooth speaker, an X-mini Kai. Both my android phones are able to pair with it without any problem. I just tried switching one of my android phones into discoverable mode and my Ubuntu laptop was able to detect it (I didn't actually try to pair with it) So, the problem seems to be between my Ubuntu laptop and the x-mini speaker. At the moment, I can't think why the speaker would work with both phones but not the laptop.

---

### Post by jeremy31 on 2016-09-29
Does this mini speaker have a discoverable mode?  I have a little speaker that all I can do is turn it on and if it doesn't find anything that it was previously paired with then it beeps and I can find it with my computer and after looking at your speakers product support page it may have a similar function, see if turning the bluetooth off on any device it was previously paired with helps

---

### Post by ian49 on 2016-09-29
The speaker has 3 options: off, connected via a jack and bluetooth mode. I've tried switching bluetooth off and on for the devices it was previously connected with several times but it's still not detected by the laptop.

I also just tried once again to detect the android phone and this time, despite repeated attempts, the laptop isn't finding anything.

Just out of interest I switched the laptop into discoverable mode and both phones were able to detect the laptop.

All of which leaves me basically clueless :-(

I think the inbuilt bluetooth functionality in Ubuntu MATE is provided by blueman, perhaps I should look for an alternative?

---

### Post by jeremy31 on 2016-09-29
With one of the Android phones being discoverable do
```
bluetoothctl
```
```
scan on
```
See if the Android phone shows up

I haven't had any issues with Blueman lately but Blueberry is another story

---

### Post by ian49 on 2016-09-29
Tried this separately with both phones, neither was detected.

---

### Post by jeremy31 on 2016-09-29
Shutdown and restart the computer, then try again.  Were the phones previously paired with the computer?  If they were the pairing might need to be deleted on both devices

---

### Post by ian49 on 2016-09-29
> **jeremy31 said:**
> Shutdown and restart the computer, then try again.  Were the phones previously paired with the computer?  If they were the pairing might need to be deleted on both devices

Will do that in just a moment. Just out of interest could this have anything to do with the issue, I read somewhere that there were known issues with bluetooth and 16.04:

```
sudo service bluetooth status

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2016-09-28 20:47:39 BST; 49min ago
     Docs: man:bluetoothd(8)
 Main PID: 758 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;758 /usr/lib/bluetooth/bluetoothd

Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: **Not enough free handles to register service**
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: **Not enough free handles to register service**
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: Current Time Service could not be registered
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: gatt-time-server: Input/output error (5)
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: **Not enough free handles to register service**
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: **Not enough free handles to register service**
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: Sap driver initialization failed.
Sep 28 20:47:41 ian-Lenovo-G70-80 bluetoothd[758]: sap-server: Operation not permitted (1)
Sep 28 20:47:57 ian-Lenovo-G70-80 bluetoothd[758]: Endpoint registered: sender=:1.51 path=/MediaEndpoint/A2DPSource
Sep 28 20:47:57 ian-Lenovo-G70-80 bluetoothd[758]: Endpoint registered: sender=:1.51 path=/MediaEndpoint/A2DPSink
```

---

### Post by ian49 on 2016-09-29
OK, well I think things might be working now although with a couple of caveats.

Having restarted the laptop it took about 4 or 5 attempts before the device (X-MINI KAI) finally showed up. On right-mouse clicking the device from within the devices list it showed 3 descriptions: headset, handsfree and audio sink. I'm not sure whether this is just passive information that's being provided or whether it expects you to select one of them.

Anyway, I paired with the X-Mini speaker but was unable to hear any sound. I then checked the sound settings to make sure I'd selected X-Mini as the output device which I had. It was identified as 'headset'. I then checked the Hardware tab and noticed there were 2 options for the X-Mini: Headset Head unit and High fidelity playback (A2DP Sink). The former had been selected as default but when I tried a sound test there was just white noise. I then switched to the sink option which incorrectly identified the speaker as being stereo but the speaker test worked fine although obviously the left and right speaker test options both played through the same speaker. Finally, I went back and played a song using Audacious and it appeared to play OK. So, hopefully, it'll be OK from now on. I'm not sure why it's all been so inconsistent and seemingly flaky but I'd like to thank you for all your input along the way.

---

### Post by rmorales on 2017-02-19
Thank you so much jeremy31. You solved my problem: Elementary OS Loki (Ubuntu 16.04) not finding my Logitech BT Adapter. The command line tool worked great.

Regards,
Rafael

---

### Post by quackk on 2018-01-23
Please check mine, currently fail to detect my razer mouse.
lost the usb pair for the mouse..

bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Rab 2018-01-24 01:27:07 +08; 4min 32s ago
     Docs: man:bluetoothd(8)
 Main PID: 9317 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;9317 /usr/lib/bluetooth/bluetoothd

Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Current Time Service could not be registered
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: gatt-time-server: Input/output error (5)
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Not enough free handles to register service
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Not enough free handles to register service
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Sap driver initialization failed.
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: sap-server: Operation not permitted (1)
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSource
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSink
Jan 24 01:27:07 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Failed to set mode: Blocked through rfkill (0x12)
Jan 24 01:27:30 mawi-ThinkPad-X1-Carbon bluetoothd[9317]: Failed to set mode: Blocked through rfkill (0x12)
~
~
~

---

### Post by no-name1 on 2018-03-09
thank you, these commands really helpd.

---

### Post by wildmanne39 on 2018-03-09
Old thread back to sleep!

---

