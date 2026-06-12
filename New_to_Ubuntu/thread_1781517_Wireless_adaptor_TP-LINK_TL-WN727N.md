---
title: "Wireless adaptor TP-LINK TL-WN727N"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by rakiru on 2011-06-13
Hi,

I have recently installed Ubuntu 11.04, but I'm still having problems using my wireless adaptor. It is a TP-LINK TL-WN727N, which I've found a lot of people having problems with. I've found a couple of solutions, but one is for an older version of ubuntu, and thus the package cannot be found, and the other is for a different linux distro, although it looked like it should work. These pages are:

[http://ubuntuforums.org/showthread.php?t=1566639](http://ubuntuforums.org/showthread.php?t=1566639)
> **nickbooker said:**
> ```
sudo apt-get update

sudo apt-get install linux-backports-modules-wireless-generic
```

[http://community.linuxmint.com/hardware/view/1518](http://community.linuxmint.com/hardware/view/1518)
> Added the following lines to /etc/modprobe.d/blacklist.conf


#disable the misbehaving RALink drivers.
#The WN727N only needs the rt2870sta driver.
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00libAt the moment I'm connected via ethernet cable to my laptop which is connected to the wireless network, which is far from ideal. Any help will be much appreciated, as it was a similar problem (albeit different wireless adaptors) that stopped me from using Ubuntu before.

Many thanks
Sean Gordon

Edit: I've also just found this post which has an extra line added to the blacklist than quoted above, but this still does not work for me: [http://ubuntuforums.org/showpost.php?p=10785495&postcount=12](http://ubuntuforums.org/showpost.php?p=10785495&postcount=12)

---

### Post by wildmanne39 on 2011-06-13
> **rakiru said:**
> Hi,

I have recently installed Ubuntu 11.04, but I'm still having problems using my wireless adaptor. It is a TP-LINK TL-WN727N, which I've found a lot of people having problems with. I've found a couple of solutions, but one is for an older version of ubuntu, and thus the package cannot be found, and the other is for a different linux distro, although it looked like it should work. These pages are:

[http://ubuntuforums.org/showthread.php?t=1566639](http://ubuntuforums.org/showthread.php?t=1566639)


[http://community.linuxmint.com/hardware/view/1518](http://community.linuxmint.com/hardware/view/1518)
At the moment I'm connected via ethernet cable to my laptop which is connected to the wireless network, which is far from ideal. Any help will be much appreciated, as it was a similar problem (albeit different wireless adaptors) that stopped me from using Ubuntu before.

Many thanks
Sean Gordon

Edit: I've also just found this post which has an extra line added to the blacklist than quoted above, but this still does not work for me: [http://ubuntuforums.org/showpost.php?p=10785495&postcount=12](http://ubuntuforums.org/showpost.php?p=10785495&postcount=12)
Hi run this command in a terminal.
```
sudo lshw -c network
```
```
lspci
```if it is is usb run this command also.
```
lsusb
``` and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by rakiru on 2011-06-23
```
sean@sean-ubuntu:~$ sudo lshw -c network
[sudo] password for sean: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: bc:ae:c5:19:76:cb
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:b800(size=256) memory:cffff000-cfffffff memory:cfff8000-cfffbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@2
       logical name: wlan0
       serial: d8:5d:4c:90:7f:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb multicast=yes wireless=Ralink STA
sean@sean-ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
04:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
05:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 4770 [RV740]
05:00.1 Audio device: ATI Technologies Inc RV710/730
sean@sean-ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by wildmanne39 on 2011-06-23
Hi, I found this link, it has the same chip as yours, the RT2870 RT3070.
[http://ubuntuforums.org/showthread.php?t=1665389&highlight=RT2870%2FRT3070+Wireless+Adapter](http://ubuntuforums.org/showthread.php?t=1665389&highlight=RT2870%2FRT3070+Wireless+Adapter)

---

### Post by rakiru on 2011-07-02
Thanks for the reply. That thread looked like it would help, but I still can't seem to make it work. :/

---

### Post by nito2721 on 2012-02-20
This worked for me. Hopefully it helps others.

[http://ubuntuforums.org/archive/index.php/t-1800178.html]("http://ubuntuforums.org/archive/index.php/t-1800178.html")

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:cd Desktop/2011Press Tab and the remainder will fill in. Press Enter. Now do:sudo su
make
make install
modprobe rt5370sta
exit
Is your wireless working?

Props to chili555 for the solution.

---

### Post by jeanlikethis on 2012-03-05
rt5370 is the best driver and I am using it on ubuntu 11.10.

I used to use rt2800usb but found it is very slow and clogging though easy to enable. I finally decided to go with rt5370. 

It needs to be compiled but just following the instructions and it is very easy. I also blacklisted rt2800, 2870 for safety reasons. 

Presently, it is running very good and very reliable and fast.

---

### Post by tomfoley on 2012-05-14
@Nito2721 Your post#6 worked great for me under Ubuntu 12.04 LTS, which also did not recognize the adapter natively. Just one observation..

I'm using the adapter on a dual boot Windows XP/Ubuntu 12.04 netbook. Ubuntu reports a connection speed of 65Mbps whereas XP says it's 150Mbps. Same router, didn't as much as move the netbook, simply booted the machine using either OS. Curious, but I'm happy either way.

---

### Post by Gorkadread on 2012-06-16
> **nito2721 said:**
> This worked for me. Hopefully it helps others.

[http://ubuntuforums.org/archive/index.php/t-1800178.html](http://ubuntuforums.org/archive/index.php/t-1800178.html)

Go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) Download this to your desktop: RT8070/RT3070/RT3370/RT5370/RT5372USB Right-click it and select Extract Here. Rename the file that's extracted to RT5370. Right-click it and select Extract Here.

Open the resulting folder and go to os > linux and use any text editor to edit config.mk. Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close the text editor.

Now, a geek's dream; open a terminal and do:cd Desktop/2011Press Tab and the remainder will fill in. Press Enter. Now do:sudo su
make
make install
modprobe rt5370sta
exit
Is your wireless working?

Props to chili555 for the solution.
-----------------------------------

Just a little note: The drivers can now be found at [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501).

---

