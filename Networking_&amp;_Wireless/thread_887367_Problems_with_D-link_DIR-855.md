---
title: "Problems with D-link DIR-855"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by AndyC_772 on 2008-08-12
Just bought a DIR-855 to replace my old 802.11g access point and it's thrown up a couple of problems :(

It's an 802.11n (draft 2.0) router with two separate radios: one 2.4 GHz and one 5 GHz. It therefore broadcasts two separate wireless networks with different SSIDs. I have both set to WPA/WPA2, hidden SSIDs, the 2.4 GHz network is set to be 802.11g/11n and the 5 GHz is 802.11n only.

My laptop is an Asus with an Intel 4965AGN card, using WiCD under Gutsy. I can connect to the 2.4 GHz network just fine, though I don't know whether it's using 11g or 11n. I'm using DHCP, and it takes about 10 seconds to get an address when it connects.

- I can't, however, connect to the 5GHz network. I can type the SSID into WiCD, see it come up in the list (marked as WPA2, which is correct), but when I try to connect it fails after taking ages 'Obtaining IP address'. Under XP it works fine and I can connect at 300 Mbps.

- Even on the 11g network, I can no longer quickly and reliably mount my NFS fileserver. I have eight shares on the NAS drive, and when I try to mount them I get:

andy@andy-ubuntu03:~$ sudo mount -a
[sudo] password for andy:
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
mount.nfs: mount to NFS server '192.168.0.201' failed: timed out, retrying
andy@andy-ubuntu03:~$ 

The drive DOES eventually mount and I can access it, but the timeouts are new. It used to mount all the shares in about 5 seconds with no error.

Any ideas please? Is it worth the hassle of upgrading to Hardy?

Ta
Andy

---

### Post by Crafty Kisses on 2008-08-12
Post the following output:
```
lshw -C network

```

---

### Post by AndyC_772 on 2008-08-12
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:49:30:10
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:8d:65:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.0.220 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

---

### Post by AndyC_772 on 2008-08-13
Just tried a wired connection, that suffers timeouts when trying to mount the NAS too - odd, since my laptop, DIR-855 and NAS all have Gbit interfaces.

---

### Post by AndyC_772 on 2008-08-25
OK, "final" update, really just for the benefit of anyone doing a search...

- the DIR-855 seems fine, it's the NAS that's upset for some reason :(
- from what I gather, the Intel wireless driver in Gutsy doesn't support 802.11n and nor does the one in Hardy.

My advice? Don't bother, stick to 802.11g and if you have a network that works, don't break it :(

---

### Post by Crafty Kisses on 2008-08-25
What happens if you try to ping a website?

---

### Post by AndyC_772 on 2008-08-25
It works fine when connected to the 11g network, and doesn't work at all when I try to connect to the 11n network.

---

