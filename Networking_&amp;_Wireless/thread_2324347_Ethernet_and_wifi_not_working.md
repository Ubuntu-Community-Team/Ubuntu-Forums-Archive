---
title: "Ethernet and wifi not working"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by vishnu10 on 2016-05-13
I have a new Dell E7470 laptop. Installed ubuntu 14.04. The ethernet is not working. I am posting the outputs of some commands to help improve the suggestions.

```
# lspci | grep -i net

00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-LM (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)

# sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:e1100000-e1101fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Ethernet Connection I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       version: 21
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:e1200000-e121ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:4d:17:43:62:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.223 link=yes multicast=yes


# lsmod | grep -i e100   : This is giving no output at all.

# dmesg | grep e100
[    0.599550] pci 0000:02:00.0: reg 0x14: [mem 0xe1000000-0xe1000fff]
[    0.607199] pci 0000:00:1d.0:   bridge window [mem 0xe1000000-0xe10fffff]
[    0.757604] pci 0000:00:1d.0:   bridge window [mem 0xe1000000-0xe10fffff]
[    0.757635] pci_bus 0000:02: resource 1 [mem 0xe1000000-0xe10fffff]

# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

I have tried the above commands from the post at [http://ubuntuforums.org/showthread.php?t=2180335](http://ubuntuforums.org/showthread.php?t=2180335) and [http://ubuntuforums.org/showthread.php?t=2143039](http://ubuntuforums.org/showthread.php?t=2143039)

THE USB TETHERING IS WORKING AND I CAN TETHER MY PHONE TO LAPTOP AND ACCESS INTERNET

I am very confused as to what the problem is... Please help me. Thank you..

---

### Post by Bucky Ball on 2016-05-13
As you haven't gotten very far with this and as this seems to be a spanking new machine I would suggest you try 16.04 LTS. If you have very new hardware, this may fix the network issues, among other things that may crop up. 

If you can get online (wirelessly?) via tethering to your phone then things are working fine, though. Might be a setting somewhere. When you are online, please use these commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Post any errors here between code tags. (Please use code tags. See the green link in my signature at the bottom of this post if you're not sure how). Reboot. Signs of life?

---

### Post by jkeenan on 2016-05-14
Quite a few people have had a problem with 14.04 and network connections in the past few days.  Please see this thread:  [http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504).  If you go into System Settings/Network and get this error message:  The system network services are not compatible with this version" -- then try the solution outlined in Wild Man's post in that thread.

---

### Post by wildmanne39 on 2016-05-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

