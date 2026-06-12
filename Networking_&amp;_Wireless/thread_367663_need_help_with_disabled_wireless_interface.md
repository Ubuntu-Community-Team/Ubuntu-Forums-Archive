---
title: "need help with disabled wireless interface"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by jeremyk on 2007-02-22
Hi,

I use Ubuntu edgy. I used several times the wireless connection. However for some reason, that I could not explain, the wireless connection is not available anymore. (My guess is that I tried, by mistake to use network-manager together with another wireless gui...)

network-manager does not allow wireless connection any more, even if 'Enable wireless' option is selected. 

To understand the situation, here is some information:

1- ifconfig gives:
eth0      Link encap:Ethernet  HWaddr 00:09:6B:D0:90:D3  
          inet addr:192.168.0.182  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fed0:90d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2531134 (2.4 MiB)  TX bytes:584033 (570.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17451 (17.0 KiB)  TX bytes:17451 (17.0 KiB)

(The wireless interfaces does not appear. It used to appear as eth1.)

2- lshw -C network gives:

  *-network:0 DISABLED    
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=prism2_pci multicast=yes
       resources: iomemory:f8000000-f8000fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:d0:90:d3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 ip=192.168.0.182 multicast=yes
       resources: iomemory:d0200000-d0200fff ioport:8000-803f irq:11

(The wireless interface is disabled).

3- less /etc/network/interfaces gives:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp


auto wlan0


My questions:

1- Can I delete the following lines:

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

from /etc/network/interfaces?

2- How can I enable again the wireless interface so that network-manager can work with it?

3- Which driver would be optimal for my wireless card?

Many thanks for answers.

Jeremy.

---

### Post by jeremyk on 2007-02-24
Any one, please?

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

