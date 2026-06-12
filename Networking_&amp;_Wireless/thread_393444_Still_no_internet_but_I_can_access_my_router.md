---
title: "Still no internet but I can access my router"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by mastaworm on 2007-03-25
I can get an IP either through ethernet or wireless and I can access the router's web-based control page, but I can't access internet or even ping the router. What am I doing wrong here? All the windows computers can get on the internet and so can my palm TX. My laptop connects just fine at my place but here at my parents house I get this problem. Both routers are dlink and seem very similar in functionality, mine(working) is just newer than theirs(not working).

---

### Post by Mr. C. on 2007-03-25
Ensure that only 1 of your interfaces is active.  System->Administration->Network.  Turn off one of them, leave the other on.

MrC

---

### Post by mastaworm on 2007-03-25
I've tried all that. I've got a feeling that it's a similar problem though. Is there a way to specifically force a connection to be primary? It seems like it's trying to go through the loopback or something stupid like that. Also, I can get internet by way of bluetooth tether to my phone but that is both slow and power hungry to my phone.

---

### Post by Mr. C. on 2007-03-25
Let's work one thing at a time.

Show output from a Terminal window of:

```
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces
```

MrC

---

### Post by mastaworm on 2007-03-25
ryan@ryan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3F:6A:D9:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:4F:C8:91  
          inet addr:191.168.0.1  Bcast:191.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe4f:c891/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18745 (18.3 KiB)  TX bytes:4211 (4.1 KiB)
          Interrupt:201 Memory:e8204000-e8206000 

ryan@ryan-laptop:~$ cat /etc/resolv.conf 
nameserver 191.168.0.254
ryan@ryan-laptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#iface wlan0 inet dhcp
#wireless-essid dlink
#wireless-key s:blahs

auto eth2
iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0


Some of those things are commented out becasue I'm using network manager

---

### Post by Mr. C. on 2007-03-25
There is a mismatch between what your ifconfig indicates and what your interfaces file shows.   This makes diagnosis difficult, because the system state does not match its configuration, which implies you've changed something since boot.

It would be impossible to get access to the router's web page without basic networking functioning.  If your router normally responds to ICMP pings, then it would respond when you can gain access to its web interface.

Network Manager currently works reliably with one network interface defined and in use.  Once booted, you can manually bring down the interfaces and bring one up manually if desired.
```

ifdown -a
ifup lo
ifup eth0 #  or wlan0
```

MrC

---

### Post by mastaworm on 2007-03-25
Ok I just tried that and it still does the same thing, I even ran ifconfig to make sure only those two were running. And just to make sure, I pinged the router with a windows pc and it worked fine.

---

### Post by Mr. C. on 2007-03-25
You haven't explained to me why your configuration does not match your files. 

You haven't helped me understand your hardware and setup.

I can't help if you're going to do the interpretation of the data for me.

Boot the system, show the output of:

```
ifconfig -a
lspci
lspci -n
sudo lshw -class network
```


MrC

---

### Post by mastaworm on 2007-03-26
Ok yeah, you're right. I don't know that much about networking but I try to learn when I can. Idon't know why the files are the way they are, I just know I hadn't changed anything since it worked at my place but as soon as I got here at my parents place it does this weird stuff.

Anyway here's what you asked for.
[PHP]ryan@ryan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:3F:6A:D9:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:717788 (700.9 KiB)  TX bytes:717788 (700.9 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:4F:C8:91  
          inet addr:191.168.0.1  Bcast:191.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe4f:c891/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1190581 (1.1 MiB)  TX bytes:58240 (56.8 KiB)
          Interrupt:201 Memory:e8204000-e8206000 

ryan@ryan-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

ryan@ryan-laptop:~$ lspci -n
00:00.0 0600: 1002:5833 (rev 02)
00:01.0 0604: 1002:5838
00:13.0 0c03: 1002:4347 (rev 01)
00:13.1 0c03: 1002:4348 (rev 01)
00:14.0 0c05: 1002:4353 (rev 16)
00:14.1 0101: 1002:4349
00:14.3 0601: 1002:434c
00:14.4 0604: 1002:4342
00:14.5 0401: 1002:4341
00:14.6 0703: 1002:434d (rev 01)
01:05.0 0300: 1002:4e50
02:00.0 0c00: 104c:8026
02:02.0 0280: 14e4:4320 (rev 03)
02:03.0 0200: 10ec:8139 (rev 10)
02:04.0 0607: 104c:ac54 (rev 01)
02:04.1 0607: 104c:ac54 (rev 01)
02:04.2 0880: 104c:8201 (rev 01)
02:07.0 0c03: 1033:0035 (rev 43)
02:07.1 0c03: 1033:0035 (rev 43)
02:07.2 0c03: 1033:00e0 (rev 04)

ryan@ryan-laptop:~$ sudo lshw -class network
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:4f:c8:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.22 firmware=Linksys,07/17/2003, 3.30.15.0 ip=191.168.0.1 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e8204000-e8205fff irq:201
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6a:d9:07
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:e8208800-e82088ff irq:193
[/PHP]

---

### Post by Mr. C. on 2007-03-26
Ok, good, now I understand your hardware.

Let's try to start with the wired connection, if that's ok with you.

System->Administration->Network, disable the wireless network, and enable the wired.  Reboot.

Now, you should have one interface (eth0) enabled - now show output from :

```
ifconfig -a
grep DHCP /var/log/syslog | tail -20

```

MrC

---

### Post by mastaworm on 2007-03-26
Hey thanks for your interest but I upgraded to feisty and everything works perfectly now.

Seriously though thanks for trying to help[img]http://www.iportalx.net/forum/smileys/thumb-up.gif[/img]

---

