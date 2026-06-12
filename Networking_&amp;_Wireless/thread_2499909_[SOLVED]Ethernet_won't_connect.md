---
title: "[SOLVED]Ethernet won't connect"
date: 2024-08-14
forum: Networking &amp; Wireless
---

### Post by corkncat on 2024-08-14
I'm using Ubuntu Server 22.04.4 LTS. Ethernet won't connect but when I added a WiFi card I can connect. I opened a terminal and type: "sudo lshw -C network" 
This is what I got concerning my ethernet: 
*-network DISABLED
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: c0
       serial: 90:2b:34:34:d0:db
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=5.15.0-117-generic latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:f7c00000-f7c3ffff ioport:d000(size=128)

How do I enable it? I checked the BIOS and it's enabled there.
Thanks

---

### Post by corkncat on 2024-08-18
This is long winded but this explains what happened in detail. My hope is that it will help someone else.
I was using an old Dell pc from the Windows Vista days to serve as my home NAS. It had Ubuntu Server 22.04,
4GB RAM, 1 SSD with the OS and 3 HDD for storage. The hardware was no longer working properly so I bought a
 used mobo, cpu & RAM combo and a new case. I then transferred my drives to the new hardware. It booted
 fine but had no internet. I installed a wifi card and had access but ethernet port was disabled. After much
 research this is how I got it working.
 
 Static IP

In order to setup a network interface with a static IP, we have to create its corresponding file:

$ sudo vim /etc/systemd/network/00-enp3s0.network

With this content:

[Match]
Name=enp3s0

[Network]
Address=192.168.1.27/24
Gateway=192.168.1.1
DNS=192.168.1.1

DHCP

With DHCP we follow the exact process above and change the configuration file content to:

[Match]
Name=enp3s0

[Network]
DHCP=yes

Restarting the service

Once we are done with our changes, it is required that we restart our service

$ sudo systemctl restart systemd-networkd

This is the link to where I found this info: [https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd](https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd)

---

