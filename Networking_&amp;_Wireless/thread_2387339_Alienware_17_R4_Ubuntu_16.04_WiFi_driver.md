---
title: "Alienware 17 R4 Ubuntu 16.04 WiFi driver"
date: 2018-03-17
forum: Networking &amp; Wireless
---

### Post by activestealth on 2018-03-17
Hi all,

I have installed Ubuntu 16.04 on my new Alienware 17 R4 laptop that comes with Killer 1550 WiFi network card. Currently I am running on LAN cable to connect to the internet but would very much like to make use of my WiFi card. I have tested that it works well in Windows 10.

How do I get Killer 1550 installed on Alienware 17 R4? 

The following are my outputs from sudo lshw -C network:

**hello@world:~$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3c:00.0
       logical name: enp60s0
       version: 10
       serial: 10:65:30:fd:d6:35
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.92 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dd300000-dd33ffff ioport:d000(size=128)[B]

  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3d:00.0
       version: 29
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:dd200000-dd203fff[/B]

I can certainly use my ethernet hence I believe I do have the Qualcomm Atheros driver. Probing further on my network controller (WiFi card?):

[B]hello@world:~$ lspci -knn | grep Net -A2
3d:00.0 Network controller [0280]: Intel Corporation Device [8086:2526] (rev 29)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1550]
3e:00.0 Non-Volatile memory controller [0108]: Toshiba America Info Systems Device [1179:0116]
    Subsystem: Toshiba America Info Systems Device [1179:0001][/B]

In case this could be of any useful information, my current linux kernel is:

[B]hello@world:~$ uname -r
4.13.0-37-generic[/B]

Thank you all for reading and your kind assistance in getting my wifi to work!

---

### Post by chili555 on 2018-03-18
Please check my answer here: [https://askubuntu.com/questions/1016903/alienware-17-r4-ubuntu-16-04-wifi-driver/1016997#1016997](https://askubuntu.com/questions/1016903/alienware-17-r4-ubuntu-16-04-wifi-driver/1016997#1016997)

---

### Post by jeremy31 on 2018-03-18
Chili555 the subsystem ID isn't in the upstream kernel yet

---

### Post by chili555 on 2018-03-18
Thanks. Answer deleted. Sorry.

---

### Post by jeremy31 on 2018-03-18
It would be better to know what the sticker on the card says it is as the source code doesn't give much for clues
```
/* 9000 Series */
	{IWL_PCI_DEVICE(0x2526, 0x0000, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x2526, 0x0010, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0A10, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0010, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0210, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0410, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0610, iwl9260_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0310, iwl5165_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0000, iwl5165_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0510, iwl5165_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x2010, iwl5165_2ac_cfg)},
	{IWL_PCI_DEVICE(0x2526, 0x1420, iwl5165_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x0710, iwl5165_2ac_cfg)},
	{IWL_PCI_DEVICE(0x9DF0, 0x2A10, iwl5165_2ac_cfg)},

```

---

### Post by chili555 on 2018-03-18
FYI, I just ran a live session for 18.04 running kernel version 4.15.0-10 and it isn't included there, either.

---

### Post by activestealth on 2018-03-19
Thanks guys, so thankful for the open source community in helping! My Alien needs help =)

---

### Post by jeremy31 on 2018-03-19
Do you have Windows on this still?  I need the inf file for the wifi, I think it can be found in Device Manager, click the wireless adapter/properties and see if the inf is listed in the driver section
You might want to contact [email]killersupport@rivetnetworks.com[/email] and ask about Linux support

---

### Post by jeremy31 on 2018-03-20
Can you provide results for
```
lspci -nv -s 3d:00.0
```

---

### Post by activestealth on 2018-03-22
> **jeremy31 said:**
> Can you provide results for
```
lspci -nv -s 3d:00.0
```

Hi Jeremy,

Thanks so much for helping! The following are the outputs:

[B]hello@world:~$ lspci -nv -s 3d:00.0
3d:00.0 0280: 8086:2526 (rev 29)
    Subsystem: 1a56:1550
    Flags: fast devsel, IRQ 255
    Memory at dd200000 (64-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: <access denied>[/B]

Much appreciation!

---

### Post by activestealth on 2018-03-22
> **jeremy31 said:**
> Do you have Windows on this still?  I need the inf file for the wifi, I think it can be found in Device Manager, click the wireless adapter/properties and see if the inf is listed in the driver section
You might want to contact [EMAIL="killersupport@rivetnetworks.com"]killersupport@rivetnetworks.com[/EMAIL] and ask about Linux support

Yes I do, but the .dat and .sys files appears to be too huge to be attached here >< I have attached a print screen of Killer-1550 details for its drivers in Windows 10.

---

### Post by karrnb on 2018-04-24
Hi,

I had a similar problem. I'd written to Killer, and this was their response.

'[FONT=arial]Thank you for your email.[/FONT]

[FONT=arial]Unfortunately, there is not currently a Linux driver available for the [/FONT][FONT=arial]Killer[/FONT][FONT=arial] Wireless 1550. We do not currently have a timetable on when one will be developed. We apologize for the inconvenience. '

One way around this is to use [/FONT]ndiswrapper, but installing drivers is still difficult.

---

### Post by jeremy31 on 2018-04-25
I have been in contact with Intel on this matter and it is being worked on, for now we can use Intel backports
```

sudo apt-get install git build-essential
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git/
cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
```

Reboot, after a kernel update you will need to 
```
cd backport-iwlwifi
make clean
make defconfig-iwlwifi-public
make -j4
sudo make install
```

Make sure Secure Boot is disabled in BIOS/UEFI

---

### Post by praseodym on 2019-01-06
Jeremy: Will this device be supported in the near future? With which kernel? Or is it already supported?

---

### Post by jeremy31 on 2019-01-06
They were added upstream back in July, it looks like it is supported in the Ubuntu 4.18 kernels.  A bug report would have to be filed to get them into 4.15

---

### Post by chili555 on 2019-01-06
> **praseodym said:**
> Jeremy: Will this device be supported in the near future? With which kernel? Or is it already supported?The device above is:> 3d:00.0 0280: 8086:2526 (rev 29)
Subsystem: 1a56:1550It appears to be supported in Ubuntu 18.10:

```
chili@T440p:~$ modinfo iwlwifi | grep 2526 | grep 1550
alias:          pci:v00008086d00002526sv*sd00001550bc*sc*i*

```My kernel version is 4.18.0-13-generic.

I haven't the device, so I can't test further.

I hope someone with the device will try a live session for 18.10 and inform us.

---

