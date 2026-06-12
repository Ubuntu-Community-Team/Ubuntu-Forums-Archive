---
title: "Connect to internet via ethernet connection"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by adammc on 2008-03-11
Hi guys,

I am unable to connect to the internet via my ethernet connection. I am currently using the wireless connection but cause it keeps dropping out I wanted to try the Ethernet.

Its not appearing as an option in the network menu where my wireless connection strength icon thingy is.

 
**Result from 'lspci' in terminal**

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:08.0 Network controller: RaLink RT2561/RT61 rev B 802.11g



**Ipconfig gave me this:**

eth0      Link encap:Ethernet  HWaddr 00:17:31:E2:97:03  
          inet6 addr: fe80::217:31ff:fee2:9703/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1668 (1.6 KB)  TX bytes:492 (492.0 b)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:E8:94:EE  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:46ff:fee8:94ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2401671 (2.2 MB)  TX bytes:151900 (148.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-E8-94-EE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Can anyone possibly help?

---

### Post by njparton on 2008-03-11
You're ethernet connection is the "eth0" connector mentioned in the output above.

You're probably looking for it in the wrong place - it won't have a network strength, that's just for wifi connections.

Look under the network options in the menus at the top of the screen for your wired connections.

---

### Post by adammc on 2008-03-11
thanx for the quick reply :)
Its not listed there, only 'wireless network'

---

### Post by adammc on 2008-03-11
can anyone possibly help?

---

### Post by sillyxone on 2008-03-11
what do you mean "only wireless network"?

as Njparton pointed out, your ethernet (wired) interface is eth0, your wireless is wlan0.

but first, please do the preliminary step of checking the wire and switch/router, make sure that it's OK. You can try plugging it into a different computer to make sure that it's work. It'd waste time just to figure out later that the cable is bad or your router/switch is not responding to DHCP request.

---

### Post by adammc on 2008-03-11
hi,
when i click the wirleless icon statsu icon in the top of my screen it hasnt got an option of connecting via a wired connection / only 'wireless connection'

Im running a dual boot with xp, in xp the ethernet works fine. So I can only assume that the connection is ok.

However, the weird ting is that the option to connect via a 'wired connection' was showing 2 days ago?

---

### Post by adammc on 2008-03-11
Is the problem that I need a driver?

---

### Post by Eiríkr on 2008-03-11
Is there an ethernet cable plugged into your router on one end, and into your computer's ethernet port on the other?  If not, that's why you cannot see any wired connection in the Network Manager icon at the top of the screen -- you need to be physically plugged in before you can select it.  And please let us know if you can check the cable / router by hooking up to a different computer.  If you *can* hook up to a different computer, and that computer also fails to access the router via the cable, then you have an entirely different set of problems.  This is why we are asking you to do this -- we cannot identify what the issue is unless you can do this and give us some feedback.  

It's like when you talk to a doctor on the phone, they always insist on seeing you in person to identify your specific symptoms before making a diagnosis.  We can't see your computer in person, but we can at least get you to describe for us in better detail what is happening.  Otherwise, no one here can help you very well at all.  

Cheers,

Eiríkr

---

### Post by handydan918 on 2008-03-11
I built a box that had that damned nvidia ethernet controller on it, and I couldn't get it up no matter what I tried or how much I googled. I gave up and spent 4.99 USD at Fry's on a cheapo NIC, and it fired right up...

---

### Post by eebagum on 2008-03-11
You could try disabling the wireless card temporarily and see if the wired nic kicks in.

---

### Post by sillyxone on 2008-03-11
> **adammc said:**
> Is the problem that I need a driver?

since you are connecting OK in XP, and ifconfig listed eth0 correctly, I think it's just the connection manager.

try to run DHCP manually (sudo dhclient) and then ifconfig again to see if eth0 get an IP

if you are using Network Manager, try Wicd instead. I found Wicd much more easier to use.

---

### Post by adammc on 2008-03-12
OK, i got this from** 'sudo dhclient'**

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:46:e8:94:ee
Sending on   LPF/wlan0/00:13:46:e8:94:ee
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:17:31:e2:97:03
Sending on   LPF/eth0/00:17:31:e2:97:03
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.3 -- renewal in 1371 seconds.

**and this from ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:17:31:E2:97:03  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::217:31ff:fee2:9703/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1701679 (1.6 MB)  TX bytes:148019 (144.5 KB)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:E8:94:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4992 (4.8 KB)

wlan0:ava Link encap:Ethernet  HWaddr 00:13:46:E8:94:EE  
          inet addr:169.254.10.78  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-E8-94-EE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Eiríkr on 2008-03-12
In your first post, eth0 had no inet address entry in its [font=courier]ipconfig[/font] output.  Above, it does, so it looks like your [font=courier]sudo dhclient[/font] worked.  Can you access the internet now via the wired connection?  After rebooting, does [font=courier]ifconfig[/font] still show eth0 with the inet address, or has it reverted to wlan0?

---

