---
title: "ubuntustudio wireless problem"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by kotak07 on 2008-05-30
I just installed ubuntu studio but i can't get on the internet even with the restricted drivers for HAL and atheros. in Windows my card says its the AR5007EG card. its in built. I dont know what to do so if anyone could help me. thanks
Kotak.

---

### Post by kotak07 on 2008-05-30
i found some tutorials to make the chipset work but this is what happens when i get to 
"sudo make" and after that.
```
cd: 1: can't cd to /lib/modules/2.6.24-16-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-16-rt/build is missing, please set KERNELPATH.  Stop.

```
I'm using this guide. [http://ubuntuforums.org/showthread.php?t=800686&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=800686&highlight=AR5007EG)

---

### Post by hal10000 on 2008-05-30
First you have to find out which card you have. Open a terminal window and try the command [COLOR="Red"]lspci[/COLOR], you may post the output here (mark the output with the mouse and paste it into your Browser with the middle mouse button. The output may look similar to rhis one:
> 
user@host:~$ lspci

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
[COLOR="Red"]01:08.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)[/COLOR]
05:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)

This is the output of my own lspci-command. The red line is my wireless card.
So we can find out which chipset is the right for your PC.

In most cases you don't need to compile or install additional drivers. we just need to know which chipset is the right for your card. Once you posted the output we can go on configuring your card.

---

### Post by kotak07 on 2008-05-30
hey thanks for replying. heres my lspci.

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


```

---

### Post by hal10000 on 2008-05-30
I guess the driver you need is called [COLOR="Red"]ath_pci[/COLOR].
You can test if this driver is loaded with the command [COLOR="Red"]lsmod | grep ath_pci[/COLOR]. If you get no outut from this command then you should try to load it manually with [COLOR="Red"]sudo modprobe ath_pci[/COLOR]. Then do [COLOR="Red"]lsmod | grep ath_pci[/COLOR] again to verify if it is loaded now. Once the druver is loaded, you can configure your network with your network-manager ( iguess in gnome you can find it under System settings--->configure network or something similar, I don't use gnome, so I can't tell exactly where it is located in the menu. You have to fill in things like essid, WPA /WEP -Key nameserver etc. If you get connected to a wireless router then the nameserver-address is usually the ip-Address of your router, or you may fill in the nameserver-address of your provider.

Hope this can help you.


Hope this can help you.

---

### Post by kotak07 on 2008-05-30
this is what came up when i did lsmod | grep ath_pci
```

neal@ubuntu:~$ lsmod | grep ath_pci
ath_pci               101408  0 
wlan                  208240  1 ath_pci
ath_hal               192720  1 ath_pci


```

i guess its not enabled but i did the other thing and the same thing came up and i cant find network manager and there is this network thing but it doesnt list wireless it just has phone modem and ethernet

---

### Post by hal10000 on 2008-05-31
Your driver is loaded, and if you didn't do a sudo modprobe ath_pci it is loaded automatically, that's fine.

There are several programs to configure a wireless device, i suggest to install such a programm, e.g. wlassistant, which is a KDE-tool, but you can run it under gnome too:

[COLOR="Red"]sudo apt-get install wlassistant[/COLOR]. Once you have installed it, you can run it with [COLOR="Red"]ALT+F2 ---> gksudo wlassistant[/COLOR].
This tool scans for wireless accesspoints in your neighborhood and presents you a list of Accesspoint that can be reached. You have to choose your own accesspoint and configure it manually or via DHCP. If you do it manually, you have to fill in the correct parameters like IP-Address essid etc.

If this doen't work or if you are unsure about further configuration, make new post, so we can try another way.

---

### Post by kotak07 on 2008-05-31
It didnt work. this is what i get when i run it.
```
Error-Wireless Assistant
No usable wireless devices found.
Wireless Assistant will now quit.

```

---

### Post by kotak07 on 2008-05-31
i also did this 
```

neal@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:35:57:74
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.2 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```

I think UNCLAIMED means that the driver is not loaded.

---

### Post by hal10000 on 2008-05-31
I guess your driver is ath_pci. The problem is, I don't have such a card, so I can not on my own pc.

Before we have to go deeper into your problem, i have one more idea:

1.   Load the driver manually -----> [COLOR="Red"]sudo modprobe ath_pci[/COLOR]
2.   perform [COLOR="Red"]iwconfig[/COLOR] and look if it can find any wireless devices
3.   run wlassistand again and configure your network

If this doesn't work, then we have to go deeper.
You shold then post the output of the following commands:
1.  [COLOR="Red"]lspci -n[/COLOR]
2. Tell us all relevant things like your kernel-version ([COLOR="Red"]uname -a[/COLOR]), wether you will be connected to an Access-Point (AP) or to a wireless router, wether you want to configure your network manually or with DHCP, the ip-address if your nameserver (if you have a wireless router then your nameserver-address might be the ip-address of your router, otherwise it might be the ip-address of your providers nameserver),
the content of the file [COLOR="Red"]/etc/network/interfaces[/COLOR], but don't forget to disguise your real essid and wireless-key.

---

### Post by phidia on 2008-05-31
> **kotak07 said:**
> I just installed ubuntu studio but i can't get on the internet even with the restricted drivers for HAL and atheros. in Windows my card says its the AR5007EG card. its in built. I dont know what to do so if anyone could help me. thanks
Kotak.

If you have the ar6007eg card, and since that's what windows reports I believe it, then there is a recent how to [here]("http://ubuntuforums.org/showthread.php?t=795984&highlight=atheros+ar5007eg").
If you are using 64 bit with that card then although it can be made to work it's not easy-and that is an understatement,

---

### Post by kotak07 on 2008-06-01
phidia that guide doesnt work for me. I still get this error when trying to do sudo make
```

cd: 1: can't cd to /lib/modules/2.6.24-16-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-16-rt/build is missing, please set KERNELPATH.  Stop.

```

and hal10000 your method didnt work either so heres lspci -n
```

neal@ubuntu:~$ lspci -n
00:00.0 0600: 8086:2a00 (rev 0c)
00:02.0 0300: 8086:2a02 (rev 0c)
00:02.1 0380: 8086:2a03 (rev 0c)
00:1a.0 0c03: 8086:2834 (rev 03)
00:1a.1 0c03: 8086:2835 (rev 03)
00:1a.7 0c03: 8086:283a (rev 03)
00:1b.0 0403: 8086:284b (rev 03)
00:1c.0 0604: 8086:283f (rev 03)
00:1c.1 0604: 8086:2841 (rev 03)
00:1c.2 0604: 8086:2843 (rev 03)
00:1c.3 0604: 8086:2845 (rev 03)
00:1c.4 0604: 8086:2847 (rev 03)
00:1d.0 0c03: 8086:2830 (rev 03)
00:1d.1 0c03: 8086:2831 (rev 03)
00:1d.2 0c03: 8086:2832 (rev 03)
00:1d.7 0c03: 8086:2836 (rev 03)
00:1e.0 0604: 8086:2448 (rev f3)
00:1f.0 0601: 8086:2815 (rev 03)
00:1f.1 0101: 8086:2850 (rev 03)
00:1f.2 0106: 8086:2829 (rev 03)
00:1f.3 0c05: 8086:283e (rev 03)
04:00.0 0200: 10ec:8136 (rev 01)
05:00.0 0200: 168c:001c (rev 01)
0c:04.0 0607: 104c:8039
0c:04.1 0c00: 104c:803a
0c:04.2 0180: 104c:803b
0c:04.3 0805: 104c:803c

```

heres uname -a

```

neal@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-17-rt #1 SMP PREEMPT RT Thu May 1 16:23:33 UTC 2008 i686 GNU/Linux

```

i will be connecting to a wireless router. i will probably use a static ip so ill configure it myself 
here etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp



auto eth0

```

---

### Post by kotak07 on 2008-06-02
bump if anyone has any other suggestions

---

### Post by hal10000 on 2008-06-03
Hi,
i have found two links which you might help, but take in mind that you should **exactly** follow the steps described there.

The first one describes the installation and configuration using ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=792158]("http://ubuntuforums.org/showthread.php?t=792158")

and the second one may be used if ndiswrapper doesn' work:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")

---

### Post by gentlejunk on 2008-12-08
> **kotak07 said:**
> phidia that guide doesnt work for me. I still get this error when trying to do sudo make
```

cd: 1: can't cd to /lib/modules/2.6.24-16-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-16-rt/build is missing, please set KERNELPATH.  Stop.

```

[/code]

i had sam problem and solved it by following
[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

with this code before instaling driver

sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)

---

