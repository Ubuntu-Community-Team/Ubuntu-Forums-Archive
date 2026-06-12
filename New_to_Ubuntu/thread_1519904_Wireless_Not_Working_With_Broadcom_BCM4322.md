---
title: "Wireless Not Working With Broadcom BCM4322"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by tony_tj3 on 2010-06-28
After a few days of trying to get this card working right I am still stuck with no wireless. I have gone through many of the solutions posted around here and tried the broadcom method with no luck. I am able to see the wireless networks menu but no networks show up, when manually entering the network information, it will just work and then proceed to give up after a few minutes.

Laptop model is HP DV4-1417ca
lspci shows my device as "Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)"

I appreciate any help that you guys have to offer.

---

### Post by macgeek417 on 2010-06-28
Do you have any other methods of connecting to the internet to use for setting up the WiFi? If so, you can do what I did with my old laptop.

Here is what I did:

* Connect to the internet
* Upen up the "Hardware Drivers" application
* Select the fwcutter driver
* Install it
* ???
* PROFIT!

That worked for me.

Hope this helps!

:)

---

### Post by tony_tj3 on 2010-06-29
I tried that one already, the driver shown to me by default is broadcom STA wireless driver. Once installed it shows that i have a wireless card, but cant use it. I'm rather stumped

---

### Post by Bucky Ball on 2010-06-29
Tony Tj3, you have a picture of Jaco as your avatar. Rock on!

Anyhow, I digress. Have you set it up correctly in System->Administration->Network?

You have that set with the correct ESSID, security key, Configuration = Auto Config (DHCP), Enable roaming = disabled?

The above is if you are getting an IP from your router and ESSID and security key need to match your routers. That is set up correctly too? Do you know its IP? If so you can ping it?

If you are running static IP you need to enter that in here instead (Configuration = Static).

Also, and you've probably done this, get online with a cable, terminal and:

```
 sudo apt-get update
```then

```
 sudo apt-get upgrade
```

---

### Post by anewguy on 2010-06-29
I think you do most if not all of this configuring when setting up the connection in network manager now.  Be sure you have "Enable Wireless" checked in network manager.  Can you see any wireless networks?  Is the network you want to connect to broadcasting the ESSID (network name) or is it what is considered a "hidden" network?

It might also help to post the outputs of the following back here:

sudo lshw -C network

iwconfig



Dave ;)

---

### Post by tony_tj3 on 2010-06-29
update & upgrade are all done previously. And I love Jaco, he's a personal hero.

I have done the manual configuration just as you said already, but it will just give me the connecting message only to give up ~30 seconds later. I have also disabled security on the router, with no change in the connection fail.

Here are the outputs you've asked for:

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:f9:e9:84
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:d8500000-d8503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:ae:d2:e6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.195 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:3000(size=256) memory:d2410000-d2410fff(prefetchable) memory:d2400000-d240ffff(prefetchable) memory:d2420000-d243ffff(prefetchable)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

All this help is greatly appreciated, I'd hate to have to put windows back on this lappy

---

### Post by tony_tj3 on 2010-06-29
I just to mention as well, when security is enabled, it will perpetually give me the "authentication is required by wireless network". Also scanning with eth1 (should be wifi) gives the result that the interface doesn't scan

iwlist eth1 scan
eth1      Interface doesn't support scanning.

---

### Post by tony_tj3 on 2010-06-29
Issue was solved. Wasn't a software issue at all, the wireless card on/off toggle was broken. Opening up the laptop and poking around got it all running right as rain :)

---

### Post by Bucky Ball on 2010-06-29
Good news! Please mark as solved from thread tools and yes Jaco is hero of mine. Fretless bass player myself.

---

