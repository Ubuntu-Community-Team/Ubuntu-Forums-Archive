---
title: "Wireless doesn't work Atheros AR5413 802.11abg NIC (rev 01)"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by ubuntpetbe on 2008-04-30
My wireless network card doesn't work
Already gone to documentation and tried a few things out:

Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)



(the following was done in the terminal)

desktop-ubuntu:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:11:2f:fc:9e:ae
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s


desktop-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

desktop-ubuntu:~$ sudo ppoeconf
sudo: ppoeconf: command not found

does somebody knows how to solve this?

---

