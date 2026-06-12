---
title: "Can Not connect to internet on ubuntu 13.10"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by Jordan_Johnson on 2014-01-22
I am a high school student brand new to Ubuntu and I've just installed Ubuntu 13.10 on my dell Inspiron 1501 and I can't connect through LAN or WiFi. I ran lspci with the results below and I don't know what to do next. Can someone help me please?[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]jordan@jordan-Inspiron-1501:~$ lspci[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx][/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 2[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 3[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 13)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200][/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]05:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Times New Roman]jordan@jordan-Inspiron-1501:~$

[/FONT][/COLOR][/SIZE]And I also used the code sudo lshw -C network and got these results.
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]jordan@jordan-Inspiron-1501:~$ sudo lshw -C network[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman][sudo] password for jordan:[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]  *-network               [/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       description: Network controller[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       product: BCM4311 802.11a/b/g[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       physical id: 0[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       bus info: pci@0000:05:00.0[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       version: 01[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       width: 32 bits[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       clock: 33MHz[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       capabilities: pm msi pciexpress bus_master cap_list[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       configuration: driver=wl latency=0[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       resources: irq:18 memory:c0200000-c0203fff[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]  *-network UNCLAIMED[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       description: Ethernet controller[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       product: BCM4401-B0 100Base-TX[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       physical id: 0[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       bus info: pci@0000:08:00.0[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       version: 02[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       width: 32 bits[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       clock: 33MHz[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       capabilities: pm bus_master cap_list[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       configuration: latency=64[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]       resources: memory:c0300000-c0301fff[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#000000][FONT=Times New Roman]jordan@jordan-Inspiron-1501:~$[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000] [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]

---

### Post by sudodus on 2014-01-22
Welcome to the Ubuntu Forums :-)

I know there are problems with Broadcom Wifi. You need a proprietary driver, that you install via the internet. But you should be able to use the wired internet, even when it is made by Broadcom. Can you switch off the wifi (with a mechanical switch or in the BIOS menu system)?

Let us hope that someone with experience of your kind of computer will read this and help you :-)

---

### Post by Jordan_Johnson on 2014-01-22
Thanks for your fast response.  I am getting no connection via wired either.  Do you know if Broadcom Ethernet cards need special drivers too?

---

### Post by sudodus on 2014-01-22
No, I don't know about that. Usually wired network works, because it is (should be) standardized since long ago. But it is possible that the wifi disturbs unless you can switch it off.

You can always try to reboot the computer and hope it will work after reboot. But think we need help from someone with more knowledge about Broadcom and Dell. Let us hope that our posts will be observed ...

---

### Post by sudodus on 2014-01-22
No, I don't know about that. Usually wired network works, because it is (should be) standardized since long ago. But it is possible that the wifi disturbs unless you can switch it off.

You can always try to reboot the computer and hope it will work after reboot. But think we need help from someone with more knowledge about Broadcom and Dell. Let us hope that our posts will be observed ...

By the way, have you checked the md5sum, so that you know that the download of the iso file was correct?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by praseodym on 2014-01-22
Download this package and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/*.deb
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Check your wireless and show the outputs of:
```

lsmod
dmesg | grep b43
iwconfig
rfkill list
lspci -nnk | grep -iA2 net
```

---

### Post by spitter on 2014-03-12
In my case during a fresh install ubuntu13.10 via usb I couldn't connect my wired network. Using your codes, checks and restart, it works for me, Acer Travelmate-5310 with Broadcom [14e4:4311].
Thank you very much

---

