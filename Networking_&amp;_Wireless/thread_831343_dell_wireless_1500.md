---
title: "dell wireless 1500"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by s1337m on 2008-06-16
ive installed ndiswrapper with my drivers (bcm43xx), and can detect the networks.  however, i cannot connect to those networks.  i used the following sites:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=574501](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=574501)

i got this card to work a while back under fedora core, but have decided to switch to ubuntu (ive heard good things).  anyway, here is some output


sean@sean-laptop:~$ sudo /sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:c5:4a:16:69  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe4a:1669/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4221294 (4.0 MB)  TX bytes:646242 (631.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75400 (73.6 KB)  TX bytes:75400 (73.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:3d:0d:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11495 (11.2 KB)  TX bytes:17619 (17.2 KB)
          Interrupt:17 Memory:dfcfc000-dfd00000 


sean@sean-laptop:~$ sudo netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
sean@sean-laptop:~$ 


any help would be appreciated!

---

### Post by CeBiff on 2008-06-16
Good luck!

---

### Post by Ayuthia on 2008-06-16
> **s1337m said:**
> ive installed ndiswrapper with my drivers (bcm43xx), and can detect the networks.  however, i cannot connect to those networks.  i used the following sites:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=574501](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=574501)

i got this card to work a while back under fedora core, but have decided to switch to ubuntu (ive heard good things).  anyway, here is some output


sean@sean-laptop:~$ sudo /sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:c5:4a:16:69  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe4a:1669/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4221294 (4.0 MB)  TX bytes:646242 (631.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75400 (73.6 KB)  TX bytes:75400 (73.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:3d:0d:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11495 (11.2 KB)  TX bytes:17619 (17.2 KB)
          Interrupt:17 Memory:dfcfc000-dfd00000 


sean@sean-laptop:~$ sudo netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
sean@sean-laptop:~$ 


any help would be appreciated!

Can you post the results of the following:
```
lshw -C network
lsmod |grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
uname -r
```

---

### Post by s1337m on 2008-06-16
> **Ayuthia said:**
> Can you post the results of the following:
```
lshw -C network
lsmod |grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
uname -r
```

sean@sean-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:3d:0d:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.100 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4a:16:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes


sean@sean-laptop:~$ lsmod |grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
ndiswrapper           192920  0 
ssb                    34308  1 b44
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd


sean@sean-laptop:~$ uname -r
2.6.24-19-generic

---

### Post by Ayuthia on 2008-06-16
> **s1337m said:**
> sean@sean-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:3d:0d:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.100 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


It looks like you are connected 192.168.1.100.  Is that the case?  Does ifconfig say the same thing?

---

### Post by s1337m on 2008-06-16
> **Ayuthia said:**
> It looks like you are connected 192.168.1.100.  Is that the case?  Does ifconfig say the same thing?

hm, it looks like i was connected wirelessly for that session (weird).  anyway, im on a wired connection now and cant connect to wireless.

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:3d:0d:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4a:16:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 module=ssb multicast=yes
sean@sean-laptop:~$ 
sean@sean-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:4a:16:69  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe4a:1669/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115862 (113.1 KB)  TX bytes:20962 (20.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72300 (70.6 KB)  TX bytes:72300 (70.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:3d:0d:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6161 (6.0 KB)  TX bytes:7123 (6.9 KB)
          Interrupt:17 Memory:dfcfc000-dfd00000 

sean@sean-laptop:~$

---

### Post by Ayuthia on 2008-06-16
If you disconnect the wired connection and do the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo dhclient -r wlan0
```and try to connect through wireless, does it work?

---

### Post by s1337m on 2008-06-17
> **Ayuthia said:**
> If you disconnect the wired connection and do the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
sudo dhclient -r wlan0
```and try to connect through wireless, does it work?

yes, i am connected now, but it took a LONG time to connect.  im going to reboot and see if its faster.

---

### Post by CeBiff on 2008-06-17
S1337M, why don't you do a favor to the people who are trying to help you and use the code tags?

Such little to ask when all you do is leach off of the help of the forum's kind members

Thn again, I don't expect much from someone with "1337" in their name

---

### Post by s1337m on 2008-06-17
> **s1337m said:**
> yes, i am connected now, but it took a LONG time to connect.  im going to reboot and see if its faster.


tried again, no luck :(

edit:  no luck with connection, though i waited about a minute.  the earlier connect took about 3 minutes.

---

### Post by manishanchan on 2008-06-17
I think the dell wireless products are good enough and they keep quality products.

---

### Post by s1337m on 2008-06-17
a slight update:  i was able to connect this morning, and the connection was fine for that session.  i rebooted, and couldn't connect.  any tips would be appreciated :)

---

### Post by Ayuthia on 2008-06-17
> **s1337m said:**
> a slight update:  i was able to connect this morning, and the connection was fine for that session.  i rebooted, and couldn't connect.  any tips would be appreciated :)

You might try changing channels on your router.  It could just be interference in the air that is affecting the wireless driver.

---

### Post by s1337m on 2008-06-17
> **Ayuthia said:**
> You might try changing channels on your router.  It could just be interference in the air that is affecting the wireless driver.

i dont think that is the issue;  im using the same drivers as i do on the my xp partition (which work great) and at the same location.

---

### Post by Ayuthia on 2008-06-17
> **s1337m said:**
> i dont think that is the issue;  im using the same drivers as i do on the my xp partition (which work great) and at the same location.

You could be right on that, but I am thinking that they software that is running the driver is different so it can produce different results.  I have seen that on my laptop, that I can get different results using ndiswrapper and using Windows.

---

### Post by s1337m on 2008-06-17
> **Ayuthia said:**
> You could be right on that, but I am thinking that they software that is running the driver is different so it can produce different results.  I have seen that on my laptop, that I can get different results using ndiswrapper and using Windows.

no luck :(

---

### Post by s1337m on 2008-06-18
UPDATE:  Looks like its a problem connecting to a WPA network.  I can connect to an unprotected network easily.  I have wpasupplicant installed, what sort of config issues should I be looking at?

---

