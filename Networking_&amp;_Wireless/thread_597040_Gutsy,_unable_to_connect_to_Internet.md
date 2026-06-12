---
title: "Gutsy, unable to connect to Internet"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Fuqaha on 2007-10-30
Hi friends,

I am a new Linux user (formerly using Vista, dual boot actually). 

Last few days, i was using the internet at my home (which connects to the provider via router, dhcp). Everything worked purrrrfectly.

However, today I brought my PC to my university and I cant seem to be able to connect to the internet (perhaps my university's server) (using Static IP) - although using Windows, it worked fine.

I have browsed and tried a few solutions provided in the forum, but to no avail.

Here some information:

```

eth0      Link encap:Ethernet  HWaddr 00:16:76:B2:FD:46  
          inet addr:192.168.105.44  Bcast:192.168.105.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:feb2:fd46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:35036 (34.2 KB)  TX bytes:4187 (4.0 KB)
          Base address:0x30c0 Memory:90300000-90320000 

```

```

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

```

/etc/network/interfaces
auto eth0
iface eth0 inet static
	address 192.168.105.44
	gateway 10.10.0.4
	netmask 255.255.255.0
	network 192.168.105.0
	broadcast 192.168.105.255

```

Gateway : 10.10.0.4, i know its weird, but using Xp / Vista, the computer connects well.

This is my Vista ipconfig that works:
```

C:\Users\Architect Fuqaha>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : ArchitectFuqaha
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) 82566DC Gigabit Platform LAN Con
nect
   Physical Address. . . . . . . . . : 00-16-76-B2-FD-46
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::6db0:8206:283a:f9e%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.105.140(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 10.10.0.4
   DNS Servers . . . . . . . . . . . : 192.168.10.1
                                       192.168.10.2
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{98AF9503-8C27-4CAE-9F05-063B995B2
1CB}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.105.140%10(Preferred)

   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.10.1
                                       192.168.10.2
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4136:e38a:2ce7:277b:3f57:9673(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::2ce7:277b:3f57:9673%9(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

```

As ive said above, ive tried a few solutions, but most of them ends with this:
[B]SIOCADDRT: No such process
Failed to bring up eth0.[/B]

Any idea? Thank you very much for even reading this. 

=)

---

### Post by kevdog on 2007-10-30
In windows you are connecting with a static IP??


Try connecting via the command line since you can change a bunch of options more freely.  The link is in my signature.  Also doing a man iwconfig will help you add additional iwconfig options not listed in the post.  I dont think you need to specify broadcast and network.  I would also try initially not connecting with a gateway statement to see what gets assigned automatically.  Without a gateway you should be able to connect to the router, just not get beyond the router -- "no gateway".  Something seems fishy about your gateway statement, but who knows.

route -n 
This command can be used to check the gateway.  Commands how to set the gateway address is at the bottom of the post or consult google.

---

### Post by MariusSilverwolf on 2007-10-30
2 questions.

1) In Gutsy, do you have the DNS server settings configured in Network Manager to match the DNS settings listed in the Windows ipconfig output?

2) When in Windows, do you need to connect through any client software before you can get to the outside world?

---

### Post by Fuqaha on 2007-10-30
Hi kevdog & MariusSilverwolf,

Thanks for your answers. I really appreciate it.

1.	At home, my desktop can easily connect to the internet without any configuration. However, when I brought it to my university, it cannot connect to the internet. **What strange is, it can detect Windows network & printers at the Places > Networks**. When I switch back to Windows, and use the same configuration (the IP, gateway & DNSs states above), my desktop connects to the internet seamlessly.

2.	The settings in my faculty requires the computers to use a static IP, and its true, because when I tried connecting (in Windows) using DHCP, it will not connect to the internet. 

3.	In Windows, to connect to the internet, I just need to change my IP, Gateway, and the DNS servers. That is, I do not need to use client software.

4.	This is what I got when I do
```

fuqaha@Fuqaha-ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
*-network                
description: Ethernet interface 
product: 82566DC Gigabit Network Connection 
vendor: Intel Corporation 
physical id: 19 
bus info: pci@0000:00:19.0 
logical name: eth0 
version: 02 
serial: 00:16:76:b2:fd:46 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-0 ip=192.168.105.44 latency=0 module=e1000 multicast=yes 
fuqaha@Fuqaha-ubuntu:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.105.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0 

```

5.	Attached here is the device map (when using Vista). 
[[IMG]http://img502.imageshack.us/img502/2866/captureky4.th.jpg[/IMG]](http://img502.imageshack.us/my.php?image=captureky4.jpg)


Thank you for your kindness. I hope my explanation above makes sense. (and ah, Im not using WiFi, im using cable).

=)

---

### Post by MariusSilverwolf on 2007-10-30
route -n looks like it hit the router and not the gateway beyond it.

I'm almost wondering what happens if you remove the "gateway" line in your interfaces file, so that it looks more like this:

auto eth0
iface eth0 inet static
	address 192.168.105.44
	netmask 255.255.255.0
	network 10.10.0.4
	broadcast 192.168.105.255

Shot in the dark, and may not be the right track, but it's the only thing that comes to mind that *I* would try right now.

---

