---
title: "Wireless disconnects then can't be reconnected"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-09-15
Sorry if this question has been addressed before, but I am not very technical and I haven't found any solution that I understand. 

Usually rarely my Dell mini 9 randomly disconnects and keeps trying to reconnect, but it can't. Only rebooting the netbook makes it so it can reconnect again. Today I rebooted and then it disconnected again and couldn't be reconnected without rebooting. Right now it is working OK, but I fear it will disconnect again. 

I have no idea what the problem is and how to fix it. If anyone has any ideas please explain them in an easy to understand fashion. 

Thanks so much!

---

### Post by mapes12 on 2009-09-15
Hi

If you bought the Dell with Ubu pre installed do you have any kind of tech support from Dell that could help you out?

The reason I suggest this is because you may not be alone and Dell may have a specific Dell patch for your wifi adapter.

If Dell do not have others having the same problem then the next thing to check is your routers wifi configuration

---

### Post by nothingspecial on 2009-09-15
Open a terminal (applications > accessories > terminal) and type

```
sudo lshw -C network
```

and
```

lspci -k
```

and post the info here.

All these 2 commands do is give information about your wireless card and the kernel module (linux speak for driver) it is using.

---

### Post by greenleaves123 on 2009-09-15
jenny@jenny-laptop:~$ sudo lshw -C network
[sudo] password for jenny: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:2c:36:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:ca:51:56
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:4e:54:e4:ee:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jenny@jenny-laptop:~$ 

jenny@jenny-laptop:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Kernel modules: intel-rng, iTCO_wdt
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Kernel modules: i2c-i801
02:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
02:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
	Kernel modules: sdhci-pci
02:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169
jenny@jenny-laptop:~$

---

### Post by nothingspecial on 2009-09-15
Can you please run this in your terminal.

```

find /etc/modprobe.d/* -exec cat {} \; | grep wl
```

I think your driver is being blacklisted (I`m not sure).

To blacklist a module is to stop it loading at boot. I`ve done a bit of digging and may have found an answer.

Post the output please.

It maybe a good few hours until I can answer due to sleep, work etc

---

### Post by greenleaves123 on 2009-09-15
jenny@jenny-laptop:~$ find /etc/modprobe.d/* -exec cat {} \; | grep wl
cat: /etc/modprobe.d/arch: Is a directory
alias parport_lowlevel parport_pc
alias parport_lowlevel parport_pc
jenny@jenny-laptop:~$

---

### Post by nothingspecial on 2009-09-16
> **greenleaves123 said:**
> jenny@jenny-laptop:~$ find /etc/modprobe.d/* -exec cat {} \; | grep wl
cat: /etc/modprobe.d/arch: Is a directory
alias parport_lowlevel parport_pc
alias parport_lowlevel parport_pc
jenny@jenny-laptop:~$

Well that didn`t work.

Anyway (and I could be on the wrong track here and not helping at all)

I`ve seen another post where an update blacklists the wl module

(I realise you probably have no idea what I`m talking about)

To see if we are on the right track can you post the output of

```
ls /etc/modprobe.d
```

and ```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by greenleaves123 on 2009-09-16
jenny@jenny-laptop:~$ ls /etc/modprobe.d
aliases       blacklist              blacklist-watchdog  lrm-video
alsa-base     blacklist-bcm43        fuse                options
alsa-base~    blacklist-framebuffer  isapnp              toshiba_acpi.modprobe
arch          blacklist-modem        libpisock9
arch-aliases  blacklist-oss          libsane

jenny@jenny-laptop:~$ cat /etc/modprobe.d/blacklist.conf
cat: /etc/modprobe.d/blacklist.conf: No such file or directory
jenny@jenny-laptop:~$

---

### Post by HarrisonNapper on 2009-09-16
Does a window come up to prompt you to enter a password when it is trying to reconnect to the network?

If so, you may need to clear the password field and re-enter it.

---

### Post by nothingspecial on 2009-09-16
Hi

I take it you are not using the current Ubuntu but an earlier version. That is why it couldn`t find that file.

Hopefully simple fix. Go to system > administration > hardware drivers (it may have been called something different back then but it will be similar). See if an alternative wireless driver is in there.

If not your going to have to do this in the command line, but I will need to see a file first
```

cat /etc/modprobe.d/blacklist-bcm43
```

This method may not work anyway but we will try. Be aware that the linux and ubuntu developers are aware of this problem and it is being worked on right now

---

### Post by greenleaves123 on 2009-09-21
Oops, sorry, I've been busy with school work. No, there isn't an alternate driver.

---

