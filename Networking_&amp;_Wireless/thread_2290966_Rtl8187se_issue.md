---
title: "Rtl8187se issue"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by stan20 on 2015-08-16
I am using a old toshiba laptop for college and need to put the network card in to monitoring mode. I have spent two days googling this and trying different guides, but keep getting stuck with errors after the ./wlan0up, when trying to setup the proper drivers.
 ```
stan@Huffy:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780MC [Mobility Radeon HD 3100]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)



```


after i do the ./wlan0up this is what i get.

```
insmod: ERROR: could not load module ieee80211_crypt-rtl.ko: No such file or directory
insmod: ERROR: could not load module ieee80211_crypt_wep-rtl.ko: No such file or directory
insmod: ERROR: could not load module ieee80211_crypt_tkip-rtl.ko: No such file or directory
insmod: ERROR: could not load module ieee80211_crypt_ccmp-rtl.ko: No such file or directory
insmod: ERROR: could not load module ieee80211-rtl.ko: No such file or directory
insmod: ERROR: could not load module r8180.ko: No such file or directory
```

---

### Post by Bucky Ball on 2015-08-17
Monitoring mode? Not sure what that is. Could you post the output of:

```
sudo lshw -C network
```

Is the wireless actually working? Can you please give a fuller description of what you are trying to do and what drivers you are trying to install?

You might want to have a look at squakie's post [here]("http://ubuntuforums.org/showthread.php?t=2226134&p=13033035&viewfull=1#post13033035") and the last one which tells how to make the change permanent.

---

