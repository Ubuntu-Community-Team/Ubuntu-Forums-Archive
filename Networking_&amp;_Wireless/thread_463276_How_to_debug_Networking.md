---
title: "How to debug Networking?"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by msandersen on 2007-06-03
I had to replace a motherboard on my old PC, I replaced it with the exact same model, hoping not having to reinstall. Ubuntu works, Windows doesn't. The BIOS seem to be a different version.

Before, it had eth0 and eth1, with eth1 set active.
Now, it shows eth0 and eth2, and a warning icon on the top right which show the following error when double-clicked relating to eth1: SIOCGIFFLAGS error: No such device

To get online, I reset the DNS servers list in the Networking control panel. I tried setting eth0 as active, but the system kept removing my DNS entries and setting it to 192.168.1.1 (which is my ADSL modem/router). It seems to be fine once I disabled eth0 and set eth2 as active.
 
As I don't know much about Linux networking, how can I troubleshoot this issue? The hardware ought to be the same, but BIOS settings might affect things. Obviously, something is different.

---

### Post by waynejkruse10 on 2007-06-03
I get the same problem on Ubuntu Feisty Fawn. I try to set the DNS settings manually in the Netwok Preferences but it sets it back automatically to my router IP. It is even more frustrating because without my ISP's DNS servers manually set my Internet is much slower and laggier than normal.

---

### Post by msandersen on 2007-06-05
Since I set eth2 as active and unticked eth0, the DNS settings have stuck. I don't know what eth0 is.
My ADSL modem ha a router with an Ethernet and a USB port. I usually use the Ethernet for my main computer, and the USB for anyhing else. This computer used to be my main computer until it "blew up". Since then I've got a new one, long overdue as the old one is rather long in the tooth. The new one just has Vista on it. Don't want to risk partitioning tools on it at this stage, too many stories of ppl having problems with Vista dual-booting, and the gparted forums confirms this. 
Anyway, now I'm using the USB port for the old computer, which has been refitted with a new motherboard of the exact same model as before, which might have been a reason for eth0 not working. But trying just now booting with the Ethernet cable in, makes no difference. It doesn't recognise eth1. Not a lot of plug-and-play here. Not a great surprise, I know, that Linux should be less userfriendly in that department, but annoying. I'd still like to know how to debug eth1.
Looking around here, I came up with these commands (truncated output):
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:40:F4:EA:E7:4D  
          inet6 addr: fe80::240:f4ff:feea:e74d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:880 (880.0 b)  TX bytes:468 (468.0 b)
          Interrupt:11 Base address:0x4f00 

eth2      Link encap:Ethernet  HWaddr 00:30:0A:44:25:98  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:aff:fe44:2598/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1184612 (1.1 MiB)  TX bytes:270301 (263.9 KiB)

```
lspci
```
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
cat /etc/iftab
```
eth0 mac 00:40:f4:ea:e7:4d arp 1
eth1 mac 00:50:bf:71:1b:19 arp 1

```

The one thing I notice is the entry for eth1 in iftab, and no mention of eth2, as well as the diferent hardware address between the two. Is this something that is assigned from the BIOS? I don't want to edit this file unless I know any better, or can fix eth1 to reappear instead of eth2.

---

### Post by msandersen on 2007-06-05
The content of file **/etc/network/interfaces**
```
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
	address 192.168.1.20
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 203.12.160.35 203.12.160.36

iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1



iface eth2 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
```As you can see, I used to have eth1 at 192.168.1.10, but changed it to 20 for eth2 as it's now the backup computer.

---

