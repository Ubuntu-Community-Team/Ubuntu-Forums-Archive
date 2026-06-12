---
title: "[SOLVED] Problems with RaLink RT2561/RT61 802.11g PCI"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Deutscher Alex on 2008-06-18
Ok so I have my (lspci says):
```
03:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```
wireless adapter more or less working, but the connection to my wireless network dies frequently. To reconnect, I simply have to reselect my wireless network from the network manager 'thing', and it (instantly) reconnects, so I know for certain that it isn't a problem with my network. I did the howto found [here]("http://ubuntuforums.org/showthread.php?t=564419") (I installed the vendor's newest driver), but that didn't solve the problem.... Please help >.>;

---

### Post by Deutscher Alex on 2008-06-18
bump? I need a solution.

---

### Post by Ayuthia on 2008-06-18
Was this issue with the original driver that came with Ubuntu?

EDIT:When it goes down, take a look at dmesg.  Just open a Terminal window and type dmesg at the prompt.  There should be some messages about your wireless at the end of the listing.

---

### Post by Deutscher Alex on 2008-06-19
> **Ayuthia said:**
> Was this issue with the original driver that came with Ubuntu?


what driver would that be? I'm pretty new to ubuntu

---

### Post by Ayuthia on 2008-06-19
> **Deutscher Alex said:**
> what driver would that be? I'm pretty new to ubuntu

The driver should have been rt61pci.  I just installed that card into my desktop and it worked right out of the box.  Of course, I have only done this this afternoon and I am still only less than a meter from my router.

Can you post the results of:
```
lsmod |grep -i -e rt61pci -e ndiswrapper
lshw -C network
ndiswrapper -l
```

---

### Post by Deutscher Alex on 2008-06-19
yes i had/have rt61pci, which was having the problem, and i installed rt61

```
:~$ lsmod |grep -i -e rt61pci -e ndiswrapper
ndiswrapper           192920  0 
rt61pci                25472  0 
rt2x00pci              11264  1 rt61pci
rt2x00lib              22528  4 rt73usb,rt2x00usb,rt61pci,rt2x00pci
mac80211              165652  4 rt2x00usb,rt61pci,rt2x00pci,rt2x00lib
eeprom_93cx6            3200  1 rt61pci
usbcore               146028  11 ndiswrapper,rt73usb,rt2x00usb,hci_usb,usbhid,lirc_mceusb2,usb_storage,libusual,ehci_hcd,uhci_hcd

```
```
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b:fc:d0:92:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:14:a5:31:40:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=***.***.*.* latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:c0:a8:f3:06:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=***.***.*.* multicast=yes wireless=IEEE 802.11g

```
```
:~$ ndiswrapper -l
rt61 : driver installed
	device (1814:0301) present (alternate driver: rt61pci)

```

---

### Post by Ayuthia on 2008-06-19
> **Deutscher Alex said:**
> yes i had/have rt61pci, which was having the problem, and i installed rt61

```
:~$ lsmod |grep -i -e rt61pci -e ndiswrapper
ndiswrapper           192920  0 
rt61pci                25472  0 
rt2x00pci              11264  1 rt61pci
rt2x00lib              22528  4 rt73usb,rt2x00usb,rt61pci,rt2x00pci
mac80211              165652  4 rt2x00usb,rt61pci,rt2x00pci,rt2x00lib
eeprom_93cx6            3200  1 rt61pci
usbcore               146028  11 ndiswrapper,rt73usb,rt2x00usb,hci_usb,usbhid,lirc_mceusb2,usb_storage,libusual,ehci_hcd,uhci_hcd

```
```
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b:fc:d0:92:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:14:a5:31:40:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.6 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:c0:a8:f3:06:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.7 multicast=yes wireless=IEEE 802.11g

```
```
:~$ ndiswrapper -l
rt61 : driver installed
	device (1814:0301) present (alternate driver: rt61pci)

```
You might see if this works:
```
sudo modprobe -r rt61pci ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```and see if it works.  If so, you will need to blacklist the rt61pci driver:
```
echo blacklist rt61pci|sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by Deutscher Alex on 2008-06-19
ok my internet just died again =(
dmsg gave me this:
```
[  251.833003] wlan0: Initial auth_alg=1
[  251.833010] wlan0: authenticate with AP 00:0f:b5:b6:ab:78
[  251.835776] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=2 status=0)
[  251.835782] wlan0: replying to auth challenge
[  251.838865] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=4 status=0)
[  251.838869] wlan0: authenticated
[  251.838873] wlan0: associate with AP 00:0f:b5:b6:ab:78
[  251.840982] wlan0: RX AssocResp from 00:0f:b5:b6:ab:78 (capab=0x411 status=0 aid=4)
[  251.840986] wlan0: associated
[  251.843177] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  268.344296] wlan0: no IPv6 routers present
[ 1631.375813] wlan0: deauthenticate(reason=3)
[ 1633.942145] wlan0: Initial auth_alg=1
[ 1633.942153] wlan0: authenticate with AP 00:0f:b5:b6:ab:78
[ 1633.944688] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=2 status=0)
[ 1633.944692] wlan0: replying to auth challenge
[ 1633.947939] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=4 status=0)
[ 1633.947943] wlan0: authenticated
[ 1633.947945] wlan0: associate with AP 00:0f:b5:b6:ab:78
[ 1633.950184] wlan0: RX AssocResp from 00:0f:b5:b6:ab:78 (capab=0x411 status=0 aid=4)
[ 1633.950189] wlan0: associated
[ 1633.951821] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```
I'm connected through wlan1 though.....

eh... it appears i blacklisted rt61 instead of rt61pci when i installed the new driver (rt61) last night... so i took rt61 off of the blacklist just now. Do I have to reboot my computer or something?

---

### Post by Ayuthia on 2008-06-19
> **Deutscher Alex said:**
> ok my internet just died again =(
dmsg gave me this:
```
[  251.833003] wlan0: Initial auth_alg=1
[  251.833010] wlan0: authenticate with AP 00:0f:b5:b6:ab:78
[  251.835776] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=2 status=0)
[  251.835782] wlan0: replying to auth challenge
[  251.838865] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=4 status=0)
[  251.838869] wlan0: authenticated
[  251.838873] wlan0: associate with AP 00:0f:b5:b6:ab:78
[  251.840982] wlan0: RX AssocResp from 00:0f:b5:b6:ab:78 (capab=0x411 status=0 aid=4)
[  251.840986] wlan0: associated
[  251.843177] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  268.344296] wlan0: no IPv6 routers present
[ 1631.375813] wlan0: deauthenticate(reason=3)
[ 1633.942145] wlan0: Initial auth_alg=1
[ 1633.942153] wlan0: authenticate with AP 00:0f:b5:b6:ab:78
[ 1633.944688] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=2 status=0)
[ 1633.944692] wlan0: replying to auth challenge
[ 1633.947939] wlan0: RX authentication from 00:0f:b5:b6:ab:78 (alg=1 transaction=4 status=0)
[ 1633.947943] wlan0: authenticated
[ 1633.947945] wlan0: associate with AP 00:0f:b5:b6:ab:78
[ 1633.950184] wlan0: RX AssocResp from 00:0f:b5:b6:ab:78 (capab=0x411 status=0 aid=4)
[ 1633.950189] wlan0: associated
[ 1633.951821] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```
I'm connected through wlan1 though.....

eh... it appears i blacklisted rt61 instead of rt61pci when i installed the new driver (rt61) last night... so i took rt61 off of the blacklist just now. Do I have to reboot my computer or something?

You can if you want to, but I don't think think that it will change anything because ndiswrapper is using the rt61 driver so the actual rt61 driver is not directly used in the kernel.

Can you post your lshw -C network after you reload ndiswrapper?
```
sudo modprobe -r rt61pci ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
lshw -C network
```I just want to see if ndiswrapper is being used or not.

---

### Post by Deutscher Alex on 2008-06-19
alright, it appears ndiswrapper is being used:
```
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1b:fc:d0:92:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:14:a5:31:40:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt61 driverversion=1.52+Airlink101,06/04/2005, 1.00 ip=***.***.*.* latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:c0:a8:f3:06:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=***.***.*.* multicast=yes wireless=IEEE 802.11g

```

Ok NOW I'm confused. According to this, we've been messing with wlan0. Under Network Settings, I've configured it to connect through wlan1.
Hmm so here's the deal between wlan0 & 1. My computer came with a built in wireless card which (in Vista) wasn't powerful enough to pick up our router's signal. So I built in a different wireless card that was. Now that I think about it, I'm pretty sure the RaLink card is the one that came built into my computer.... 

Ok crap. I tried connecting through wlan0; it failed. It seems I've only been messing with the wireless card I wasn't using....
Which explains why the problem persists >.>


EDIT: >.> I feel really dumb now. I got the wlan0 configuration to work, so I'll see how that works out. If it has the same problem, I'll bump

---

### Post by Deutscher Alex on 2008-06-20
ok I declare my stupidity solved. Can only moderators change the [ubuntu] to [SOLVED]?

---

### Post by Deutscher Alex on 2008-06-28
For future reference:

I had to reinstall Ubuntu because of the whole -19 kernel upgrade problem with nVidia drivers, so I just went through this problem again.
The rt61pci driver is truly problematic and needs to be replaced with rt61; it wasn't just me selecting the wrong wlan configuration

---

### Post by Ozlanthos on 2010-10-29
I'm using Kubuntu 10.04. With my previous installations of Ubuntu/Kubuntu I didn't have any issues with my wireless card detecting or connecting to the internet via wireless DSL, but for some reason 10.04 detects the network but won't connect to the internet...(btw I am not really a big linux user but this issue is causing me not to use it at all)....Any help?

-Oz

---

