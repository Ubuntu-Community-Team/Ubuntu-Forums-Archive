---
title: "Internet Connection Problems"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by shadow129 on 2008-04-26
Hey guys I need some help. Today a brand-new, top of the line, Pentium 3 HP came into my possession. :guitar: It came without an OS, so I decided I'd make it my first dedicated Linux rig. The installation went great (7.04 Feisty Fawn I had laying around from last year) but when I went to try out Firefox I got "the server cannot be reached" page. I've tried both Eth0 and Eth1. Ubuntu says I'm connected and I've tried both of the 2 Ethernet ports on this beast but to no avail. I took out the add-on Ethernet card thinking maybe it could be causing some conflict but I haven't tested it quite yet. If that fails to work could you guys give me some suggestions to try next? The motherboard is a Intel 815 if that helps.

---

### Post by Iowan on 2008-04-26
Post results of **lspci** and** ifconfig -a** and contents of **/etc/network/interfaces**.
Also, how are you connected to internet and how do you get IP address - DHCP, manual configuration?

---

### Post by shadow129 on 2008-04-26
lspci: 

dj@dj-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
dj@dj-desktop:~$ 

ipconfig -a

eth0      Link encap:Ethernet  HWaddr 00:01:02:D4:F1:07  
          inet6 addr: fe80::201:2ff:fed4:f107/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:1 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:7264 (7.0 KiB)
          Interrupt:5 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:01:02:D4:F1:07  
          inet addr:169.254.6.105  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1520 (1.4 KiB)  TX bytes:1520 (1.4 KiB)



I tried /etc/network/interfaces but it said "Permission Denied" I have the connection set to DHCP. Using Verizon DSL with a Westell router. Have the ethernet cable plugged into the integrated ethernet port and removed the add-on NIC.

---

### Post by Iowan on 2008-04-26
**/etc/network/interfaces** is not a command.  The contents must be read, copied, and pasted.  The avah address (169.254.6.105) means your computer did not get an IP address from your router.

---

### Post by shadow129 on 2008-04-27
/etc/network/interfaces results:


auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp



auto eth0

---

### Post by Iowan on 2008-04-27
Can you **ping** the router?
(*Probably* 192.168.1.1 but the manual would be the best guide)

---

### Post by shadow129 on 2008-04-27
I can't ping 192.168.1.1 I get 100% packet loss. Oh and what manual are you talking about? I know I said router before but I'm actually hooked straight to a modem not a router, thought I should make that clear. In WinXP my connection uses DHCP and it works just fine. Would it help to give you any of the details under XP's Network Connections section? It lists my: IP Address, Subnet Mask, Default Gateway, DHCP Server (same address as my Default Gateway) and 2 DNS Server Addresses.

---

### Post by shadow129 on 2008-04-28
bump

---

### Post by Iowan on 2008-04-29
The modem manual should have information about it's address and DHCP information - or the Windows information should bi similar.

---

### Post by shadow129 on 2008-04-30
I'm not sure where the manual is, but Windows gives me this for the DHCP:

DHCP Server: 71.110.144.1

If you tell me what else would be useful I'll post it up for you.

---

### Post by Iowan on 2008-04-30
Can you ping 71.110.144.1?  (Can Windows?)
Does Windows list a gateway? (Probably not for DHCP).

---

### Post by BoJaN111 on 2008-04-30
I'm having this same problem except when I use my XP machine as a router(ethernet to XP then crossover to linux) the connection works perfectly, I'm using it right now but when I plug the cable from my modem into the linux machine I get nothing... It's as if Ubuntu doesn't want to work without a router.

I've tried DHCP,roaming mode and a static IP using the same settings as XP(with XP disconnected) I also recieve packets but can't ping anywhere or view any pages in firefox.

---

### Post by hikeb on 2008-05-01
I'm having almost the same problem. When at home I'll have no problems connecting to the internet through wireless or ethernet cable. But when I come to work I have no internet access with Ubuntu. If I boot up with Windows I'll have no problems with internet access. I also tried booting from a knoppix live-cd and had no problems accessing the internet. So the problem is Ubuntu. 

Now it gets trickier... I can ping, resolve and trace. I also noticed that when trying to download things for example with wget it will start download, but after a few bytes (4 or 5 Kb) it will stop.

I would like to post my outputs, but I need to know how to send command output to a file so I can easily post my results.

Any ideas?

---

### Post by shadow129 on 2008-05-01
> **Iowan said:**
> Can you ping 71.110.144.1?  (Can Windows?)
Does Windows list a gateway? (Probably not for DHCP).

It says my Default Gateway is 71.110.165.1

I'll try to ping that address right now.

---

### Post by shadow129 on 2008-05-09
Sorry it took me so long to reply. I tried pinging that address and I got 100% packet loss. Just today a friend gave me a Linksys router, I'm not sure if I can use that to my advantage in any way.

---

