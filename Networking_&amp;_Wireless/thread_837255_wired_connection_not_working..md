---
title: "wired connection not working."
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by kienseng on 2008-06-22
i dont know what have i done to the networking things, just now i restart and i found that my wired connection is not working, now i can only online using XP, cant online in Ubuntu 8.04, even i type ifconfig in the terminal there, it only display loopback interface device and the wireless connection wl0, the wired connection should be in eth0, but somehow it doesnt show up, i seriously need help now....

---

### Post by djhk on 2008-06-22
I have been trying to get wireless to work.
At one point I lost my wired connection.
Rebooting in Recovery mode restored it.
Hope this works for you.

---

### Post by kienseng on 2008-06-22
but then at the recovery mode there which option should i choose?

---

### Post by kienseng on 2008-06-23
any other solution?? recovery mode seems like doesnt help much for me :(

---

### Post by kienseng on 2008-06-23
anyone can help with my problem?? pls.......

---

### Post by superprash2003 on 2008-06-23
please post your ifconfig output

---

### Post by kienseng on 2008-06-23
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65808 (64.2 KB)  TX bytes:65808 (64.2 KB)



wlan0     Link encap:Ethernet  HWaddr 00:1a:73:d0:15:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:fc000000-fc004000 


```

the eth0 driver is missing, and the Ubuntu are like not recognize it :(

---

### Post by kienseng on 2008-06-23
sorry for bump this thread so many times, but i really need help, i've posted the ifconfig, can anyone gives the solution please? :(

---

### Post by chili555 on 2008-06-23
Please post the wired ethernet portion of:```
sudo lshw -C network
```Thanks.

---

### Post by kienseng on 2008-06-23
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=20 mingnt=1
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:d0:15:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=10.83.76.121 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
network unclaimed, y it become like this??? :(

---

### Post by kienseng on 2008-06-24
anyone?? i really demand the solution....

---

### Post by kienseng on 2008-06-24
anyone??

bump...

---

### Post by kienseng on 2008-06-24
i typed lshpci at the terminal there, and it show me this
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


```
means the Ubuntu are still recognize my driver and hardware right?

---

### Post by pokipoki08 on 2008-06-24
```
gksudo gedit /etc/network/interfaces
```

Add & save [COLOR="Blue"]text in blue[/COLOR] below into file /etc/network/interfaces

```
[COLOR="Blue"]auto eth0
iface eth0 inet dhcp[/COLOR]
```

Run these commands at the terminal

```
sudo /etc/init.d/networking restart
ifconfig
```

If all is well, you should see an IP address in eth0.

Note : You can only have 1 active network connection at any time. So, it's either the wired (eth0) or the wireless (wlan0).

When you want to try connecting to wireless, disable or comment out those [COLOR="Blue"]text in blue[/COLOR] in /etc/network/interfaces

---

### Post by chili555 on 2008-06-24
Please do, in a terminal:```
sudo modprobe forcedeth
sudo lshw -C network
```Is your card still unclaimed? Now do:```
ifconfig
```Does your interface eth0 reappear?

If this fixes it, we will have to take some steps to make this, hopefully, permanent.

---

### Post by kienseng on 2008-06-24
i type already, but it show me this....
```
sudo: unable to resolve host Ubuntu
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.


```
why the Ubuntu failed to bring up eth0?

even in the ifconfig there the eth0 still not appear

---

### Post by kienseng on 2008-06-24
> **chili555 said:**
> Please do, in a terminal:```
sudo modprobe forcedeth
sudo lshw -C network
```Is your card still unclaimed? Now do:```
ifconfig
```Does your interface eth0 reappear?

If this fixes it, we will have to take some steps to make this, hopefully, permanent.

yes, it works, you sure this can work permanently?

---

### Post by kienseng on 2008-06-24
it works now, but everytime i restart it not working again and i need to type the command over again.

it show this error after i typed sudo modeprobe forcedeth
```
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'mkdir'

```

---

### Post by chili555 on 2008-06-24
Let's see:```
cat /etc/modprobe.d/blacklist
```I wonder if the failure of *forcedeth* to load is related. Let's fix problem #1 before we move forward. This:> sudo: unable to resolve host Ubuntubothers me, too. May I please see:```
cat /etc/hosts
```> you sure this can work permanently?Yes, indeed. Thanks.

---

### Post by kienseng on 2008-06-24
this is what it appear after i typed the cat /etc/modprobe.d/blacklist

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi



sudo apt-get install ndiswrapper-utils-1.9

mkdir ~/bcm43xx

```
and after i typed this  cat /etc/hosts, it show me this....
```
# The following lines are desirable for IPv6 capable hosts

```

---

### Post by chili555 on 2008-06-24
Please *sudo gedit /etc/modprobe.d/blacklist* and remove these lines:```
sudo apt-get install ndiswrapper-utils-1.9

mkdir ~/bcm43xx
```Proofread carefully, save and close. Use any text editor you have, such as kate, kwrite, nano or vim, if you do not have gedit.

*sudo gedit /etc/hosts* to make it look like this (a bit of guesswork here):```
127.0.0.1 localhost
127.0.1.1 Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Proofread carefully, save and close. Then do:```
sudo modprobe forcedeth
sudo /etc/init.d/networking restart
```Note any errors and tell us if your wired connection comes up.

---

### Post by kienseng on 2008-06-25
i'm sorry, but it doesn't work, the eth0 wired connection do come up, but after i restart then it not working again, i need the command all over again to get it working, is there a solution that i can get it automatically working when the cable is pluggled in?

---

### Post by chili555 on 2008-06-25
Please *sudo gedit /etc/modules* and add a single word on its own line:```
forcedeth
```Proofread, save and close. Use any other text editor if you don't have gedit; kwrite, kate, nano or vim will work as well.

Reboot. If your */etc/network/interfaces* file contains this:```
auto eth0
iface eth0 inet dhcp
```then you should be connected at boot.

---

### Post by kienseng on 2008-06-26
k thx.... problem solved...

---

### Post by altonbr on 2008-06-30
Why was this so hard to fix? And the use of the command line? Ugh.

---

### Post by Mark Anthony Degamo on 2008-06-30
hey i have the same problem. I'm using static ip and I have already provided my ip address, subnetmask and DNS but still i cannot browse the internet....i tried to install a network driver but i can't run the application to install the driver...I am using Asus P5SD2-VM.....can someone help me with this problem...please

---

