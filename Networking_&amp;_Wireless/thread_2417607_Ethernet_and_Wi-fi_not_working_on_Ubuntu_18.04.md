---
title: "Ethernet and Wi-fi not working on Ubuntu 18.04"
date: 2019-04-25
forum: Networking &amp; Wireless
---

### Post by andrei113113113 on 2019-04-25
[COLOR=#242729][FONT=Arial]My new laptop arrived yesterday, after installing ubuntu i found out that the ethernet and wi-fi are not working. I searched for a solution but nothing seems to work. I don't know why but i think there is a problem with HP laptops, I'm new in the world of linux so I'll be glad if you could help me. The output of some commands that may help: 
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]rfkill list all[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Consolas]enter co0: hci0: Bluetooth[/FONT][/COLOR]
Soft blocked: no [COLOR=#242729][FONT=Consolas]Hard blocked: node  [/FONT][/COLOR]
```
[COLOR=#242729][FONT=Arial]lspci -nnk | grep -iA3 net[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Consolas]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821][/FONT][/COLOR]
Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84be]
    Kernel driver in use: r8169
    Kernel modules: r8169
```
[COLOR=#242729][FONT=Arial]lshw -C network[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Consolas] *-network UNCLAIMED       [/FONT][/COLOR]
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:b1100000-b110ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eno1
       version: 15
       serial: e4:e7:49:3e:3d:a7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s [COLOR=#242729][FONT=Consolas]       resources: irq:17 ioport:3000(size=256) memory:b1004000-b1004fff memory:b1000000-b1003fff[/FONT][/COLOR]
```

---

### Post by VMC on 2019-04-25
from terminal, what does this show: ```
dmesg|grep wifi
```

---

### Post by praseodym on 2019-04-25
[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb)

Install this file by double-click and run

```
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Does LAN work now? Please show also
```

lspci -nnk
```

---

### Post by andrei113113113 on 2019-04-25
> **VMC said:**
> from terminal, what does this show: ```
dmesg|grep wifi
```

Nothing

---

### Post by andrei113113113 on 2019-04-25
**I don't have acces to the internet how can i download the driver ?**
this is the output : 
```
00:00.0 Host bridge[0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor HostBridge/DRAM Registers [8086:5914] (rev 08)
    Subsystem:Hewlett-Packard Company Xeon E3-1200 v6/7th Gen Core Processor HostBridge/DRAM Registers [103c:84be]
00:02.0 VGAcompatible controller [0300]: Intel Corporation UHD Graphics 620[8086:5917] (rev 07)
    Subsystem:Hewlett-Packard Company UHD Graphics 620 [103c:84be]
    Kernel driver inuse: i915
    Kernel modules:i915
00:04.0 Signalprocessing controller [1180]: Intel Corporation Skylake ProcessorThermal Subsystem [8086:1903] (rev 08)
    Subsystem:Hewlett-Packard Company Xeon E3-1200 v5/E3-1500 v5/6th Gen CoreProcessor Thermal Subsystem [103c:84be]
    Kernel driver inuse: proc_thermal
    Kernel modulesProcessor_thermal_device
00:14.0 USBcontroller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCIController [8086:9d2f] (rev 21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP USB 3.0 xHCI Controller[103c:84be]
    Kernel driver inuse: xhci_hcd
00:14.2 Signalprocessing controller [1180]: Intel Corporation Sunrise Point-LPThermal subsystem [8086:9d31] (rev 21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP Thermal subsystem[103c:84be]
    Kernel driver inuse: intel_pch_thermal
    Kernel modules:intel_pch_thermal
00:16.0Communication controller [0780]: Intel Corporation Sunrise Point-LPCSME HECI #1 [8086:9d3a] (rev 21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP CSME HECI [103c:84be]
    Kernel driver inuse: mei_me
    Kernel modules:mei_me
00:17.0 SATAcontroller [0106]: Intel Corporation Sunrise Point-LP SATA Controller[AHCI mode] [8086:9d03] (rev 21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP SATA Controller [AHCI mode][103c:84be]
    Kernel driver inuse: ahci
    Kernel modules:ahci
00:1c.0 PCI bridge[0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port[8086:9d10] (rev f1)
    Kernel driver inuse: pcieport
00:1c.4 PCI bridge[0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5[8086:9d14] (rev f1)
    Kernel driver inuse: pcieport
00:1c.5 PCI bridge[0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #6[8086:9d15] (rev f1)
    Kernel driver inuse: pcieport
00:1f.0 ISA bridge[0601]: Intel Corporation Device [8086:9d4e] (rev 21)
    Subsystem:Hewlett-Packard Company Device [103c:84be]
00:1f.2 Memorycontroller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21](rev 21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP PMC [103c:84be]
00:1f.3 Audio device[0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP HD Audio [103c:84be]
    Kernel driver inuse: snd_hda_intel
    Kernel modules:snd_hda_intel, snd_soc_skl
00:1f.4 SMBus[0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
    Subsystem:Hewlett-Packard Company Sunrise Point-LP SMBus [103c:84be]
    Kernel modules:i2c_i801
02:00.0 Networkcontroller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11acPCIe Wireless Network Adapter [10ec:c821]
    Subsystem:Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless NetworkAdapter [103c:831a]
03:00.0 Ethernetcontroller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem:Hewlett-Packard Company RTL8111/8168/8411 PCI Express GigabitEthernet Controller [103c:84be]
    Kernel driver inuse: r8169
    Kernel modules:r8169
```

---

### Post by VMC on 2019-04-25
> **andrei113113113 said:**
> Nothing
When I get nothing, its because of missing firmware. Check this:
```
ls /lib/firmware|grep wifi
```, and see if any outpur matches your wifi hardware.

---

### Post by andrei113113113 on 2019-04-26
> **VMC said:**
> When I get nothing, its because of missing firmware. Check this:
```
ls /lib/firmware|grep wifi
```, and see if any outpur matches your wifi hardware.
This is the output:
```
iwlwifi-1000-5.ucode
iwlwifi-100-5.ucode
iwlwifi-105-6.ucode
iwlwifi-135-6.ucode
iwlwifi-2000-6.ucode
iwlwifi-2030-6.ucode
iwlwifi-3160-10.ucode
iwlwifi-3160-12.ucode
iwlwifi-3160-13.ucode
iwlwifi-3160-16.ucode
iwlwifi-3160-17.ucode
iwlwifi-3160-7.ucode
iwlwifi-3160-8.ucode
iwlwifi-3160-9.ucode
iwlwifi-3168-21.ucode
iwlwifi-3168-22.ucode
iwlwifi-3168-27.ucode
iwlwifi-3168-29.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2a-6.ucode
iwlwifi-6000g2b-6.ucode
iwlwifi-6050-5.ucode
iwlwifi-7260-10.ucode
iwlwifi-7260-12.ucode
iwlwifi-7260-13.ucode
iwlwifi-7260-16.ucode
iwlwifi-7260-17.ucode
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-13.ucode
iwlwifi-7265-16.ucode
iwlwifi-7265-17.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode
iwlwifi-7265D-13.ucode
iwlwifi-7265D-16.ucode
iwlwifi-7265D-17.ucode
iwlwifi-7265D-21.ucode
iwlwifi-7265D-22.ucode
iwlwifi-7265D-27.ucode
iwlwifi-7265D-29.ucode
iwlwifi-8000C-13.ucode
iwlwifi-8000C-16.ucode
iwlwifi-8000C-21.ucode
iwlwifi-8000C-22.ucode
iwlwifi-8000C-27.ucode
iwlwifi-8000C-31.ucode
iwlwifi-8000C-34.ucode
iwlwifi-8000C-36.ucode
iwlwifi-8265-21.ucode
iwlwifi-8265-22.ucode
iwlwifi-8265-27.ucode
iwlwifi-8265-31.ucode
iwlwifi-8265-34.ucode
iwlwifi-8265-36.ucode
iwlwifi-9000-pu-b0-jf-b0-33.ucode
iwlwifi-9000-pu-b0-jf-b0-34.ucode
iwlwifi-9000-pu-b0-jf-b0-38.ucode
iwlwifi-9260-th-b0-jf-b0-33.ucode
iwlwifi-9260-th-b0-jf-b0-34.ucode
iwlwifi-9260-th-b0-jf-b0-38.ucode
mwlwifi
rtlwifi


```

---

### Post by VMC on 2019-04-26
Looks like you have the firmware, how about firmware settings in the BIOS. Check to make sure it enabled.

---

### Post by andrei113113113 on 2019-04-26
> **VMC said:**
> Looks like you have the firmware, how about firmware settings in the BIOS. Check to make sure it enabled.
What should i exactly look for in the BIOS?

---

### Post by praseodym on 2019-04-26
Realtek 8821CE wifi chip.

How do you post results here without internet? Exactly: Use the same method to download that driver from my post above. If that works install the wifi driver with deactivated secure boot

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```

---

### Post by andrei113113113 on 2019-04-27
> **praseodym said:**
> Realtek 8821CE wifi chip.

How do you post results here without internet? Exactly: Use the same method to download that driver from my post above. If that works install the wifi driver with deactivated secure boot

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
I'm using another laptop to reply here. I downloaded the driver as you said and moved it to the laptop with the problem. I try to install the package with sudo dpkg -i and this is what i get: 
```


(Reading database... 125266 files and directories currently installed.)
Preparing to unpackr8168-dkms_8.046.00-1_all.deb ...
Unpacking r8168-dkms(8.046.00-1) over (8.046.00-1) ...
dpkg: dependencyproblems prevent configuration of r8168-dkms:
 r8168-dkms dependson dkms (>= 2.1.0.0); however:
  Package dkms isnot installed.


dpkg: errorprocessing package r8168-dkms (--install):
 dependency problems- leaving unconfigured
Errors wereencountered while processing:
 r8168-dkms


```

---

### Post by praseodym on 2019-04-27
[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.6.1-4ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.6.1-4ubuntu1_all.deb)

Add this one as well

---

### Post by andrei113113113 on 2019-04-28
> **praseodym said:**
> [http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.6.1-4ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.6.1-4ubuntu1_all.deb)

Add this one as well
I downloaded it and moved to the laptop, I do not think this packages are istalled, I am getting a bunch of errors while i try to install them with sudo dpkg -i, like the one from the above.e

---

### Post by praseodym on 2019-04-28
Please place both of them in "Downloads" and run
```

cd ~/Downloads/
sudo dpkg -i *.deb
```Post error results with a txt file

---

### Post by andrei113113113 on 2019-04-29
Should I download all the packages that he is asking me for ?
```
(Reading database ... 125323 files and directories currently installed.)Preparing to unpack dkms_2.6.1-4ubuntu1_all.deb ...
Unpacking dkms (2.6.1-4ubuntu1) over (2.6.1-4ubuntu1) ...
dpkg: dependency problems prevent configuration of dkms:
 dkms depends on gcc; however:
  Package gcc is not installed.
 dkms depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 dkms depends on make | build-essential; however:
  Package make is not installed.
  Package build-essential is not installed.


dpkg: error processing package dkms (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Errors were encountered while processing:
 dkms



```

---

### Post by praseodym on 2019-04-30
Thats an option. Put them into "Downloads", too.

---

### Post by andrei113113113 on 2019-05-01
> **praseodym said:**
> Thats an option. Put them into "Downloads", too.

I have to download a lot of packages, is not there any way to download them faster?

---

### Post by wildmanne39 on 2019-05-01
You can use a cell phone and tether it to your computer using an usb cable then it will essentially be an ethernet connection, just plug it into your computer and turn tethering on in your phone or turn it on first then plug it in,I do not remember it is one way or the other first.

---

### Post by andrei113113113 on 2019-05-01
> **wildmanne39 said:**
> You can use a cell phone and tether it to your computer using an usb cable then it will essentially be an ethernet connection, just plug it into your computer and turn tethering on in your phone or turn it on first then plug it in,I do not remember it is one way or the other first.
I have tried but ethernet or your method is not working too.

---

### Post by wildmanne39 on 2019-05-01
Since it connects through your USB port I see no reason for your Ethernet to have to work to tether to your cell phone, it just shows as an Ethernet connection it does not use your Ethernet card.

---

### Post by praseodym on 2019-05-01
Add the CD/USB to the running system, add it as package source and run from terminal
```

sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by andrei113113113 on 2019-05-01
> **praseodym said:**
> Realtek 8821CE wifi chip.

How do you post results here without internet? Exactly: Use the same method to download that driver from my post above. If that works install the wifi driver with deactivated secure boot

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```

After [**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533") opened my eyes and teached me that you can connect to internet through a phone with a USB cable i used this and it works now, seems like i had no drivers installed, thanks a lot !

---

