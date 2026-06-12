---
title: "no wireless since Hardy upgrade..."
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by ish666 on 2008-06-24
Recently up graded to Hardy and lost wireless. Is an ACER travelmate 2450 laptop

Have tried troubleshooting guides and no luck. Please help. Thanks

ish@ish-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ish@ish-laptop:~$ sudo lshw -C network
sudo: unable to resolve host ish-laptop
[sudo] password for ish: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:09:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:09:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:17:6d:af
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by pytheas22 on 2008-06-24
Did you have to do anything special to get the wireless to work in Gutsy?

If not, compiling the latest madwifi from source may help:
```

sudo apt-get install build-essential
wget http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.bz2?modtime=1202880171&big_mirror=0
tar-xvf madwifi*
cd madwifi*
make
sudo make install
```

then reboot and see if your card is recognized.

If that doesn't work, then you'll probably have to use ndiswrapper.

---

