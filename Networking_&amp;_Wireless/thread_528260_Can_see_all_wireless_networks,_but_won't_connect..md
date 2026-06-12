---
title: "Can see all wireless networks, but won't connect."
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by wilsonisme on 2007-08-17
Hey guys,

Trying to install Ubuntu on my little sister's windows machine she screws up weekly. Everything is fine except I can't get it to work with our wireless network. I have tried the linksys wireless G PCI card and the usb network adapter, both exhibit the same problem:

They are detected and I can see the list of all wireless networks near me. However, when I go to connect to ours, it hangs on a message like "preparing X (wireless device) for use with X (wireless network). Something along those lines. Anyway, I have tried with both WPA enabled and no network security, it does the same thing regardless, so it isn't a security issue. 

I also tried connecting to my neighbors wireless network briefly as it is not secured, same problem.

I am using Ubuntu 7.04.

Any ideas?
Thanks!
Grant

---

### Post by amoose on 2007-08-17
I'm having the same problem: gusty, dell d630.  With mine, it will connnect, but only after many, many tries.

---

### Post by kevdog on 2007-08-17
Please post the following

lspci -nn
lshw -C network

Did you install any drivers for the wireless card???

---

### Post by amoose on 2007-08-17
00:00.0 Host bridge [0600]: Intel Corporation Mobile Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation Mobile IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation Mobile SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

---

### Post by amoose on 2007-08-17
iskra@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:7f:f9:0f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.1mp firmware=14.2 1:0 () ip=192.168.2.2 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:de:0a:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes

---

### Post by kevdog on 2007-08-17
Please also post
lshw -C network 
iwlist scan

---

### Post by amoose on 2007-08-17
iskra@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:7f:f9:0f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.1mp firmware=14.2 1:0 () ip=192.168.2.2 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:de:0a:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:3F:E8:5F
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=49/100  Signal level=-79 dBm  Noise level=-79 dBm
                    Extra: Last beacon: 92ms ago

---

### Post by kevdog on 2007-08-17
Lets just take baby steps, and try to do everything at the command line so we can generate some debugging output:

```

sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "belkin54g"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

```

---

### Post by amoose on 2007-08-17
iskra@ubuntu:~$ sudo ifconfig eth1 down
[sudo] password for iskra:
iskra@ubuntu:~$ sudo ifconfig eth1 up
iskra@ubuntu:~$ iwconfig eth1 essid "belkin54g"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Operation not permitted.
iskra@ubuntu:~$ sudo iwconfig eth1 essid "belkin54g"
iskra@ubuntu:~$ iwconfig eth1 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.
iskra@ubuntu:~$ sudo iwconfig eth1 mode Managed
iskra@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:7f:f9:0f
Sending on   LPF/eth1/00:1b:77:7f:f9:0f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 960092336 seconds.
iskra@ubuntu:~$

---

### Post by kevdog on 2007-08-17
Ok -- so it works now right???
 You were issued an IP address of 192.168.2.2.  

Can you ping the router or connect to the internet???

---

### Post by amoose on 2007-08-17
Yes I'm responding from the machine which is giving me the trouble.  My problem is that I need to try to connect several times - maybe 3 or 4 before it actually does so.  This is true regardless of whether the network is encrypted, password protected or not.  It's also true regardless of whether more than one network is detected - although that's only been the case once. Generally I can detect multiple networks; I guess we're in the wireless age...

What's nettlesome is that this process of trying and re-trying takes about 20 minutes.  I've run linux on laptops for a while and have never seen this before.  In the past, either I couldn't connect at all because I didn't have the proper driver or I had no difficulties.

Time and future help is very greatfully appreciated!

---

### Post by amoose on 2007-08-17
Yes I'm responding from the machine which is giving me the trouble.  My problem is that I need to try to connect several times - maybe 3 or 4 before it actually does so.  This is true regardless of whether the network is encrypted, password protected or not.  It's also true regardless of whether more than one network is detected - although that's only been the case once. Generally I can detect multiple networks; I guess we're in the wireless age...

What's nettlesome is that this process of trying and re-trying takes about 20 minutes.  I've run linux on laptops for a while and have never seen this before.  In the past, either I couldn't connect at all because I didn't have the proper driver or I had no difficulties.

Time and future help is very greatly appreciated!

---

### Post by kevdog on 2007-08-17
Sounds possibly like a driver problem.  I dont know a lot about the ipw driver for intel -- I know its not bug free.  You said you had a Broadcom or Linksys card you were trying.  We could try to configure that if you want and see if it makes any difference.

If you need to type those commands on the previous page alot, put them in a script file, make it executable, put it in a directory such as ~/bin.  Make sure ~/bin is in your path (.bashrc file). That way you can just type the name of the script file once to execute all those commands.

---

### Post by amoose on 2007-08-17
I'm willing to try (re-)configuring so long as I will be able to get back to the current situation.  Although far from ideal, connecting to the web is important enough that I'm willing to wait 20 minutes or whatever it takes as opposed to not being able to connect at all.

Again, thank you.

---

### Post by kevdog on 2007-08-17
Ok stick the linksys card in and then post:

lshw -C network
lspci -nn

We're not going to destroy what you already have working right now.  In fact it will help us, since I think we are going to have to install ndiswrapper.  Im willing to bet $100 that the linksys card has a broadcom chipset.

---

### Post by amoose on 2007-08-17
I'm sorry, I don't think I understand.  The only card I have is the one that came with the laptop.  Are you getting that from the lspci?

---

### Post by kevdog on 2007-08-17
> I have tried the linksys wireless G PCI card and the usb network adapter, both exhibit the same problem

Thought you had a few wireless devices??

---

### Post by amoose on 2007-08-17
You, very generously, must be helping more than one of us at a time.  I didn't write that.  In any case, I'm willing to try any ideas you have.

---

### Post by amoose on 2007-08-18
Anyone else??

---

