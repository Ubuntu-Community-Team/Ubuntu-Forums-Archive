---
title: "Bluetooth Manager not detecting any bluetooth device suddenly"
date: 2018-05-11
forum: Networking &amp; Wireless
---

### Post by muthuct on 2018-05-11
I am new to Ubuntu forums, so please request any info that I might have missed. I installed Lubuntu 18.04 on HP Pavilion-15-p027tx and everything was working fine. For using my bluetooth boAt Rockerz headset I installed blueman (Bluetooth Manager). I configured it to add new device and it paired and connected with my bluetooth headset. It was working fine. But today I was unable to connect to the headset so I removed it from list of paired devices and tried to pair it again. But of no use. I checked my headset with my android phone, it is working perfectly. Also I checked if lubuntu was recognising any other bluetooth device and it wasn't. I also checked if my bluetooth hardware is working by logging into my windows OS (dual boot) and I was able to connect to my bluetooth headset. So the problem is not with the bluetooth hardware or the headset. I read most of the threads related to this of no use.
Output of "uname -r; lsusb; lspci -nnk | grep -iA2 net; rfkill list all; hciconfig -a; dmesg | egrep -i 'blue|firm' " command
```

4.15.0-20-generic
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
08:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
    Kernel driver in use: wl
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:2281]
    Kernel driver in use: r8169
    Kernel modules: r8169
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
hci0:    Type: Primary  Bus: USB
    BD Address: 38:B1:DB:E9:37:1A  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:2364 acl:0 sco:0 events:151 errors:0
    TX bytes:6357 acl:0 sco:0 commands:151 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'my-linux-workstation'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)

[    0.000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x20 (or later)
[    0.057600] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.456257] [Firmware Bug]: Invalid critical threshold (0)
[    1.784483] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   22.851537] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   23.419902] Bluetooth: Core ver 2.22
[   23.419929] Bluetooth: HCI device and connection manager initialized
[   23.419934] Bluetooth: HCI socket layer initialized
[   23.419937] Bluetooth: L2CAP socket layer initialized
[   23.419945] Bluetooth: SCO socket layer initialized
[   23.537924] Bluetooth: hci0: BCM: chip id 70
[   23.538916] Bluetooth: hci0: BCM: features 0x06
[   23.554935] Bluetooth: hci0: BCM43142A
[   23.554939] Bluetooth: hci0: BCM (001.001.011) build 0000
[   23.586413] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   23.586417] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   25.596095] Bluetooth: hci0: command 0x1003 tx timeout
[   32.365464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.365465] Bluetooth: BNEP filters: protocol multicast
[   32.365470] Bluetooth: BNEP socket layer initialized
[   34.396069] Bluetooth: hci0: command 0x1003 tx timeout
[   77.614800] Bluetooth: RFCOMM TTY layer initialized
[   77.614810] Bluetooth: RFCOMM socket layer initialized
[   77.614821] Bluetooth: RFCOMM ver 1.11
[  689.951386] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  714.782380] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  905.950195] Bluetooth: hci0: command 0x1003 tx timeout
[ 1499.975810] Bluetooth: hci0: last event is not cmd complete (0x0f)

```

---

### Post by jeremy31 on 2018-05-11
```
wget https://www.dropbox.com/s/r6q9zt59darq80n/BCM43142A0-0a5c-216c.hcd
sudo cp BCM43142A0-0a5c-216c.hcd /lib/firmware/brcm/BCM.hcd
```
Reboot and see if that firmware fixes it

---

