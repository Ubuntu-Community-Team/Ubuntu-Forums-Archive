---
title: "Semp Toshiba Aurex wireless problem"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by daleybortolon on 2013-12-11
0 down vote favorite
	

I've just bought a Semp Toshiba Aurex notebook IS 1817HD, Intel i5 / 4GB RAM / 2 X 750 G SATA II , Supports RAID 0 and 1 / ATI Radeon HD 5650 GPU with 2GB DDR3 RAM / Wi-Fi 802.11 b/g/n, Realtek 10/100/1000 Mbps Ethernet Adapter.

I formatted and installed Ubuntu 13.10 in one of the hard drives (the other I use as a partition for files), and even though the wireless worked perfectly at first, after a couple of days it stopped working. Ubuntu won't even recognize it. I've been googling for a solution, but it's no use, I haven't been able to find anything helpful that actually works.

Does anybody have any tips on this? Any help will be greatly appreciated!

carlos@toshiba:~$ sudo lshw -class network
[sudo] password for carlos: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 06
       serial: 00:14:0b:6f:37:31
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:6000(size=256) memory:f0d04000-f0d04fff memory:f0d00000-f0d03fff

carlos@toshiba:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

carlos@toshiba:~$ dmesg | grep -i firmware
[    0.255779] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored

rfkill list all  

(no results!!!!!!!!)

I have posted it at askubuntu with no results.
Please people, any suggestions are welcome!

---

### Post by chili555 on 2013-12-11
We see no wireless device at all! Is it one of those rare devices that's attached to an internal USB bus?```
lsusb
```

---

### Post by daleybortolon on 2013-12-11
> **chili555 said:**
> We see no wireless device at all! Is it one of those rare devices that's attached to an internal USB bus?```
lsusb
```

Ok, this is the resultr for thr code:
carlos@toshiba:~$ lsusb
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1934:5168 Feature Integration Technology Inc. (Fintek) F71610A or F71612A Consumer Infrared Receiver/Transceiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have no idea!
Thanks for the reply!

---

### Post by chili555 on 2013-12-11
I still see no wireless. Does it show up in Windows or elsewhere? Is there a setting in the BIOS to enable and disable wireless?

---

### Post by daleybortolon on 2013-12-12
> **chili555 said:**
> I still see no wireless. Does it show up in Windows or elsewhere? Is there a setting in the BIOS to enable and disable wireless?

Yes, it worked fine with windows and worked fine with Ubuntu for a few days, using live cd and after it being installed. Today, live cd won't recognize tha wireless card anymore. I've also checked BIOS and it shows no wireless options. Is it possible that somehow I "burned" the WI FI card during the process of formatting and installing Ubuntu? I tried dual boot but to no avail so I had to format de HDDs and install Ubuntu in one of them. I worked fine for a few days...

---

### Post by chili555 on 2013-12-12
>  Is it possible that somehow I "burned" the WI FI card during the process of formatting and installing Ubuntu?Anything is possible, I guess, however that would be the first case I ever heard about. I've been hanging around Linux for many years so I've heard of a lot, but not that.>  I worked fine for a few days... Do you mean after you installed Ubuntu? Then it didn't burn because of the install, did it?

I fear that it has failed electrically.

---

### Post by daleybortolon on 2013-12-13
> **chili555 said:**
> Anything is possible, I guess, however that would be the first case I ever heard about. I've been hanging around Linux for many years so I've heard of a lot, but not that.Do you mean after you installed Ubuntu? Then it didn't burn because of the install, did it?

I fear that it has failed electrically.

I agree with you. I've also been using Ubuntu since 7.10 and I've never heard of it causing any trouble like that. I think that while fiddling in BIOS I may have pressed a bad combination of keys that led to WIFI card "desconnection" or a "short circuit". I'm a Ubuntu fan but no expert. Would have any suggestions as how to how to setup BIOS properly?

---

### Post by chili555 on 2013-12-13
> **daleybortolon said:**
> I agree with you. I've also been using Ubuntu since 7.10 and I've never heard of it causing any trouble like that. I think that while fiddling in BIOS I may have pressed a bad combination of keys that led to WIFI card "desconnection" or a "short circuit". I'm a Ubuntu fan but no expert. Would have any suggestions as how to how to setup BIOS properly?In most cases,Ubuntu will work properly with the BIOS reset to default. In many BIOS', it is F5 and then F10 to save. [http://www.build-my-home-computer.com/image-files/bios-load-setup-default.jpg](http://www.build-my-home-computer.com/image-files/bios-load-setup-default.jpg)

If you reset the BIOS to default and the wireless still doesn't appear in lspci, then I'd consider either replacing it with something from Ebay or a carefully researched for Ubuntu capability USB wireless.

---

