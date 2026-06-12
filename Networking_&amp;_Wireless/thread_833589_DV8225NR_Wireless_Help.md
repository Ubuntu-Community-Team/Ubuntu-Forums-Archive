---
title: "DV8225NR Wireless Help"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by sleepwalka26 on 2008-06-18
I am using a HP DV8225NR laptop, usingUbuntu8.04. I have followed countless numbers of guides on how to get wifi working, and every time ended in the same scenario the " blue wifi light" comes on but i cannot connect via wifi. I have ndiswrapper-1.52 installed, bcm43xx blacklisted and i get

 ~$ ndiswrapper -l
bcmwl5 : driver installed
	device ( 14E4:4318 ) present (alternate driver: ssb)

Any ideas?

----------------
Now playing on MediaMonkey: [2 Pistols - Robbery](http://www.foxytunes.com/artist/2+pistols/track/robbery)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by Ayuthia on 2008-06-18
> **sleepwalka26 said:**
> I am using a HP DV8225NR laptop, using Ubuntu8.04. I have followed countless numbers of guides on how to get wifi working, and every time ended in the same scenario the "wifi light" comes on but no wifi. Any ideas?

----------------
Now playing on MediaMonkey: [2 Pistols - Robbery](http://www.foxytunes.com/artist/2+pistols/track/robbery)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)
Can you open up your Terminal and post the results for:
```
lspci -nn
```
It will help us figure out your wireless card.

---

### Post by sleepwalka26 on 2008-06-18
*~$ lspci -nn*
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
*[COLOR="Red"]**06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)**[/COLOR]*
06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

---

### Post by Ayuthia on 2008-06-25
Ok.  You might want to check lshw -C network and see which driver is being used.  It should say ndiswrapper.  If you see b43-pci-bridge, please try:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprbe ndiswrapper
```

EDIT:
Can you also post your uname -r info?  There have been some problems with the 4318 cards on some of the recent kernel releases.

---

### Post by sleepwalka26 on 2008-06-26
~$ uname -r
2.6.24-19-generic

---

### Post by sleepwalka26 on 2008-06-26
i used the codes u gave me, it got my wireless to work but everytime i shut down i gotta re enter it into my terminal... also i started out being able to connect to my router which is WPA protected but now it seems i cant connect to it for some reason

---

### Post by Ayuthia on 2008-06-27
See if this works:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```
It comes from this site:[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

That will perform just about the same thing whenever the ndiswrapper module is loaded.  So this should run when you start up.  Hope it works!

---

### Post by Silvernail on 2008-06-28
I am using a Compaq Presario and have somewhat the same problems.
```
 
dave@gadabout:~$ sudo modprobe -r b43 ssb bcm43xx ndiswrapper
[sudo] password for dave: 
dave@gadabout:~$ sudo depmod -ae
dave@gadabout:~$ sudo modprobe ndiswrapper
dave@gadabout:~$ lshw -C hardware
WARNING: you should run this program as super-user.
dave@gadabout:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:c5:d9:e0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
dave@gadabout:~$ 


```
Still no blue light. This went away when I upgraded to 8.04. Does the above look correct?

Dave

---

### Post by Silvernail on 2008-06-28
Moderator....
Please delete my above message. I meant to post under its own thread.
Sorry about that.

---

### Post by jlv7ferrets on 2008-07-07
Hey if anyone finds the answer the infinite problem, let me know step by step... i have been fighting with mine for the last 2 years, and until i know specifically what to do... sticking with lame-o windows... i thought about just swapping out my internal wifi card for one that miraculously works out of box... any suggestions... are greatly appreciated

---

