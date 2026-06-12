---
title: "No Internet after changing some settings. URGENT"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by djbenny on 2007-05-22
i had to get my sound working, and i used this to do that but then the internet went.

> 
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1 ro acpi=off

#### DELETED STUFF #####

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-26-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot


i also had to reconfigure the xserver then i rebooted and it goes on ubuntu 7.04 now with sound but no internet!


Help Please, ben

---

### Post by djbenny on 2007-05-22
does no-one know what the problem is?

---

### Post by djbenny on 2007-05-22
*-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:4b:14:3d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-5 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:d2000000-d201ffff ioport:3000-301f irq:17
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d2200000-d2200fff irq:17


info bout network devices if that helps

---

### Post by chili555 on 2007-05-22
Which internet? The wired or wireless? Just guessing, I'll assume wireless.

Does it take a long time to boot? And when it boots, wireless is not active? This may be related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/108152](https://bugs.launchpad.net/ubuntu/+bug/108152)

Please try:```
sudo modprobe ipw3945
sudo ifup eth1
```

On a modern machine like you have, you absolutely should not have to disable ACPI to get sound. I suggest you keep searching for sound fixes.

---

### Post by djbenny on 2007-05-22
no wired, it doesnt htake that long to boot

---

### Post by chili555 on 2007-05-22
This is from your *lshw:*```
link=no
```Is the cable connected? Is it faulty? Is the router or switch working correctly?

What happens when you do:```
sudo modprobe e1000
sudo ifup eth0
```Thanks.

---

### Post by djbenny on 2007-05-22
it was working fully before i edited the menu.lst file.

and give me 5 mins and i'll post the output

---

### Post by djbenny on 2007-05-22
responses

ben@laptop:~$ sudo modprobe e1000
Password:
ben@laptop:~$ sudo ifup eth0
ifup: interface eth0 already configured

---

### Post by djbenny on 2007-05-22
what should i do?

---

### Post by chili555 on 2007-05-22
Does:```
sudo ethtool eth0
```show link detected: yes? If not, it's the cable or router.

---

### Post by djbenny on 2007-05-22
well its working on vista ok and on the generic version of ubuntu which the menu.lst hasnt been edited.

i will post responce in a few mins..

---

### Post by djbenny on 2007-05-22
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes


also on bootup there is a message:

Failed to allocate memory recourse #6 with a load of numbers.

---

### Post by djbenny on 2007-05-22
it says link detected so i do not understand whats wrong

---

### Post by chili555 on 2007-05-22
What is the outcome of:```
sudo dhclient eth0
```Thanks.

---

### Post by djbenny on 2007-05-22
ben@laptop:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:4b:14:3d
Sending on   LPF/eth0/00:16:36:4b:14:3d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by djbenny on 2007-05-22
any answers?

---

### Post by djbenny on 2007-05-22
need to know urgently! :(

---

### Post by djbenny on 2007-05-22
bump

---

### Post by srt4play on 2007-05-22
Are you behind a router?

If you set your IP address statically does it work?

---

### Post by djbenny on 2007-05-22
i do not know i am at university on the university network...

---

### Post by djbenny on 2007-05-22
is this not solvable?

---

### Post by djbenny on 2007-05-22
my friend is going to take a look at it this weekend but any help be great!

---

### Post by djbenny on 2007-05-23
i have tried everything i can think of and te nert still is not working :(

---

### Post by djbenny on 2007-05-23
bump.

---

### Post by djbenny on 2007-05-24
i take it there are no answers to this question.

---

### Post by djbenny on 2007-05-29
needanswer desperate!

---

