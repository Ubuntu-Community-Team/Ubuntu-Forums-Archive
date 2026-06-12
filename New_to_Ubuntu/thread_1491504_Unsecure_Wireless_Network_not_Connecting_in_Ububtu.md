---
title: "Unsecure Wireless Network not Connecting in Ububtu 10.04"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by kalairajan on 2010-05-23
HI 

     I am using Ubuntu 10.04 64 bit on dell studio 1535 , I am able to connect to secure wireless network , but when i try to connect to Unsecure wireless or other wifi hotspot , it shows message like , unable to get IP address , but the same work with my friends computer running windows OS , I browsed the forum and went through some threads where they suggested to use wicd , it didnt help .. any recommendation on how i should be troubleshooting this is appreciated, please let me know?

Thanks
kalairajan

---

### Post by kalairajan on 2010-05-23
I am attaching some of my system configuration information 

 ```
Network controller: Broadcom Corporation BCM4312 802.11b/g 

 mumbo@mumbo-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:63fb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


mumbo@mumbo-laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2c:85:9e:ec
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:e8:ee:e6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.17 latency=0 multicast=yes
       resources: irq:30 memory:fc500000-fc50ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


mumbo@mumbo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

mumbo@mumbo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   

          Link Quality:5  Signal level:212  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

mumbo@mumbo-laptop:~$ uname -a
Linux mumbo-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
mumbo@mumbo-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
```

---

### Post by kalairajan on 2010-05-23
I also tried the different dhcp preferences in wicd , i tried automatic , dhcpcd , dhclient , still the same issue , i enabled the debug option in advanced setting in wicd , but i do not know the location of the logs ..any clues ?

---

