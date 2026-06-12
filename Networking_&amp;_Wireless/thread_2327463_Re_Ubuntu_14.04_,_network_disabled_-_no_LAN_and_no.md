---
title: "Re: Ubuntu 14.04 , network disabled - no LAN and no Wifi Connection"
date: 2016-06-11
forum: Networking &amp; Wireless
---

### Post by SathyaNG on 2016-06-11
Hello Good Morning ,

i was come up with new network issue in my Ubuntu dual boot with Win10 laptop. firstly LAN and WiFi was working fine in Win 10 boot.

if i boot in Ubuntu, i was unable to get my WiFi and LAN connected, i have reviewed all help topics but nothing did worked. here is some of outputs  when i select **Network from System Settings i was getting error as a Network configuration is not valid with version **i have done based on previous posts. i was unable to ping any IP address and any hosts.


Need you guys expertise to resolve this issue , Thanks in Advance - SatyaNG

```
sathyang@SathyaNG-VC:~$ tpconfig
The program 'tpconfig' is currently not installed.You can install it by typing:
sudo apt-get install tpconfig
  
sathyang@SathyaNG-VC:~$ sudo apt-get installtpconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automaticallyinstalled and are no longer required:
 linux-headers-3.13.0-58 linux-headers-3.13.0-58-generic
 linux-headers-3.13.0-61 linux-headers-3.13.0-61-generic
 linux-headers-3.13.0-63 linux-headers-3.13.0-63-generic
 linux-headers-3.13.0-64 linux-headers-3.13.0-64-generic
 linux-image-3.13.0-58-generic linux-image-3.13.0-61-generic
 linux-image-3.13.0-63-generic linux-image-3.13.0-64-generic
 linux-image-extra-3.13.0-58-generic linux-image-extra-3.13.0-61-generic
 linux-image-extra-3.13.0-63-generic linux-image-extra-3.13.0-64-generic
 python3-distro-info python3-pyinotify wine-compholiowine-compholio-amd64
 wine-compholio-i386:i386
Use 'apt-get autoremove' to remove them.
The following NEW packages will beinstalled:
 tpconfig
0 upgraded, 1 newly installed, 0 to removeand 64 not upgraded.
Need to get 66.2 kB of archives.
After this operation, 169 kB of additionaldisk space will be used.
Err [http://archive.ubuntu.com/ubuntu/trusty/universe](http://archive.ubuntu.com/ubuntu/trusty/universe) tpconfig amd64 3.1.3-15
 Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetchhttp://archive.ubuntu.com/ubuntu/pool/universe/t/tpconfig/tpconfig_3.1.3-15_amd64.deb  Temporary failure resolving'archive.ubuntu.com'
 
E: Unable to fetch some archives, maybe runapt-get update or try with –fix-missing?
```
 
```
sathyang@SathyaNG-VC:~$ sudo lshw -C network
 *-network               
      description: Wireless interface
      product: AR9285 Wireless Network Adapter (PCI-Express)
      vendor: Qualcomm Atheros
      physical id: 0
      bus info: pci@0000:02:00.0
      logical name: wlan0
       version: 01
      serial: 74:2f:68:3d:02:80
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physicalwireless
      configuration: broadcast=yes driver=ath9k driverversion=3.13.0-78-genericfirmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
      resources: irq:17 memory:dea00000-dea0ffff
 *-network DISABLED
      description: Ethernet interface
      product: AR8151 v2.0 Gigabit Ethernet
      vendor: Qualcomm Atheros
      physical id: 0
      bus info: pci@0000:03:00.0
      logical name: eth0
      version: c0
      serial: 14:da:e9:32:8a:1c
      capacity: 1Gbit/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress vpd bus_master cap_list ethernetphysical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=atl1cdriverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
      resources: irq:17 memory:de000000-de03ffff ioport:b000(size=128)
```
  
```
sathyang@SathyaNG-VC:~$ sudo ifconfig eth0up
sathyang@SathyaNG-VC:~$ sudo lshw -C network
 *-network               
      description: Wireless interface
      product: AR9285 Wireless Network Adapter (PCI-Express)
      vendor: Qualcomm Atheros
      physical id: 0
      bus info: pci@0000:02:00.0
      logical name: wlan0
      version: 01
      serial: 74:2f:68:3d:02:80
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list ethernet physicalwireless
      configuration: broadcast=yes driver=ath9kdriverversion=3.13.0-78-generic firmware=N/A latency=0 link=no multicast=yeswireless=IEEE 802.11bgn
      resources: irq:17 memory:dea00000-dea0ffff
 *-network
      description: Ethernet interface
      product: AR8151 v2.0 Gigabit Ethernet
      vendor: Qualcomm Atheros
      physical id: 0
      bus info: pci@0000:03:00.0
      logical name: eth0
      version: c0
      serial: 14:da:e9:32:8a:1c
      capacity: 1Gbit/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress vpd bus_master cap_list ethernetphysical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=atl1cdriverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
      resources: irq:47 memory:de000000-de03ffff ioport:b000(size=128)
```

nothing worked out till now.. any suggestions please ... Thanks, SathyaNG

---

### Post by jeremy31 on 2016-06-11
*Thread moved to **Networking & Wireless**.*

What happens if you ```
iwlist scan
```
Does it have any output?

---

### Post by SathyaNG on 2016-06-12
here is the output :

```
sathyang@SathyaNG-VC:~$ iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Failed to read scan data : Network is down


sathyang@SathyaNG-VC:~$ sudo ifconfig eth0 up
sathyang@SathyaNG-VC:~$ sudo ifconfig wlan0 up
sathyang@SathyaNG-VC:~$ iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     No scan results
```

Note: Noticed when i try to create new network connection, i was not able to save any new network connection, when i restart the network manager, i was getting error saying Ubuntu experienced problem.

---

### Post by jeremy31 on 2016-06-12
Can you get the wireless script to the computer and run it?  See [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385) for instructions on how to get it with no internet access

What is the result of ```
dpkg -l | grep libnl
```

---

