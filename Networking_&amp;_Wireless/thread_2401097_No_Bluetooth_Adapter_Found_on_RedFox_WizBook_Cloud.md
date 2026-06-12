---
title: "No Bluetooth Adapter Found on RedFox WizBook Cloud"
date: 2018-09-13
forum: Networking &amp; Wireless
---

### Post by thenflux on 2018-09-13
Recently, my wifi was fixed. Now I'm looking to fix the bluetooth now. Any ideas?

lsusb shows
```
paolo@paolo-WB-Z8140:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 011: ID 1018:1006  
Bus 001 Device 005: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 1ea7:0064  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg | grep -i blue shows
```
paolo@paolo-WB-Z8140:~$ dmesg | grep -i blue

```

Strangely, nothing comes out when entering such line.

rfkill list all shows
```
paolo@paolo-WB-Z8140:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2018-09-13
The 1018:1006 is evidently the touchpad: [https://askubuntu.com/questions/876656/hid-touchpad-not-working-but-detected/876658](https://askubuntu.com/questions/876656/hid-touchpad-not-working-but-detected/876658)

The 058f:5608 is evidenlty the camera: [https://lists.debian.org/debian-user/2017/11/msg00065.html](https://lists.debian.org/debian-user/2017/11/msg00065.html)

The 1ea7:0064  is evidently a wireless mouse: [https://linux-hardware.org/index.php?id=usb:1ea7-0064](https://linux-hardware.org/index.php?id=usb:1ea7-0064)

Unfortunately, we see no sign whatever of any bluetooth device. Unless there is some option in the BIOS to enable/disable bluetooth, I am afraid there is no device present at all.

---

### Post by jeremy31 on 2018-09-13
Post results for ```
dmesg | egrep -i 'blue|firm|sdio'
```

---

### Post by praseodym on 2018-09-13
Maybe its a wireless device with integrated BT?!
```

lspci -nnk
```please

---

### Post by chili555 on 2018-09-13
Man, oh man!!! You have two of the three best gurus in the business helping you right here.

---

### Post by jeremy31 on 2018-09-13
thenflux post on the wireless issue [https://ubuntuforums.org/showthread.php?t=2399217](https://ubuntuforums.org/showthread.php?t=2399217) and previous wifi script results- [http://paste.ubuntu.com/p/tKrGmn43vH/](http://paste.ubuntu.com/p/tKrGmn43vH/)

---

### Post by thenflux on 2018-09-13
dmesg | egrep -i 'blue|firm|sdio'
```
paolo@paolo-WB-Z8140:~$ dmesg | egrep -i 'blue|firm|sdio'

[    0.237470] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    3.258061] mmc1: new high speed SDIO card at address 0001
[    6.100297] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43430a0-sdio.bin for chip 0x00a9a6(43430) rev 0x000000
[    6.205348] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430a0-sdio.clm_blob failed with error -2
[    6.206004] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: May 29 2017 00:03:43 version 7.13.53.9 (r664949) FWID 01-130000

```

 lspci -nnk
```

paolo@paolo-WB-Z8140:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register [8086:2280] (rev 22)
	Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register [8086:7270]
	Kernel driver in use: iosf_mbi_pci
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers [8086:22b0] (rev 22)
	Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers [8086:7270]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Multimedia controller [0480]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit [8086:22b8] (rev 22)
	Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit [8086:7270]
00:0b.0 Signal processing controller [1180]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller [8086:22dc] (rev 22)
	Subsystem: Device [7270:8086]
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller [8086:22b5] (rev 22)
	Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller [8086:7270]
	Kernel driver in use: xhci_hcd
00:1a.0 Encryption controller [1080]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine [8086:2298] (rev 22)
	Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine [8086:7270]
	Kernel driver in use: mei_txe
	Kernel modules: mei_txe
00:1f.0 ISA bridge [0601]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU [8086:229c] (rev 22)
	Subsystem: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU [8086:7270]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich

```

---

### Post by praseodym on 2018-09-14
> ```
[    6.023093] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430a0-sdio.txt failed with error -2
```

[https://github.com/armbian/firmware/blob/master/brcm/brcmfmac43430a0-sdio.txt](https://github.com/armbian/firmware/blob/master/brcm/brcmfmac43430a0-sdio.txt)

Lets try
```

cd /lib/firmware/brcm/
sudo apt-get install git
sudo git clone https://github.com/armbian/firmware/blob/master/brcm/brcmfmac43430a0-sdio.txt
```
Reboot and check

```
dmesg | grep brcm
```

---

### Post by thenflux on 2018-09-14
> **praseodym said:**
> [https://github.com/armbian/firmware/blob/master/brcm/brcmfmac43430a0-sdio.txt](https://github.com/armbian/firmware/blob/master/brcm/brcmfmac43430a0-sdio.txt)

Lets try
```

cd /lib/firmware/brcm/
sudo apt-get install git
sudo git clone https://github.com/armbian/firmware/blob/master/brcm/brcmfmac43430a0-sdio.txt
```
Reboot and check

```
dmesg | grep brcm
```

Here it goes
```
paolo@paolo-WB-Z8140:~$ dmesg | grep brcm
[    6.259776] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43430a0-sdio.bin for chip 0x00a9a6(43430) rev 0x000000
[    6.259922] usbcore: registered new interface driver brcmfmac
[    6.372375] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430a0-sdio.clm_blob failed with error -2
[    6.372383] brcmfmac: brcmf_c_process_clm_blob: no clm_blob available(err=-2), device may have limited channels available
[    6.373013] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: May 29 2017 00:03:43 version 7.13.53.9 (r664949) FWID 01-130000
paolo@paolo-WB-Z8140:~$ 



```

Checking on the icons at the bottom right, it still says "No Bluetooth Adapter Found"

---

