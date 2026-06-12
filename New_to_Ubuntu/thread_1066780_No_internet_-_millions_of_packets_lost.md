---
title: "No internet - millions of packets lost"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Cardcaptor Stacey on 2009-02-11
I've been without an internet connection for about 10 days now. It originally connected fine, but all of a sudden the internet stopped completely (I suspect it could have been an update from apt). I've tried many fixes and uninstalled network-manager and knetworkmanager thinking that they were the problem but it didn't work. I have manually configured my personal network settings into /etc/network/interfaces which looks like this (I have xed out my personal IP's):

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.x.x.x
netmask 255.255.255.x
network 10.x.x.x
gateway 10.x.x.x
broadcast 10.x.x.x
```

I don't understand why this isn't working. There's nothing wrong with the connection itself as I am using a different laptop now on the same network and it works great.

This is what ipconfig saying:
```
eth0 Link encap:Ethernet HWaddr 00:1e:68:ac:69:6f
inet addr: 10.x.x.x Broadcast: 10.x.x.x Mask: 255.255.255.255.x inet 6 addr: fe80::21e:68ff::feac:696f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:4127194634 overuns:0 frame:0
TX packets:0 errors:0 dropped:1236 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0B) TX bytes:0(0.0B)
Interrupt:219

lo Link encap:Local loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:728 errors:0 dropped:0 overruns:0 frame:0
TX Packets:728 errors:0 dropped:0 overruns:0 carrier:0 collisios:0 txqueuen:0
RX bytes:62184 (62.1KB) TX bytes:62184 (61.1KB)
```

Your help is greatly appreciated. :) Thank you

---

### Post by Kevbert on 2009-02-11
The first thing to work out is what wireless card you have as you may need to install a firmware driver. Go to Applications-Accessories-Terminal and enter the following command(s)
```
lspci
```
to list all PCI devices or
```
lsusb
```
to list all USB devices (if you are using a wireless USB adapter).
The output will give you the wireless chipset and model (for example Broadcomm BCM4306 Rev02). The output will determine how to proceed. The alternative will be if you have a disk/CD with WIndows XP .inf and .sys drivers in which we can try a different approach.

---

### Post by handydan918 on 2009-02-11
Any IP's that staart with 10. are private IP's and as such, are not directly accessible from the Internet, assuming you are behind a NAT router. 
It might be helpful to post the file unedited so that the network gods can review things like your broadcast range, etc.

also, what does ```
sudo dhclient
``` give you?

---

### Post by Cardcaptor Stacey on 2009-02-11
Sorry, it took so long getting back. Had to manually type everything. Please excuse any typos :(

Kevbert - Sorry, I failed to say I'm using a wired connection. I'm not sure if I've ever had wireless working on my Acer Aspire One but I will damn give it a try if wired doesn't work. Did lspci and this is what it returned:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation G2801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation G2801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation G2801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation G2801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation G2801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation G2801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation G2801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation G2801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation G2801G (ICH7 Family) USB EHCI Controller (rev 02)
00:le.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:lf.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:lf:2: IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:lf.3 SMBus Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtex Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abh Wireless PCI Express Adapter (rev 01)
04.00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04.00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04.00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04.00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

sudo dhclient gives (omitted the copyright):
```

Listening on LPF/eth0/00:le:68:ac:69:6f
Sending on LPF/eth0/00:le:68:ac:69:6f
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by niteshifter on 2009-02-11
Hi,

That other laptop that works ... if it's a Linux or Mac OS X machine run this command:
```
ifconfig
```
and take note of the lines that begin with "inet addr", write down that line and post it here.

Example ifconfig, want the line in [COLOR="Red"]red[/COLOR]:
```

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:81:29:E8  
          [COLOR="Red"]inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::21c:bfff:fe81:29e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10061 errors:23 dropped:142 overruns:0 frame:0
          TX packets:6231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13219503 (12.6 MB)  TX bytes:701813 (685.3 KB)
          Interrupt:17 Base address:0x8000 Memory:f9fff000-f9ffffff 
```



If it's a windows machine (2k, XP, Vista), click Start, then Run and type in:
```
cmd
```
then type
```
ipconfig
```
and take note of the line(s) that begin with "IP Address", Subnet Mask and Default Gateway, write down those addresses and post it here.

Example ipconfig, want the stuff in [COLOR="Red"]red[/COLOR]:
```
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
[COLOR="Red"]        IP Address. . . . . . . . . . . . : 192.168.1.139
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
[/COLOR]
```

---

### Post by Cardcaptor Stacey on 2009-02-11
The laptop is FreeBSD but ifconfig still works. Just displays a little different. Here's the line:

```
removed for security reasons
```

---

### Post by niteshifter on 2009-02-11
Hi,

Ok, looks like you are connected to a static sub-net, so nevermind DHCP (dhclient).

After you edited your /etc//network/interfaces file did you restart networking? The below (or a reboot) is needed. Until restarted, changes in the interface file will have no effect.
```
sudo /etc/init.d/networking restart
```

---

### Post by Cardcaptor Stacey on 2009-02-11
Yes, I always do ```
sudo /etc/init.d/networking restart
``` after I change the interfaces file, followed by ```
ping www.google.co.uk
``` which returns "ping: unknown host www.google.co.uk".

---

### Post by Kevbert on 2009-02-11
Have a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=902860") for wireless (especially post 6) as you have the infamous Atheros AR242x wifi.
What info do you have under Administration-Network-Hosts (you should also be able to check this in terminal, but I can't remember the command)?

---

### Post by NetworkGuy on 2009-02-11
Another idea..   Could this be a DNS issue?   Can you ping your router by IP addess?  Look like it would be 10.1.1.1.   If that works, can you ping 69.147.76.15 (yahoo.com)?

If both of those work, then we need to look into your /etc/resolv.conf file to see if the nameserver lines are correct.

---

### Post by ugm6hr on 2009-02-11
Have you tried booting into an older kernel?

EDIT: [https://bugs.launchpad.net/ubuntu/+bug/313866](https://bugs.launchpad.net/ubuntu/+bug/313866)

---

### Post by Cardcaptor Stacey on 2009-02-11
ugm6hr, thank you sooooooooo much. *kiss* I can't believe it was the kernel all along. All fixed now. Incase someone else is having this problem, I changed to version 2.6.27-9-generic.

Thanks to everyone else who helped. :)

---

