---
title: "trying to set up usb wifi"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by fattysfinest on 2008-01-13
Hi all, Ive been trying to get the wireless working on this laptop. Acer Travelmate 290.
It has a built in card, Intel 2100, after a couple of weeks of trying to get this to work, I,ve  decided it might be easier to use  mt trend net TEW424UB H/W:3. OR. usb .
Ive downloaded the driver to my desk top but can't get nswrapper to work.
I am using Ubuntu 7.04 and wicd for my network manager.
I dont care how but I need wireless. The kind I get on windows that shows available hotspots.
Heres where I am, I thought I blacklisted the 2100 but I guess I screwed that up too, Thanks for any help! this is frustrating
 
bb@bb-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
bb@bb-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:10:fe:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.10.105 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:c000-c0ff iomemory:e0001000-e00010ff irq:10
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@01:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:03:f7:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: iomemory:e0000000-e0000fff irq:10
bb@bb-laptop:~$ +sudo cat /etc/network/interfaces
bash: +sudo: command not found
bb@bb-laptop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp


bb@bb-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
bb@bb-laptop:~$  sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by videodrome on 2008-01-13
I was unable to get my intel 2200 internal wifi card to work on my acer travelmate 290. I had to buy a ralink card on ebay and it worked out of the box. The intel cards seem to conflict with the "radio switch off" issue. Does your dmesg throw a radio switch off error message, even if your switch is turned on?

In other words, if you type "dmesg" in the terminal and scroll up the wireless section, is there something there about the radio switch being turned off?

Loomis

---

### Post by fattysfinest on 2008-01-14
Thanks for the reply, I did as you said and found
eth1: Radio is disabled by RF switch. 
Do you know how to enable it or should I buy a new adapter(wifi) and what kind did you use on your Acer?
Thanks for the help!

---

### Post by fattysfinest on 2008-01-14
Thank You Videodrome! 
After doing a search on enabling  wifi switch I discovered that...I'm an IDIOT!
On the side of the laptop there is 2 jacks one for headphones and one for a mic. (little pics showing headphones and mic). Beside that is a switch with a little pic showing what I thought was a mic. On closer inspection I see that its supposed to be an antenna! I did think it was strange that there would be a switch for turning the mic on and off but never gave it another thought. Well I turned on the wifi switch and I can now see some signals! (still can't seem to connect but at least its a start!)
I'm still kicking myself for wasting over two weeks working on a non  existent  problem. Thanks again for turning on the light!
Brian

---

