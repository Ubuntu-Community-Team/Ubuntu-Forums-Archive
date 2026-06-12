---
title: "wireless problem with hp 450 g1 in ubuntu"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by benjamin41 on 2015-04-23
hi 
I am a newbie user in ubuntu and i installed ubuntu 14.04LTS i have problem with wireless button i can't switch it on and always is off
i tried so many ways but doesn't work 

[HR][/HR]
for this code : 
```
iwlist eth1 scanning
```

i get this :
eth0      Interface doesn't support scanning.
ppp0      Interface doesn't support scanning.
lo        Interface doesn't support scanning

[HR][/HR]
and for this code :
```
lspci
```

i get this:

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] (rev ff)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter

please help :(](*,)

---

### Post by chili555 on 2015-04-23
Benjamin-

Thank you for agreeing to be our tester! Your device is relatively new and the driver has, up to now, been tricky to impossible to get working properly. However, a new and improved driver has appeared! I have compiled it successfully but I don't have the device, so I can test no further. That's where you can help us.

Please get a temporary internet connection by ethernet or tethering or whatever means possible. Open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/neurobin/MT7630E.git
cd MT7630E
make
sudo make install
sudo modprobe mt76xx
```It may take a reboot. Please let us know your result. We will probably have one additional step.

---

