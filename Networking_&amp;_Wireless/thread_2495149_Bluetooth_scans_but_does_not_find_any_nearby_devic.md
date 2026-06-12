---
title: "Bluetooth scans but does not find any nearby devices. Other symptoms."
date: 2024-02-08
forum: Networking &amp; Wireless
---

### Post by hunterakins on 2024-02-08
I recently had my motherboard replaced in a Dell 5550 Precision laptop with Ubuntu 22.04, which fixed issues I had with the power adapter not being detected/ computer randomly shutting down. 
Shortly after the replacement I did a firmware update, which I do not know how to view the details of (for example, in which log to find the details). 

After these two events, my Bluetooth scans endlessly without every finding devices. 

Running rfkill
~&#10095; rfkill
ID TYPE      DEVICE      SOFT      HARD
 0 bluetooth hci0   unblocked unblocked
 1 wlan      phy0   unblocked unblocked


Bluetoothctl outputs:
"
Agent registered
[CHG] Controller C0:3C:59:E9:17:12 Pairable: yes
[bluetooth]# scan on
Discovery started
"

No devices ever show up here
"
[bluetooth]# show 
Controller C0:3C:59:E9:17:12 (public)
    Name: hunter-Precision-5550
    Alias: hunter-Precision-5550
    Class: 0x007c010c
    Powered: yes
    Discoverable: yes
    DiscoverableTimeout: 0x0000003c
    Pairable: yes
    UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
    UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree Audio Gateway   (0000111f-0000-1000-8000-00805f9b34fb)
    UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
    UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0540
    Discovering: yes
    Roles: central
    Roles: peripheral
Advertising Features:
    ActiveInstances: 0x00 (0)
    SupportedInstances: 0x0c (12)
    SupportedIncludes: tx-power
    SupportedIncludes: appearance
    SupportedIncludes: local-name
    SupportedSecondaryChannels: 1M
    SupportedSecondaryChannels: 2M
"

I looked in BIOS and it seemed like everything is fine (Bluetooth is enabled). 

Not sure what exactly is going wrong here. 

I am also having some strange WiFi behavior. I have no problem connecting to my home network. However, my work wifi using WPA enterprise. I am unable to fix the settings of the Wi-Fi network. It just keeps asking me to supply a username and password as though its simple WPA (not enterprise). I have an Ethernet connection that I use through my Thunderbolt dock. Occasionally that also is not working, showing a question mark next to the Ethernet symbol. 

I think most likely this is related to the firmware update, but it could definitely be related to the motherboard replacement. 

Any help or ideas to try here would be greatly appreciated.

---

### Post by jeremy31 on 2024-02-08
Post results from terminal for ```
lsusb; sudo dmesg | egrep -i 'blue|firm'
```

---

### Post by hunterakins on 2024-02-08
~> lsusb; sudo dmesg | egrep -i 'blue|firm' 
Bus 006 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 006 Device 003: ID 0bda:0413 Realtek Semiconductor Corp. Dell dock
Bus 006 Device 002: ID 0bda:0487 Realtek Semiconductor Corp. Dell dock
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 413c:b06e Dell Computer Corp. Dell dock
Bus 005 Device 009: ID 413c:b06f Dell Computer Corp. Dell dock
Bus 005 Device 008: ID 0bda:402e Realtek Semiconductor Corp. USB Audio
Bus 005 Device 007: ID 1908:1320 GEMBIRD DM8261 Flashdisc
Bus 005 Device 006: ID 046d:c548 Logitech, Inc. USB Receiver
Bus 005 Device 005: ID 30fa:0300  USB OPTICAL MOUSE 
Bus 005 Device 003: ID 0bda:5413 Realtek Semiconductor Corp. Dell dock
Bus 005 Device 002: ID 0bda:5487 Realtek Semiconductor Corp. Dell dock
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 001 Device 003: ID 0bda:5510 Realtek Semiconductor Corp. Integrated_Webcam_HD
Bus 001 Device 002: ID 27c6:533c Shenzhen Goodix Technology Co.,Ltd. FingerPrint
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by hunterakins on 2024-02-08
You can see above that earlier, dmesg returned nothing matching blue | firm. 
Since then, my internet completely stopped working. I could not connect to ethernet nor wifi. 
I restarted the computer. I still had the same issues. 
After ten minutes or so, the internet randomly started working. 

Now, after the restart, dmesg has some messages about bluetooth

sudo dmesg | egrep -i 'blue|firm'


[    2.665971] Bluetooth: Core ver 2.22
[    2.670644] NET: Registered PF_BLUETOOTH protocol family
[    2.670646] Bluetooth: HCI device and connection manager initialized
[    2.670650] Bluetooth: HCI socket layer initialized
[    2.670652] Bluetooth: L2CAP socket layer initialized
[    2.670657] Bluetooth: SCO socket layer initialized
[    2.695085] iwlwifi 0000:00:14.3: loaded firmware version 77.2df8986f.0 QuZ-a0-hr-b0-77.ucode op_mode iwlmvm
[    2.891353] Bluetooth: hci0: Found device firmware: intel/ibt-19-0-4.sfi
[    2.891387] Bluetooth: hci0: Boot Address: 0x24800
[    2.891388] Bluetooth: hci0: Firmware Version: 206-22.23
[    2.891390] Bluetooth: hci0: Firmware already loaded
[    2.895443] Bluetooth: hci0: HCI LE Coded PHY feature bit is set, but its usage is not supported.
[    3.550478] i915 0000:00:02.0: [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    3.754474] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.754485] Bluetooth: BNEP filters: protocol multicast
[    3.754496] Bluetooth: BNEP socket layer initialized
[    3.762772] Bluetooth: MGMT ver 1.22
[    3.795503] nouveau 0000:01:00.0: pmu: firmware unavailable
[   38.133453] Bluetooth: RFCOMM TTY layer initialized
[   38.133476] Bluetooth: RFCOMM socket layer initialized
[   38.133486] Bluetooth: RFCOMM ver 1.11

---

### Post by hunterakins on 2024-02-09
Another update:
I booted to Ubuntu 18.04 from a USB. I have the same bluetooth issue in Ubuntu 18.04.

---

### Post by SeijiSensei on 2024-02-09
I've turned off Bluetooth and networking on my Dell laptop by accidentally hitting the wrong Fn-key combination. According to this, for a Precision, it looks like it's Fn+F2. [https://smallbusiness.chron.com/activate-bluetooth-dell-laptop-55852.html](https://smallbusiness.chron.com/activate-bluetooth-dell-laptop-55852.html)

---

