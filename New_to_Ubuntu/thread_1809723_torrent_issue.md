---
title: "torrent issue"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by robgraves on 2011-07-22
I'm still fairly new to the linux world ~ 6 months or so (btw I've been loving using and learning linux in the last year), anyway i have a dual boot setup on my HP laptop which is only about a year old with Windows 7 and Ubuntu 11.04 64bit on it.
    i've noticed that in windows i'm using utorrent for torrent files and either transmission or qbittorrent in ubuntu.  well in windows the torrent, just always works, i can leave it alone and it will continue to download on its own, however in ubuntu, regardless of what torrent program i use, i frequently have times where when downloading a torrent, it will disconnect me from my internet connection, and i have reconnect and restart the download, so in ubuntu i fell like i'm always babysitting my torrents.  does anyone know why this is happening and what to do to remedy it? 

thank you

---

### Post by linuxman94 on 2011-07-22
Sounds like a driver issue. Are you using wireless or wired?

---

### Post by robgraves on 2011-07-22
wireless, so would i need to update that driver? and actually how would i do that?

---

### Post by linuxman94 on 2011-07-22
Yes more than likely you will have to install a driver.  But first we need to know details about the card.  Can you post the results of these commands?

```
sudo lshw -C network
iwconfig
```

---

### Post by robgraves on 2011-07-22
results of sudo lshw -C network
```
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:af:c6:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:12:35:19
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0010000-f001ffff

```results of iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Rob Graves Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 30:46:9A:64:B7:6C   
          Bit Rate=65 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:109   Missed beacon:0

```

---

### Post by linuxman94 on 2011-07-22
Try installing this package either by using synaptic or apt-get.

```
linux-backports-modules-wireless-generic
```

---

### Post by robgraves on 2011-07-22
didn't work, do i need to enable certain repositories for that? my output from terminal:
```
robgraves@ubuntu:~$ sudo apt-get install linux-backports-modules-wireless-natty-generic
[sudo] password for robgraves: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-natty-generic
robgraves@ubuntu:~$ 

```

---

### Post by linuxman94 on 2011-07-22
Oops the natty part shouldn't be there.  Edited my other post to change it.

---

### Post by robgraves on 2011-07-22
same issue:
```
robgraves@ubuntu:~$ sudo apt-get install linux-backports-modules-wireless-generic
[sudo] password for robgraves: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-generic
robgraves@ubuntu:~$ 

```

---

### Post by linuxman94 on 2011-07-22
Gahh! *face palm* I forgot you have to enable the backports repo.  The easiest way is to open software sources and go to the updates tab then check "Unsupported updates (natty-backports)"

---

### Post by robgraves on 2011-07-22
okay, i went into the software sources, enabled the unsupported natty backports, let it reload via the software sources(GUI) then went back to the terminal and ran sudo apt-get update just in case, then tried to do both of the aforementioned packages, both with same result. do i need to reboot?

---

### Post by robgraves on 2011-07-22
not sure, can't find that package

---

### Post by robgraves on 2011-07-22
any other suggestions?

---

### Post by linuxman94 on 2011-07-22
Sorry about the wrong packages, i didn't have access to a ubuntu computer at the time.  You should install this:

```
linux-backports-modules-cw-2.6.39-natty-generic
```

Make sure to reboot and then test again.

---

### Post by robgraves on 2011-07-22
cool, that one went through, maybe that will resolve the problem

---

