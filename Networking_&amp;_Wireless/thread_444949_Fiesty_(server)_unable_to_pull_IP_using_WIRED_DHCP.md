---
title: "Fiesty (server) unable to pull IP using WIRED DHCP"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by rsain on 2007-05-15
*This problem is similar to many - with slight differences, please read closely.*

I'm at home running a cable modem --> linksys wrt54g --> Two home computers and two Ubuntu Servers (sunfire x2200's)

Router is set to DHCP. Both macintosh machines are able to pull an IP, one is wireless the other is wired.

I added the two servers the other day (Ubuntu server latest stable release). I have the cable installed in eth1 (I also tried this in eth0). The /etc/network/interfaces file is set as follows:
---
#the rimary network interface
auto eth1
#iface the1 inet static
# address 192.168.1.111
# netmask 255.255.255.0
# network 192.168.1.0
# broadcast 192.168.1.255
# gateway 192.168.1.1
iface eth1 inet dhcp
---

after changing it from static (I commented all the lines) I ran sudo /etc/init.d/networking restart and I get the following:


There is already a pid file /var/run/dhclient.eth1.pid with pid 4897
killed old client processes, removed old pid file
<snip>
dhcpdiscover on eth1 to 255.255.255.255 port 67 interval 3
dhcpdiscover on eth1 to 255.255.255.255 port 67 interval 4
dhcpdiscover on eth1 to 255.255.255.255 port 67 interval 7
dhcpdiscover on eth1 to 255.255.255.255 port 67 interval 12
dhcpdiscover on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
no working leases in persistent database - sleeping


Now I run ifconfig eth1 and this is returned:

eth1 link encap:ethernet hwaddr 00:16:36:68:46:0e
upbroadcast multicast mtu:1500 metric:1
rx packets:0 errors:0 dropped:0 overruns:0 frame:0
tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
rx bytes:0 (0,0 b) tx bytes: 0(0,0 b)
interrupt:20 base address: 0xe000


As you can see it's not pulling an IP address!
Any ideas what is going on?

I've tried both machines, multiple ports on each. I tried setting it up as static. I reset the servers, I reset the router.

I'm at a loss.

TIA,

- Ryan

---

### Post by x64Jimbo on 2007-05-15
You should probably be setting up static IPs on the DHCP server, not the clients. Set the clients back to DHCP and then set up static addresses for them in your router. Much easier this way.

---

### Post by rsain on 2007-05-15
I'm a bit confused.... which clients? 

My two sun boxes need to connect to the net to finish the config as LAMP and to get appropriate PEAR packages, etc. 

I cannot get these buggers to talk to the router at all. Static or not. There will be no clients asking these servers for ip addresses.

- Ryan

---

### Post by x64Jimbo on 2007-05-15
The servers are clients. They are clients of your DHCP server, which is your router. You need to get them to talk to your router and ask it for an IP address rather than assume their own IP addresses. You can use the router to always assign the same IPs to each box so that your port forwards always work correctly.

---

### Post by rsain on 2007-05-15
gotcha.

That was my first attempt - assign the IPs static. I'll uncomment the lines and report what I get.

Thanks.

- ryan

---

### Post by dbott67 on 2007-05-15
There are a number of threads with people having issues with certain NIC modules.

Can you post the output of the following 2 commands:
```
dbott@feisty:~$ [COLOR=Red]**sudo lshw -C network**[/COLOR]
Password:
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:16

dbott@feisty:~$ [COLOR=Red]**sudo lspci | grep Eth**[/COLOR]
02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

```Check [this thread]("http://ubuntuforums.org/showthread.php?p=2588739#post2588739") (post #13 and #19, specifically) for more network troubleshooting tips.

-Dave

---

### Post by rsain on 2007-05-15
This is annoying. I created a static IP on the router - 192.168.1.111 i set my interfaces file to read as follows:

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
address 192.168.1.111
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

ifconfig eth2 shows the correct ip but I cannot ping anything (even machines on the local network).

- Ryan

---

### Post by dbott67 on 2007-05-15
What is the output of:
```
route -n
```

-Dave

---

### Post by rsain on 2007-05-15
After running sudo lshw -C network the following returns:

description: ethernet interface
product: netextreme bcm5715 gigabit ethernet
vendor: broadcom corp
physical id: 4.1
bus info: pci@06:04.1
logical name: eth3
version: a3
serial: 00:16:36:68:46:0c
capacity: 1gb/s
width: 64 bits
clock: 66mhz
capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion:3.72 duples=half firmware=5715-v3.24 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair
resources: iomemory:fdfc0000-fdfcffff iomemory:fdfb0000-fdfbffff irc:18

After running sudo lspci | grep Eth the following returned:

00:08.0 bridge: nvidia corp mcp55 ethernet (rev a3)
00:09.0 bridge: nvidia corp mcp55 ethernet (rev a3)
06:04.0 ethernet controller: broadcom corp netxtreme bcm5715 gigabit ethernet (rev a3)
06:04.1 ethernet controller: broadcom corp netxtreme bcm5715 gigabit ethernet (rev a3)

Does this help?

- Ryan

---

### Post by rsain on 2007-05-15
looks a bit odd to me (but I don't know what I'm looking for):


 route -n
line 1
192.168.1.0   0.0.0.0    255.255.255.0     U   0   0   0 eth2
line 2
0.0.0.0       192.168.1.1    0.0.0.0  UG   0   0   0  eth2

- Ryan

---

### Post by dbott67 on 2007-05-15
> **rsain said:**
> looks a bit odd to me (but I don't know what I'm looking for):
```
route -n
192.168.1.0   0.0.0.0    255.255.255.0     U   0   0   0 eth2
 0.0.0.0       192.168.1.1    0.0.0.0  UG   0   0   0  eth2
```

- Ryan

This looks okay (here's mine for comparison):
```
dbott@feisty:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

In your case, the routing table is saying, if the IP address is not on this network (192.168.1.0) then send it to the gateway device (192.168.1.1).

Yours is the same as mine (except my interface is eth0, not eth2).

If the 2nd line was missing (which happens from time to time) then you would not be able to get off your network.

-Dave

---

### Post by dbott67 on 2007-05-15
By the way, here's a handy little trick for when you can't get online and you need to paste the output here:

[COLOR=Red]*Note: you don't need to do this, it's just for future reference.*[/COLOR]

If you can't get online at all, maybe you copy & paste the output to a text file & save it to USB/floppy and bring it over to a working computer (or use the 'redirect' command).

Can you please post the output of the following commands:

```
cat /etc/network/interfaces > interfaces.txt
```This will create a file in your home directory called 'interfaces.txt that you can copy to USB or floppy and then upload from Windows. _**It won't display anything on screen.**_

Here's mine as an example (redirected to the screen only, not to a file):

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```This command shows ALL network interfaces on the system (whether enabled or not). Again, you should redirect the output to a file:

```
ifconfig -a > ifconfig.txt
``````
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```This command outputs the network hardware detected:

```
sudo lshw -C network > lshw.txt
```Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```This command prints out your routing table:

```
route -n > route.txt
``````
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```And finally, this command prints out PCI information:

```
lspci > lspci.txt
``````
dbott@dapper:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
?000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR=Red]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```After you've run the 5 commands, copy the files (interfaces.txt, ifconfig.txt, lshw.txt, route.txt and lspci.txt) to a floppy or USB drive and them post them up here.

- Dave

---

### Post by rsain on 2007-05-15
thanks for the advice... copying now uploading in a minute.

- ryan

---

### Post by dbott67 on 2007-05-15
A few things to try:

1. Make sure the tg3 module is loaded:
```
dbott@feisty:~$ [COLOR=Red]**lsmod | grep [COLOR=Blue]8139[/COLOR]**[/COLOR]
8139too                27648  0
mii                     6528  1 8139too

```

Replace [COLOR=Blue]8139[/COLOR] with [COLOR=Blue]tg3:
[COLOR=Black]```
lsmod | grep tg3
```[/COLOR]

[/COLOR]2. Try the link in post #6 above.  The 2 key posts in that thread (#13 and #19) provide a few tips that have worked for others (changing boot parameters [such as [COLOR=Red]acpi=off[/COLOR]] in grub and resetting BIOS to defaults), as well as how to make the changes in grub.

-Dave

---

### Post by rsain on 2007-05-15
I can see the files you wanted me to create but it doesnt seem to recognize my usb stick..... or I just don't know where to look. 

Hang on....

- ryan

---

### Post by rsain on 2007-05-15
Oh happy day. Inserted USB. Couldn't find the bugger - so ran fdisk -l   

tried to cp to that location, to no avail. Then just for fun, check the stick in the powerbook and see if it happened to cp. Well, great, the whole 2gig of info is gone.... 

I'm about ready to go back to dapper - this fiesty is making me pissy!

- ryan

---

### Post by rsain on 2007-05-15
> **dbott67 said:**
> A few things to try:

1. 
```
dbott@feisty:~$ [COLOR=Red]**lsmod | grep [COLOR=Blue]8139[/COLOR]**[/COLOR]
8139too                27648  0
mii                     6528  1 8139too

```
This produces nothing.

> 
Replace [COLOR=Blue]8139[/COLOR] with [COLOR=Blue]tg3:
[COLOR=Black]```
lsmod | grep tg3
```[/COLOR]


This produced tg3   114308   0
> 
[/COLOR]2. Try the link in post #6 above.  The 2 key posts in that thread (#13 and #19) provide a few tips that have worked for others (changing boot parameters [such as [COLOR=Red]acpi=off[/COLOR]] in grub and resetting BIOS to defaults), as well as how to make the changes in grub.

-Dave

I'll get there. I'm still trying to do your requests....

- Ryan

---

### Post by rsain on 2007-05-15
Ok - after finally figuring out how to successfully mount a usb stick...

INTERFACES
```

[COLOR="DarkRed"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
#iface eth2 inet static
#	address 192.168.1.111
#	netmask 255.255.255.0
#	network 192.168.1.0
#	broadcast 192.168.1.255
#	gateway 192.168.1.1
iface eth2 inet dhcp


```[/COLOR]
IFCONFIG
```

[COLOR="DarkRed"]eth0      Link encap:Ethernet  HWaddr 00:16:36:68:46:0D  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:16:36:68:46:0E  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr 00:16:36:68:46:0B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth3      Link encap:Ethernet  HWaddr 00:16:36:68:46:0C  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:784 (784.0 b)  TX bytes:784 (784.0 b)

[/COLOR]

```
ROUTE
```

[COLOR="DarkRed"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/COLOR]

```
LSPCI
```

[COLOR="DarkRed"]00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ASPEED Technology, Inc. AST2000
05:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev b5)
06:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5715 Gigabit Ethernet (rev a3)
06:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5715 Gigabit Ethernet (rev a3)[/COLOR]

```
LSHW
```

 [COLOR="DarkRed"] *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5715 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@06:04.0
       logical name: eth2
       version: a3
       serial: 00:16:36:68:46:0b
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 firmware=5715-v3.24 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: iomemory:fdff0000-fdffffff iomemory:fdfe0000-fdfeffff irq:19
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5715 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 4.1
       bus info: pci@06:04.1
       logical name: eth3
       version: a3
       serial: 00:16:36:68:46:0c
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=half firmware=5715-v3.24 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair
       resources: iomemory:fdfc0000-fdfcffff iomemory:fdfb0000-fdfbffff irq:18[/COLOR]

```

There you go! The reason the route changed is because I switched back to dhcp to try something (from the router side).

- ryan

---

### Post by x64Jimbo on 2007-05-16
I misspoke earlier. My WRT54G is running the DD-WRT firmware and has the capability to add Static DHCP leases, but the factory firmware does not. I **highly** recommend loading this aftermarket firmware however, since it adds this feature and lots more that you will find extremely useful.

---

### Post by dbott67 on 2007-05-16
Hi Ryan,

Sorry it's taken so long to get back to you --- my home phone/internet service is out (don't know why, but the repair tech is coming today).

Anyhow, it looks like each of the Sunfire's have dual ethernet cards.  Perhaps we could try disabling one of them and then re-enabling the other:

1. Edit your interfaces file so that eth2 & eth3 are set for DHCP.

2. Make sure that you only have one patch cable connected & verify which interface it's plugged into (eth2 or eth3) [I'll assume it's plugged into eth2 for this example].

3. Bring down both interfaces:
```
sudo ifdown eth2
```
```
sudo ifdown eth3
```

4. Bring up eth2:
```
sudo ifup eth2
```

5. Request an IP from DHCP server:
```
sudo dhclient eth2
```

Keep the USB plugged in and re-direct any output to a file if you still can't get online.

-Dave

---

### Post by rsain on 2007-05-16
Thanks for the help everyone! 

IIRC the 2200 has 4 network cards. I'll bring them all down and open only eth2.

However, we just set up Ubuntu (6x) on two x4100s and didn't have this issue at all (several weeks ago). 

I tried the GRUB solutions mentioned in the other posts and all that did was cause a weird problem where the stysem hangs in the middle of the boot (still haven't got out of that mess yet). 

I'll also look into the firmware upgrade for my router.

- ryan

---

### Post by rsain on 2007-05-16
> **x64Jimbo said:**
> I misspoke earlier. My WRT54G is running the DD-WRT firmware and has the capability to add Static DHCP leases, but the factory firmware does not. I **highly** recommend loading this aftermarket firmware however, since it adds this feature and lots more that you will find extremely useful.

I've been peeking around the DD-WRT site and while this looks very useful all I see are failure points for a user who is not confident and skilled.... :-D 

Quite honestly I can't even figure out which version to download! I'm running the WRT54G v3 (so pretty much any stable release will work) but then I go to the file list in the wiki and have no idea which version to actually grab (each does something different) - and I can see myself toasting my router by choosing the wrong one. 

So, my awareness of my ignorance warns me not to do this. 

If you have some quick words of confidence and support - I may be willing to give it a go.

- Ryan

---

### Post by rsain on 2007-05-16
> **dbott67 said:**
> 

1. Edit your interfaces file so that eth2 & eth3 are set for DHCP.

I did this and here is the current uncommented contents of the /etc/network/interfaces file: 
```

[COLOR="DarkRed"]auto lo
iface lo inet loopback
auto eth2
iface eth2 inet dhcp
iface eth3 inet dhcp[/COLOR]

```
> 
2. Make sure that you only have one patch cable connected & verify which interface it's plugged into (eth2 or eth3) [I'll assume it's plugged into eth2 for this example].
OK

> 
3. Bring down both interfaces:
```
sudo ifdown eth2
```
```
sudo ifdown eth3
```
[quote]

Done. Upon bringing down eth3 the following returned:

```

[color="DarkRed"]
ifdown: interface eth3 not configured
[/color]

```

[quote]
4. Bring up eth2:
```
sudo ifup eth2
```


[color="DarkRed"]
the output file was created but there was nothing in it. Basically, nothing happened. It did the usual - tried to get a connection, but couldn't.[/color]
> 
5. Request an IP from DHCP server:
```
sudo dhclient eth2
```


[color="DarkRed"]
Basically, the same thing happened again - output file created, but no content in it. On screen display was the same stuff - 
```
[color="DarkRed"] listening on XXX 
Sending on same. 
Sending on Socket/fallback. 
Dhcpdiscover on eth2 to 255.255.255.255 port 67 interval 6
Dhcpdiscover on eth2 to 255.255.255.255 port 67 interval 8
Dhcpdiscover on eth2 to 255.255.255.255 port 67 interval 10
Dhcpdiscover on eth2 to 255.255.255.255 port 67 interval 7
No DHCPoffers received
no working leases in persistent database - sleeping[/color]

```

- Ryan

---

### Post by dbott67 on 2007-05-16
Hi Ryan,

It may be the type of NIC or perhaps the driver or kernel.

Let's compare this install with the 6 installs from last week.  You'll need to post the output from one of the working servers, plus the one that's giving you trouble:

1. Compare kernel versions:
```
uname -a
```

2. Compare nic hardware & driver, etc:
```

  *-network:0
       description: Ethernet interface
       product: [COLOR=Red]NetXtreme BCM5715 Gigabit Ethernet[/COLOR]
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@06:04.0
       logical name: eth2
       version: a3
       serial: 00:16:36:68:46:0b
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR=Red]driver=[COLOR=Blue]tg3[/COLOR] driverversion=[COLOR=Blue]3.72[/COLOR][/COLOR] firmware=5715-v3.24 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: iomemory:fdff0000-fdffffff iomemory:fdfe0000-fdfeffff irq:19
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5715 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 4.1
       bus info: pci@06:04.1
       logical name: eth3
       version: a3
       serial: 00:16:36:68:46:0c
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=half firmware=5715-v3.24 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair
       resources: iomemory:fdfc0000-fdfcffff iomemory:fdfb0000-fdfbffff irq:18

```

3. If you've got an old spare NIC lying around, maybe you can pop it in the server & try it (or perhaps swap out one of the extra NICs from the x4100 servers).

---

### Post by rsain on 2007-05-16
We did two installs with Ubuntu version 6.x. Problem is those are in Kabul, Afghanistan and I'm not (western USA). No spare cards laying around, but these are 'out of the box' servers! 

I'm trying a fresh install with a few different settings for network config, I'll report back. 

- Ryan

---

### Post by rsain on 2007-05-16
And before you ask - I can't ssh into those because we turn them off every day when we leave work (Kabul). We have to, because the power turns off to the building shortly thereafter. So, I may be able to grab the info late tonight when everyone gets to work (about 11pm for me).... :)

- Ryan

---

### Post by rsain on 2007-05-16
Tried the grub options as listed in other posts

adding noapic did nothing (after reboot still unable to pull an IP)
adding apic=off did nothing

- Ryan

---

### Post by rsain on 2007-05-16
hmmm.. this is really odd.

I was looking at 

```
lshw -C networking
```

and saw that the network "numbers" were not matching with the logical name of the device. 

So I just left the cord in slot 0 (according to the back of the machine) and started enabling each of the NICs one by one. I got to eth3 with cord in slot 0 and it pulled an ip using dhcp. 

Another person did report that they just had to "networking restart" 4 or 5 times (each time) in order for it to get an ip. Odd coincidence? 

So,

Still not sure what really got this to work, but I'm going to try and replicate on a new machine. 

Oh, and I still have grub set with the acpi=off.

- Ryan

---

### Post by rsain on 2007-05-16
Ok, second machine. No modifications to grub.

eth2 is actually port listed as 0 on the back of the machine. Set "auto eth2" and "iface eth2 inet dhcp" and worked fine. 

- ryan

---

