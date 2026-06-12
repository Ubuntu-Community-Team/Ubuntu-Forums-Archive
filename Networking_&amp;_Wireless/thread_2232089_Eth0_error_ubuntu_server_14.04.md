---
title: "Eth0 error ubuntu server 14.04"
date: 2014-06-29
forum: Networking &amp; Wireless
---

### Post by Martin_Hansen on 2014-06-29
Hello Everyone.
When i check on ifconfig -a eth0 doesn't show up even with ethernet cable inserted, but instead lo, p4p1 and wlan0 shows up.
my network card is: Broadcom netlink BCM57781 Gigabit Ethernet PCIe.
If further Info is needed go ahead and ask! :) .

---

### Post by chili555 on 2014-06-29
What do these commands tell us?```
sudo lshw -C network
ifconfig
dmesg | grep p4p1
```

Thanks.

---

### Post by Martin_Hansen on 2014-06-30
Sudo lshw -C network gives me:
```
*-network DISABLED
description: Ethernet interface
product: Netlink BCM57781 Gigabit Ethernet PCIe
vendor:  Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: p4p1
version: 10
serial: bc:5f:f4:8a:f1:07
capacity: 1Gbit/s
width: 64 bits
clock 33mhz
capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=sb latency=0 link=no multicast=yes port=twisted pair
resources: irq:16 memory:ea110000-ea11ffff memory:ea100000-ea10ffff memory:f7a00000-f7a007ff

*-network DISABLED
description: Wireless Interface
product: AR93xx Wireless Network Adapter
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:07:00.0
logical name: wlan0
version: 01
serial: 10:fe:ed:10:0e:5b
width: 64 bits
clock: 33mhz
capabilities: pm msi pciexpress bus_master cap_list ROM ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
resources: irq:18 memory:f79100000-f791ffff memory:f7920000-f792ffff

ifconfig gives me:
lo Link escape:LocalTalk Loopback
inet addr:127.0.0.1 Mask:[255.000.000.000]("tel:255.000.000.000")
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:0
RX bytes:1184 (1.1 KB) TX bytes:1184 (1.1 KB)

dmesg | grep p4p1 gives me:
[      2.691508] systemd-udevd[119]: renamed network interface eth0 to p4p1
[      9.608462] IPv6: ADDCONF(NETDEV_UP): p4p1: link is not ready
```

and thats it.

---

### Post by chili555 on 2014-06-30
We wonder why both ethernet and wireless are disabled. Is this machine running Network Manager?```
ps aux | grep -i network
```In my laptop, where it is running, part of the output is:```
root       792  0.0  0.1 356644  9196 ?        Ssl  Jun26   0:14 [COLOR="#FF0000"]Network[/COLOR]Manager
```If it is not running, what is the result of:```
sudo ifconfig p4p1 up
sudo dhclient p4p1
```Errors? Warnings?? Interesting messages?

If it connects, I suggest we amend /etc/network/interfaces  to set a static address, gateway, DNS, etc. First, let's see what happens above.

As for the question of why the interface is enumerated p4p1 instead of eth0, I do not know; I suspect, however, that we can use p4p1 seamlessly in its place.

---

### Post by steeldriver on 2014-06-30
I think the p4p1 naming is a biosdevname feature --> [http://packages.ubuntu.com/trusty/biosdevname](http://packages.ubuntu.com/trusty/biosdevname)

Not sure if that's the default for 14.04 or a result of something the OP has installed

---

### Post by Martin_Hansen on 2014-06-30
ps aux | grep -i  network gives me:
```
root     1080     0.0      0.0      11744 936 tty1        S+     17:59      0:00 grep --color=auto -i network
```

the result of sudo ifconfig p4p1 is nothing while sudo dhclient p4p1 crashes the system.

EDIT:
by crashing i mean that i cant write any commands. Sorry!

---

### Post by chili555 on 2014-06-30
> biosdevname in its simplest form takes a kernel device name
as an argument, and returns the BIOS-given name it "should" be.

This is necessary on systems where the BIOS name for a given device
(e.g. the label on the chassis is "Gb1") doesn't map directly and
obviously to the kernel name (e.g. eth0).

This also works as a straight udev rule, which is provided.Thank you for the clarification. It may be standard on a server install; it is not installed on my laptop. I wonder/suspect that p4p1 signifies the card in the 4th PCI slot and the 1st ethernet port on that card.

---

### Post by chili555 on 2014-06-30
If the terminal is frozen, it may mean trouble but I more likely believe that the system is requesting an IP address behind the scenes and hasn't got one yet. You could ask the command to give more information, or be **v**erbose:```
sudo dhclient -v p4p1
```Hopefully, you'll see something like:> Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/p4p1/f0:de:f1:3e:b2:xx
Sending on   LPF/p4p1/f0:de:f1:3e:b2:xx
Sending on   Socket/fallback
DHCPDISCOVER on p4p1 to 255.255.255.255 port 67 interval 3 (xid=0xd176322)
DHCPDISCOVER on p4p1 to 255.255.255.255 port 67 interval 8 (xid=0xd176322)Then it, ideally, will get an IP address. In either event, you will see some clues you can report here.

If you do get an IP address, that suggests that the hardware and driver are working as expected. If so, I suggest you set a static IP address in /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto p4p1
iface p4p1 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1

```If there are references to eth0, remove them. Of course, substitute your details here. Select an address outside the DHCP pool used in the router or switch.

Get the system to read and use the changed file:```
sudo ifdown p4p1 && sudo ifup -v p4p1
```Test:```
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---

### Post by Martin_Hansen on 2014-06-30
First of all sudo dhclient -v p4p1 does give me something like that but at the end it says something like: NO DHCPOFFERS recieved.
no working leases in persistent database - sleeping.
and no there isn't any ip address :( .

EDIT:
my bad i did it without ethernet cable :/ now i get an ip of 192.168.10 i can use internet now but i have to Reasign the address everytime i reboot, i dont know how to Thanks you :)

---

### Post by chili555 on 2014-06-30
After you've done:```
sudo ifconfig p4p1 up
```Does the interface still show as disabled here as before?```
sudo lshw -C network
```Previously, it said:> *-network [COLOR="#FF0000"]DISABLED[/COLOR]
description: Ethernet interface
product: Netlink BCM57781 Gigabit Ethernet PCIe
vendor:  Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: p4p1Are there any clues in the log?```
dmesg | grep -e p4p1 -e tg3
```So far, it looks pretty encouraging:> First of all sudo dhclient -v p4p1 does give me something like that but at the end it says something like: NO DHCPOFFERS recieved.
no working leases in persistent database - sleeping.May I assume the obvious; that it is connected to the router or switch with a known working CAT5 or 6?

---

### Post by Martin_Hansen on 2014-06-30
Wireless is now working aswell, if everything Will Continue this Way i'll mark this as solved in 24 hours.

---

### Post by Martin_Hansen on 2014-07-01
The Internet is working but I still wonder why my /etc/network/interfaces looks like this:
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback
```

and another thing I cant login from a remote computer with xrdp.

---

### Post by chili555 on 2014-07-01
I thought you got it working by modifying /etc/network/interfaces as I suggested above. If not, then how?

---

### Post by Martin_Hansen on 2014-07-01
I made it work by using this: [COLOR=#000000][FONT=Ubuntu Mono]sudo dhclient -v p4p1[/FONT][/COLOR] command (Remember your ethernet cable!) and then installing this package: Ubuntu-Desktop and updating everything but as i said i cant connect from xrdp :/

---

### Post by steeldriver on 2014-07-01
If you installed the ubuntu-desktop package then network-manager has probably taken over your interface configuration

If you are determined to use xrdp then you will probably want to install a different desktop session such as xfce4 - xrdp doesn't seem to play well with the Unity desktop

---

### Post by Martin_Hansen on 2014-07-01
> **steeldriver said:**
> 
If you are determined to use xrdp then you will probably want to install a different desktop session such as xfce4 - xrdp doesn't seem to play well with the Unity desktop

Well that's not the problem, the problem is the fact that it won't even connect it doesn't even get to the xrdp login screen.

---

### Post by chili555 on 2014-07-01
I know exactly zero about xrdp. Perhaps steeldriver will take over.

---

### Post by Martin_Hansen on 2014-07-01
I dont actually think that it's xrdp's fault I think that it is the fact that /etc/network/interfaces didn't have the code you wrote, do you know how to do it proper?

---

### Post by chili555 on 2014-07-01
You can edit the file to add the code yourself.```
gksudo gedit /etc/network/interfaces
```Use nano or kate or leafpad or vim if you don't have the text editor gedit.

Change the text to read as i outlined above. Proofread carefully, save and close the text editor.

Be certain you substitute your exact details if they differ from my best guess above.

Reboot.

---

### Post by Martin_Hansen on 2014-07-02
Hi Guys, I fixed the xrdp problem by disabling firewall.

And because everything is working I want to give a big thanks to: chili555 and steeldriver for their help and friendliness.
I will now mark this thread as Solved.

---

### Post by chili555 on 2014-07-02
Awesome! Glad it's working.

---

