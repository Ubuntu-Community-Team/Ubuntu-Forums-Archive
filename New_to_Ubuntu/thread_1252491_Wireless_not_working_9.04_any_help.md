---
title: "Wireless not working 9.04 any help"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by as3k on 2009-08-28
Hello all,
I am a COMPLETE NOOB to ubuntu and linux but I wanted to try my hand at a new OS. I installed Ubuntu Jaunty Jakelope on my old Gateway MX6455 laptop. It loaded great and runs perfectly fine EXCEPT for my wireless.  For some reason it doesnt start up. I clicked on the network manager on the top right of the screen nothing is shown. below i have included the readout from a few commands that i have seen on the web to figure out wireless hardware types/ setups. 

Screenshots:
[IMG]http://i31.tinypic.com/125qasz.png[/IMG]
[IMG]http://i28.tinypic.com/15etfuh.png[/IMG]

readout from lspci.txt
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
    Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
    Kernel modules: shpchp
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
    Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
    Kernel driver in use: pata_atiixp
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
    Kernel modules: radeonfb
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
    Kernel driver in use: sky2
    Kernel modules: sky2
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
05:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
05:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1
05:09.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```
readout from $sudo lshw -C network
```
nick@nick-laptop:~$ sudo lshw -C network
[sudo] password for nick: 
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:8f:67:9e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:87:ea:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:c1:3e:20:29:2e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```thanks guys

---

### Post by earthpigg on 2009-08-28
this may sound silly, but i only suggest it because i myself have made this mistake:

is there a physical button on your laptop that enables/disables the wireless adapter?

---

### Post by lkraemer on 2009-08-28
First, if you have Windows on that Gateway, boot it up and make sure the
Wifi works.  Don't turn it off, then exit windows.  I forget what keys
turn it on/off but it might be CNTL F2.  Just leave it on in Windows,
then exit.

You need to follow this post.
[http://ubuntuforums.org/showthread.php?t=1251294](http://ubuntuforums.org/showthread.php?t=1251294)

It shouldn't be hard to get it working.  Just decide what route you
want to go.

lkraemer

---

### Post by ptn107 on 2009-08-28
You're using a Broadcom BCM4318 wireless adapter. I have the same one in my compaq laptop.  Broadcom adapters require proprietary firmware. You have two options, both do the exact same thing:

1) Install the package 'b43-fwcutter' and when it asks to fetch and install firmware say 'yes', voilà!

2) Open up System -> Administration -> Hardware Drivers and select Broadcom wireless driver (or similar) and click activate.  Let it download and choose yes if it asks to fetch and install firmware.

---

### Post by as3k on 2009-08-29
> 
*@ptn107*

You're using a Broadcom BCM4318 wireless adapter. I have the same one in my compaq laptop. Broadcom adapters require proprietary firmware. You have two options, both do the exact same thing:

1) Install the package 'b43-fwcutter' and when it asks to fetch and install firmware say 'yes', voilà!

2) Open up System -> Administration -> Hardware Drivers and select Broadcom wireless driver (or similar) and click activate. Let it download and choose yes if it asks to fetch and install firmware. I installed the b43-fwcutter.deb and ran it, it seems to have worked because now it shows it in the hardware drivers in admin.  Im happy about that now i know its there. BUT when i click activate it doesnt do anything. it stays with that grey bubble... so im guessing its not active.  any suggestions??

---

### Post by lkraemer on 2009-08-29
If you follow the previous post you should find the *.fw firmware located
in the appropriate folders.  If that exists, you should be able to enable
your Wifi.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
I'd still like to see the output of the following commands posted.
iwconfig should tell you more.

If nothing else works, you can still use the Windows Drivers with ndiswrapper.

lkraemer

---

### Post by LewRockwell on 2009-08-29
> **as3k said:**
> I installed the b43-fwcutter.deb and ran it, it seems to have worked because now it shows it in the hardware drivers in admin.  Im happy about that now i know its there. BUT when i click activate it doesnt do anything. it stays with that grey bubble... so im guessing its not active.  any suggestions??

reboot?

maybe several reboots?

we have had repeated occurences where rebooting several times "mysteriously" cures the subject of the trouble-call

spooky...

.

---

