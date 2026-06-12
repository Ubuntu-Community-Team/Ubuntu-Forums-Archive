---
title: "Intel Wireless-N 7260HMWBN Bluetooth driver under 14.04"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by tubos2 on 2014-06-11
- I've installed 14.04 LTS and ubuntu recognized the card's wifi module
but not the bluetooth module.

- What are the steps to manually add a driver to enable BT as well?

---

### Post by kjetil-fleten on 2014-06-12
I have the same problem, and I believe it is related to the firmware. Try to run "sudo  lshw -C network", to check your current version. My firmware showed up to be 22.1.7.0 using 14.04, while latest firmware is 23.214.9.0 ([http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware)). The only problem now, is that I need to apply this patch [https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=431031851ea72a25abb9ad4df56a0f3b997e3026](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=431031851ea72a25abb9ad4df56a0f3b997e3026) to the newest firmware before I can apply it. I have not been successful with that yet...

---

### Post by tubos2 on 2014-06-13
Can someone help ?

---

### Post by jeremy31 on 2014-06-13
It appears that the patch is applied in the 3.15 kernel, upgrading the kernel might be easier than applying the patch.  One important question, did the computer have that card in it as OEM?  I was only able to get one of those to work in 1 of 3 laptops that I have.  One hard blocked the card, the other wouldn't boot because of the whitelist, and the third was easy- just plug and play.  There are only 3 extra modules loaded from what I remember and they are btusb, toshiba_bluetooth, and bluetooth.  Have you checked to see if bluetooth is hard blocked or anything in dmesg?

---

### Post by tubos2 on 2014-06-14
no , the card is an pcie mini card , i bought and installed in an intel nuc D34010WYK PC.

The wifi worked out of the box , but i'd like to enable the bluetooth module as well.

---

### Post by jeremy31 on 2014-06-14
```
lsusb
``````
iwlwifi | grep firmware
```

Mine has working bluetooth using firmware iwlwifi-7260-7

---

### Post by tubos2 on 2014-06-14
how do i install iwlwifi driver ?

below I have some lines from my dmesg

> 3.418148] iwlwifi 0000:02:00.0: irq 62 for MSI/MSI-X[    3.557904] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    3.595380] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[    3.596409] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    3.596668] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    4.578476] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    4.578698] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
dirk@dirk-nuc:/lib/firmware$ dmesg | grep tooth
[    4.176266] Bluetooth: Core ver 2.17
[    4.176300] Bluetooth: HCI device and connection manager initialized
[    4.176309] Bluetooth: HCI socket layer initialized
[    4.176314] Bluetooth: L2CAP socket layer initialized
[    4.176320] Bluetooth: SCO socket layer initialized
[    4.191194] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.191199] Bluetooth: BNEP filters: protocol multicast
[    4.191210] Bluetooth: BNEP socket layer initialized
[    4.205693] Bluetooth: RFCOMM TTY layer initialized
[    4.205707] Bluetooth: RFCOMM socket layer initialized
[    4.205715] Bluetooth: RFCOMM ver 1.11




---

### Post by tubos2 on 2014-06-14
And some more info , below in the hope someone can help
me get this bluetooth to work:

> *-network       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 4b
       serial: 00:15:00:bc:28:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.24.8.0 ip=192.168.2.143 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:62 memory:f7c00000-f7c01fff




---

### Post by jeremy31 on 2014-06-14
```
[   16.709992] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler[   16.710034] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   17.055578] Bluetooth: Core ver 2.17
[   17.055597] Bluetooth: HCI device and connection manager initialized
[   17.055604] Bluetooth: HCI socket layer initialized
[   17.055607] Bluetooth: L2CAP socket layer initialized
[   17.055648] Bluetooth: SCO socket layer initialized
[   17.173814] Bluetooth: hci0: read Intel version: 370710018002030d00
[   17.219181] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   17.377965] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   18.215312] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.215316] Bluetooth: BNEP filters: protocol multicast
[   18.215323] Bluetooth: BNEP socket layer initialized
[   18.216294] Bluetooth: RFCOMM TTY layer initialized
[   18.216303] Bluetooth: RFCOMM socket layer initialized
[   18.216308] Bluetooth: RFCOMM ver 1.11
[ 1990.672248] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[ 1993.154444] Bluetooth: hci0: read Intel version: 370710018002030d00
[ 1993.154448] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 1993.313650] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
```

The only thing different is that I have toshiba_bluetooth detecting the device.  I wonder what is on your PC that is supposed to do that?  Could try ```
ls /sys/module | grep bluetooth
```
Does it even register in ```
lsusb
```??
Mine shows this ```
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
```

What was your old wifi device?  Are it's driver modules still loaded?  ```
lsmod
```

---

### Post by tubos2 on 2014-06-14
>  
$ ls /sys/module | grep bluetooth
bluetooth


> lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 


> lsmod
bluetooth             395423  10 bnep,rfcomm

This is a new hw configuration no old wifi c

---

### Post by kjetil-fleten on 2014-06-14
I found another thread that describes the problem here: [http://askubuntu.com/questions/450348/bluetooth-not-working-in-ubuntu-14-04](http://askubuntu.com/questions/450348/bluetooth-not-working-in-ubuntu-14-04) 

It seems like the problem there was because of an issue with missing firmware. This was revealed by dmesg | grep -i blue, and resolved by
sudo apt-get install linux-firmware.
I have not tried my selves yet, but it could do the trick.

---

### Post by tubos2 on 2014-06-14
I tried it but it seems they were already installed
and I have no errors in my dmesg output like that thread.

> sudo apt-get install linux-firmware

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
linux-firmware set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




---

### Post by jeremy31 on 2014-06-14
> **tubos2 said:**
> I tried it but it seems they were already installed
and I have no errors in my dmesg output like that thread.

You definitely have a unique situation.  have you checked dmesg for other intel hardware ```
dmesg | grep 8086
```

You PC might need special drivers made and I imagine you already have the BIOS update from 6 months ago.  I would ask here as well [https://communities.intel.com/community/tech/nuc/content](https://communities.intel.com/community/tech/nuc/content) as intel tries to be linux friendly

---

### Post by tubos2 on 2014-06-14
I already updated to the latest bios firmware for my nuc

> dmesg | grep 8086

[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.179550] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.179668] pci 0000:00:02.0: [8086:0a16] type 00 class 0x030000
[    0.179811] pci 0000:00:03.0: [8086:0a0c] type 00 class 0x040300
[    0.179960] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.180140] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    0.180336] pci 0000:00:19.0: [8086:1559] type 00 class 0x020000
[    0.180535] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.180714] pci 0000:00:1c.0: [8086:9c10] type 01 class 0x060400
[    0.180878] pci 0000:00:1c.3: [8086:9c16] type 01 class 0x060400
[    0.181051] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    0.181282] pci 0000:00:1f.0: [8086:9c43] type 00 class 0x060100
[    0.181483] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    0.181662] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.181968] pci 0000:02:00.0: [8086:08b1] type 00 class 0x028000




---

### Post by kjetil-fleten on 2014-06-16
Now that we know linux-firmware is installed, I'm curious to know if it really supply the latest firmware for that device, like we think it does ? Does "sudo lshw -C network" show up with firmware 23.214.9.0, or a previous version ?

---

### Post by derry2 on 2014-06-25
> **kjetil-fleten said:**
> Now that we know linux-firmware is installed, I'm curious to know if it really supply the latest firmware for that device, like we think it does ? Does "sudo lshw -C network" show up with firmware 23.214.9.0, or a previous version ?

I seem to have the same issue with my NUC D34010WYK and an Intel Dual Band Wireless-N 7260 PCIe Mini. Wireless works fine, but the Bluetooth isn't working at all.

I am running Kernel 3.14.1-031401-generic but the firmware for the iwlwifi is 22.24.8.0 

As stated, the wireless works fine, but I bought this module for my NUC so I could get some Bluetooth peripherals connected...

---

### Post by jeremy31 on 2014-06-25
There is another firmware that needs to be loaded for bluetooth to work from my dmesg ```
[COLOR=#000000][FONT=Ubuntu Mono][ 1993.154448] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq[/FONT][/COLOR][ 1993.313650] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
```

I am not sure if this can be forced in some way

---

