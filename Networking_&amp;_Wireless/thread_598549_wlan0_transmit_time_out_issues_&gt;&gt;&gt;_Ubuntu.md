---
title: "wlan0 transmit time out issues &gt;&gt;&gt; UbuntuStudio (Gutsy x64)"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by ceeleelewis on 2007-10-31
I´ve been trying to resolve this issue by first using the ifup/ifdown commands but I get a response as if the device is not configured. 

I can´t seem to restart the network with the /etc/rc/networks restart command 
At this point my only option is to restart the machine. 
I´m using driver loader ( 2.6.22-14-generic #1 SMP) because I had issues installing ndiswrapper on both the generic and rt kernels ...although I would perfer to use the rt kernel for UbuntuStudio 7.10 (Gutsy) ..

Could there be a problem with the Windows drivers I using for this card? Or is there a way I can resolve this problem ... even if i have to restart the card rather than constantly my laptop when wireless times out... thanks in advance for any help in solving this issue. 

BTW: why is there no /etc/iftab in this version of the distro (UbuntuStudio 7.10 x64)? Is this because this a generic kernel? Or should I update my repos to get a standard x64 Ubuntu kernel?

(Below is the messages I receiving from kernel)  

clewis@OpenMuse:~$ tail -400 /var/log/messages | grep wlan0
Oct 31 12:07:41 OpenMuse kernel: [   43.566982] wlan0: New link status: Disconnected (0002)
Oct 31 12:07:42 OpenMuse kernel: [   46.336281] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 31 12:07:42 OpenMuse kernel: [   46.681284] wlan0: New link status: Connected (0001)
Oct 31 12:07:42 OpenMuse kernel: [   46.682638] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 31 12:08:27 OpenMuse dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Oct 31 12:08:42 OpenMuse dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 31 12:08:42 OpenMuse dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 31 12:08:42 OpenMuse dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 31 12:09:18 OpenMuse kernel: [  108.530826] NETDEV WATCHDOG: wlan0: transmit timed out
Oct 31 12:09:26 OpenMuse kernel: [  116.523653] NETDEV WATCHDOG: wlan0: transmit timed out

---

### Post by noob12 on 2007-10-31
In  7.10, /etc/iftab has been replaced by /etc/udev/rules.d/70-persistent-net.rules .  If you upgraded your /etc/iftab would have been converted during the upgrade.  

For the transmit timeout issue, can you post  the output of
```

lspci -nn

sudo lshw -C network

```

---

### Post by ceeleelewis on 2007-12-13
Sorry for being soooo late to respond (Had to put this on the back-burner). But here´s the output from lspci -nn

clewis@OpenMuse:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
05:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
05:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]


And here´s the output from sudo lshw -C network

clewis@OpenMuse:~$ sudo lshw -C network
[sudo] password for clewis:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:2c:d1:02
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:73:8c:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=driverloader driverversion=driverloader 2.39 - Linuxant Dr ip=192.168.42.32 latency=168 module=driverloader multicast=yes wireless=IEEE 802.11g
clewis@OpenMuse:~$ 



Again, sorry for being so late ... but I would really appreciate the help on this one thanks.

---

