---
title: "Blueman Assistand tells &quot;No adapters found&quot;"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by mark183 on 2016-12-19
Hi, 

Lenovo X230 / Ubuntu-MATE 16.04: was trying to fix a bluetooth issue and so far I have only made it worse.

Output from this command (from [https://ubuntuforums.org/showthread.php?t=2346462](https://ubuntuforums.org/showthread.php?t=2346462)):

```
uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

Returns:


```


mark@mark-X230:~$ uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
4.4.0-53-generic
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bdb:1926 Ericsson Business Mobile Networks BV 
Bus 003 Device 004: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 003 Device 005: ID 24ae:1003  
Bus 003 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_wwan_sw: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:302 acl:0 sco:0 events:6 errors:0
    TX bytes:95 acl:0 sco:0 commands:9 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 

[    0.134205] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.177181] pnp 00:01: [Firmware Bug]: PNP resource [mem 0xfed10000-0xfed13fff] covers only part of 0000:00:00.0 Intel MCH; extending to [mem 0xfed10000-0xfed17fff]
[    3.152219] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    3.175426] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.694863] Bluetooth: Core ver 2.21
[    4.694883] Bluetooth: HCI device and connection manager initialized
[    4.694886] Bluetooth: HCI socket layer initialized
[    4.694890] Bluetooth: L2CAP socket layer initialized
[    4.694897] Bluetooth: SCO socket layer initialized
[    4.717797] Bluetooth: hci0: BCM: chip id 63
[    4.733764] Bluetooth: hci0: BCM20702A
[    4.734685] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[    6.188852] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    6.795482] Bluetooth: hci0 command 0x213c tx timeout
[   10.235003] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.235009] Bluetooth: BNEP filters: protocol multicast
[   10.235014] Bluetooth: BNEP socket layer initialized
[   14.791823] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[   16.795841] Bluetooth: hci0 command 0x0c03 tx timeout
[   24.792174] Bluetooth: hci0: BCM: Reset failed (-110)
[   26.920229] Bluetooth: hci0 command 0x0c03 tx timeout
[   34.912519] Bluetooth: hci0: BCM: Reset failed (-110)
mark@mark-X230:~$


```


Any hint?

Thanks & BR
Mark

---

### Post by jeremy31 on 2016-12-19
Do you have a firmware file for the bluetooth?  The file is specific to the chipset and you need the one for ID 0a5c:21e6

---

### Post by mark183 on 2016-12-20
Do you mean this one here?
BCM43142A0-0a5c-21e6.hcd

I installed that following instructions from here: [https://forums.linuxmint.com/viewtopic.php?t=207025](https://forums.linuxmint.com/viewtopic.php?t=207025)
(could it be that JeremyB is also jeremy31?  ;-)

```

wget https://www.dropbox.com/s/p6h7ho21fct2pzb/fw-0a5c_21e6.hcd
sudo cp fw-0a5c_21e6.hcd /lib/firmware/
sudo cp fw-0a5c_21e6.hcd /lib/firmware/brcm/BCM43142A0-0a5c-21e6.hcd
sudo modprobe -r btusb
sudo modprobe btusb

```

---

### Post by jeremy31 on 2016-12-20
I do post over there
You may need to rename the file with the newer kernels
```
sudo cp /lib/firmware/brcm/BCM43142A0-0a5c-21e6.hcd /lib/firmware/brcm/BCM.hcd
```

Then modprobe -r and modprobe btusb or reboot and see if it works

---

### Post by mark183 on 2016-12-22
Done & reboot, but still getting the "No adapters found" pop up. Also, the last bit of this printout seems unchanged:

```

[    0.134198] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.177048] pnp 00:01: [Firmware Bug]: PNP resource [mem 0xfed10000-0xfed13fff] covers only part of 0000:00:00.0 Intel MCH; extending to [mem 0xfed10000-0xfed17fff]
[    3.112381] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[    3.115867] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.889832] Bluetooth: Core ver 2.21
[    4.889853] Bluetooth: HCI device and connection manager initialized
[    4.889857] Bluetooth: HCI socket layer initialized
[    4.889860] Bluetooth: L2CAP socket layer initialized
[    4.889865] Bluetooth: SCO socket layer initialized
[    4.900972] Bluetooth: hci0: BCM: chip id 63
[    4.916956] Bluetooth: hci0: BCM20702A
[    4.917910] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[    6.108639] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    6.979000] Bluetooth: hci0 command 0x213c tx timeout
[   10.007532] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.007536] Bluetooth: BNEP filters: protocol multicast
[   10.007540] Bluetooth: BNEP socket layer initialized
[   14.974784] Bluetooth: hci0: BCM: Patch command 213c failed (-110)
[   16.978756] Bluetooth: hci0 command 0x0c03 tx timeout
[   24.974512] Bluetooth: hci0: BCM: Reset failed (-110)
[   27.098417] Bluetooth: hci0 command 0x0c03 tx timeout
[   35.094208] Bluetooth: hci0: BCM: Reset failed (-110)
mark@mark-X230:~$ 


```


Running this:
```
hciconfig hci0 up
```

returns "Can't init device hci0: Connection timed out (110)"

---

### Post by jeremy31 on 2016-12-22
You could try converting firmware yourself using Pilot6's guide [here](http://askubuntu.com/a/632348/300665)
Just search the windows inf file for 21e6

---

### Post by mark183 on 2016-12-25
With some more searching I found a way to make it work again (though I don't exactly understand why ...):

From [https://bugzilla.kernel.org/show_bug.cgi?id=81821](https://bugzilla.kernel.org/show_bug.cgi?id=81821) I learned exactly which origin firmware my X230 needs: BCM20702A1_001.002.014.0449.0462.hex

This is contained in the ThinkPad Bluetooth with Enhanced Data Rate Software for Windows 7 (32-bit, 64-bit), downloaded from Lenovo:
[https://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/g4wb12ww.exe](https://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/g4wb12ww.exe)

Based on instructions from here: [http://hillenius.com/blog/2016/06/direct-loading-firmware-bcm20702a1-0a5c-21e6hcd/index.html](http://hillenius.com/blog/2016/06/direct-loading-firmware-bcm20702a1-0a5c-21e6hcd/index.html) :

```
[FONT=&quot]mark@mark-X230:~$ [COLOR=#800080]innoextract g4wb12ww.exe[/COLOR][/FONT]
```

This creates app/Win64, containing among many others: BCM20702A1_001.002.014.0449.0462.hex, which I copied to the Desktop.

Then:

```

mark@mark-X230:~$ hex2hcd Desktop/BCM20702A1_001.002.014.0449.0462.hex
mark@mark-X230:~$ cp Desktop/BCM20702A1_001.002.014.0449.0462.hcd /lib/firmware/brcm/BCM20702A1-0a5c-21e6.hcd

```

Reboot, and Bluetooth is back again.

This command:

```
uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
```

Now returns:

```
mark@mark-X230:~$ name -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm'
No command 'name' found, did you mean:
 Command 'lame' from package 'lame' (universe)
 Command 'mame' from package 'mame' (multiverse)
 Command 'nama' from package 'nama' (universe)
 Command 'named' from package 'bind9' (main)
 Command 'uname' from package 'coreutils' (main)
 Command 'namei' from package 'util-linux' (main)
 Command 'nvme' from package 'nvme-cli' (universe)
 Command 'nam' from package 'nam' (universe)
name: command not found
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 5986:02d2 Acer, Inc 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bdb:1926 Ericsson Business Mobile Networks BV 
Bus 003 Device 004: ID 046d:c069 Logitech, Inc. M-U0007 [Corded Mouse M500]
Bus 003 Device 005: ID 24ae:1003  
Bus 003 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_wwan_sw: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
hci0:    Type: BR/EDR  Bus: USB
    BD Address: F8:2F:A8:EB:47:F6  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING 
    RX bytes:2421 acl:0 sco:0 events:207 errors:0
    TX bytes:33395 acl:0 sco:0 commands:206 errors:0
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'mark-X230'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x11ce
    LMP Version: 4.0 (0x6)  Subversion: 0x220e
    Manufacturer: Broadcom Corporation (15)

[    0.134114] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.177013] pnp 00:01: [Firmware Bug]: PNP resource [mem 0xfed10000-0xfed13fff] covers only part of 0000:00:00.0 Intel MCH; extending to [mem 0xfed10000-0xfed17fff]
[    3.137800] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    3.197567] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    4.695401] Bluetooth: Core ver 2.21
[    4.695421] Bluetooth: HCI device and connection manager initialized
[    4.695426] Bluetooth: HCI socket layer initialized
[    4.695428] Bluetooth: L2CAP socket layer initialized
[    4.695433] Bluetooth: SCO socket layer initialized
[    4.707460] Bluetooth: hci0: BCM: chip id 63
[    4.723444] Bluetooth: hci0: BCM20702A
[    4.724395] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[    5.383565] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0462
[    5.400494] Bluetooth: hci0: Broadcom Bluetooth Device
[    5.703801] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.703803] Bluetooth: BNEP filters: protocol multicast
[    5.703806] Bluetooth: BNEP socket layer initialized
[    6.150959] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   10.063470] Bluetooth: RFCOMM TTY layer initialized
[   10.063481] Bluetooth: RFCOMM socket layer initialized
[   10.063486] Bluetooth: RFCOMM ver 1.11
mark@mark-X230:~$ 

```

---

### Post by jeremy31 on 2016-12-25
What you did is just a little different than what Pilot6 posted but it works

---

