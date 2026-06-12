---
title: "Newbie needs wireless setup help"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by hdtvman on 2010-07-07
As a background, I have several Windows machines and I am spoiled by the "plug it in & the system takes (care of) you" approach of most hardware, including usb network adapters.

I have wireless-n network that works fine on laptops and desktops with usb adapters.

I have not been so lucky with 3 different installs of Ubuntu 10.04.  The only wireless-n that works is on a newer HP laptop with wireless-n built-in.  I use WUBI to run Ubuntu "next to" my Windows 7 install.  Fortunately, when I did that, a popup announced that hardware drivers where available and I d/l-d and installed them and now that machine's install has wireless-n.

I have two other installs on desktops that I can not get working with wireless-n.  I think it's because the network drivers and/or setup is not correct.  But I have not been very successful reading and changing things so that the proper drivers and configuration changes are made.

I'm having trouble understanding some of the help offered in all the posts I look at because I have no frame of reference.

Is there a top down explanation of the process that is going on in the install so I can begin to understand how to deal with these issues?

Thanks, hdtvman

---

### Post by nothingspecial on 2010-07-07
The first thing you need to do is post what wireless cards you have

Open a terminal on the machines that are not working and type

```
sudo lshw -C network
```

Then copy and paste what it says into a new post in this thread

---

### Post by kevinatkins on 2010-07-07
For a particular wireless adapter to work, an appropriate driver is needed. If you're lucky (as in the case of your HP laptop), the necessary driver is available in the Ubuntu software repositories. Some wireless chipsets are still not supported properly - to use these, it is possible to use the windows drivers with a Linux compatibility 'wrapper' around them, using what is known as 'ndiswrapper'. 

To help further, we will need to know what wireless adapter you're using. If you're using a USB dongle, please could you open a terminal and post the results of the following command -
```
lsusb
```
If you're using an internal PCI wireless card, please could you post the results of -
```
lspci
```
We should then be in a position to steer you in the right direction.

---

### Post by hdtvman on 2010-07-07
Here is the result:

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///home/jp/Desktop/Screenshot.png[/IMG]

I need to ask how to capture the output from terminal and put it in the reply.

---

### Post by hdtvman on 2010-07-07
attached is the result of the sudo command string.

notice that the ip address of the wireless adapter is wrong.  it connceted to my network but did not get a IP address from the DCHP server.

---

### Post by hdtvman on 2010-07-07
This is better:

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:b5:f7:39
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:6f:5b:0d:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bgn

---

