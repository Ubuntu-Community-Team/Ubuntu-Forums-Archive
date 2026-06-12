---
title: "Auto Eth Issue"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-11-03
Hi,

A while back, I might have messed up my settings for my hardwired network connection. It still will not connect to a wired network connection, but I took a look at the wired connection, and it appeared that there were two redundant network connections (same MAC address) with different names. I believe that one was called Auto Eth0 and one was Auto Ethernet.

I could not connect using either network connection, so I deleted them. However, I cannot seem to figure out how to build a hardwired connection from scratch. Any suggestions?

All help is appreciated.

Thanks,
Kurt

+EDIT:
If there are no Wired connections listed in the network manager, and if you plug a cable in, the system automatically creates a connection called "Auto Ethernet". In the settings for this connection, the MAC address is blank. Perhaps if I enter in my ethernet card's MAC address into this setting, it might work?

---

### Post by endotherm on 2010-11-03
well, in network-manager, tell it to add a connection. the only real peice of info you absolutly need is the mac address for eth0, so run ifconfig -a, and check the value "HWAddr" to get it, and paste it into NM.

not sure if you want to use static addresses or dhcp, etc, so let us know if you have specific questions in the ip configuration realm.

---

### Post by jkurtisr32 on 2010-11-03
> **endotherm said:**
> well, in network-manager, tell it to add a connection. the only real peice of info you absolutly need is the mac address for eth0, so run ifconfig -a, and check the value "HWAddr" to get it, and paste it into NM.

not sure if you want to use static addresses or dhcp, etc, so let us know if you have specific questions in the ip configuration realm.

Thanks. Took a look at ifconfig -a. According to the output, I have two auto eth connections, which are eth0 and eth1. Is it displaying one as my wired connection and one the wireless? I only have one wired card.

I tried comparing the two MAC addresses in the output for eth0 and eth1 to the MAC address of my wireless card in the network manager, but the network manager does not display a MAC address for my wireless card, so I have no idea which MAC address corresponds to my wired connection.

---

### Post by cj13579 on 2010-11-03
what does your /etc/network/interfaces file look like?

---

### Post by jkurtisr32 on 2010-11-08
> **cj13579 said:**
> what does your /etc/network/interfaces file look like?

```
auto lo
iface lo inet loopback
```

This is what the file contains.

Did I use the CODE tags properly?

---

### Post by SuaSwe on 2010-11-08
Looks fine to me. :)

I believe you should be able to get your current and correct MAC from the BIOS, e.g. before booting into the operating system. Seems weird that two ethernet cards with separate MACs are listed when you only have one though!

---

### Post by SuaSwe on 2010-11-08
Also, what's the output of:

```

lspci

```

in Terminal?

---

### Post by jkurtisr32 on 2010-11-08
> **SuaSwe said:**
> Also, what's the output of:

```

lspci

```

in Terminal?

Here is the output

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

Still haven't found the mac address, but thanks a lot for your help.

-Kurt

---

### Post by sandyd on 2010-11-08
> **jkurtisr32 said:**
> Thanks. Took a look at ifconfig -a. According to the output, I have two auto eth connections, which are eth0 and eth1. Is it displaying one as my wired connection and one the wireless? I only have one wired card.

I tried comparing the two MAC addresses in the output for eth0 and eth1 to the MAC address of my wireless card in the network manager, but the network manager does not display a MAC address for my wireless card, so I have no idea which MAC address corresponds to my wired connection.
eth0 is by default ethernet
eth1 is wireless.

you can tell by running "sudo iwconfig"
only the wireless will show.

---

### Post by SuaSwe on 2010-11-09
I stand corrected! Wireless has always shown up as wlan0 on my systems. :)

---

### Post by jkurtisr32 on 2010-11-12
> **sandyd said:**
> eth0 is by default ethernet
eth1 is wireless.

you can tell by running "sudo iwconfig"
only the wireless will show.

This convention worked for me. I was able to find the proper mac address.

Thanks a lot for the help you guys.

-Kurtis

---

