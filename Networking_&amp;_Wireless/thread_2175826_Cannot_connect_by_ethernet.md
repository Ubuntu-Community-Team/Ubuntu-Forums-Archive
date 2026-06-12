---
title: "Cannot connect by ethernet"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2013-09-21
Hi,

OS: Lubuntu 12.04

I am trying to connect to the internet via a wired connection on a computer which has not been connected to the Internet for some time (6 months?). I cannot browse the Internet and I am continually told that I am disconnected. 

Priorly though, I have connected using this computer by wired connection with the very same router and network parameters. I *can* connect via wired connection with the same router on another computer, and I *can* connect on this computer on a wireless connection to the same router.

Anybody know what might be going on?

Many thanks.

---

### Post by mikewhatever on 2013-09-21
You could post the output of ifconfig, or whatever parameters you were talking about. Otherwise, how should anyone know?

---

### Post by rdh61 on 2013-09-21
Dear Mikewhatever, very often technically knowledgeable people underestimate the level of ignorance possible in technically unknowledgeable people.

Here is the output of ifconfig:

robert@robert-workdesk:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:167106 (167.1 KB)  TX bytes:167106 (167.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:3f:ed:77:9e  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:feed:779e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1777630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1021329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2561926063 (2.5 GB)  TX bytes:191194838 (191.1 MB)

Many thanks.

---

### Post by mikewhatever on 2013-09-21
Yeah, sorry about that. 
So, the output doesn't show any ethernet interfaces (usually eth0). You'll need to digg a bit deaper, try "lspci" and "dmesg | grep eth" .

---

### Post by Warren Hill on 2013-09-21
Your wireless lan seems to be connecting to your router OK so the problem may be between your router and the ISP.

Can you provide the output from the following commands

```
lsb_release -a;ping-c5 8.8.8.8; route -n; nm-tool
```

but It does not show any wired connection what's  the output of

```
sudo lshw -C network
```

---

### Post by rdh61 on 2013-09-21
@ mikewhatever

```
robert@robert-workdesk:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)
03:02.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

```

```
robert@robert-workdesk:~$ dmesg | grep eth
robert@robert-workdesk:~$

```

---

### Post by rdh61 on 2013-09-21
@ Warren Hill

```
robert@robert-workdesk:~$ lsb_release -a;ping-c5 8.8.8.8; route -n; nm-tool
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise
ping-c5: command not found
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


NetworkManager Tool


State: connected (global)


- Device: wlan0  [WLAN_7A3C] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        00:22:3F:ED:77:9E


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *WLAN_7A3C:      Infra, 74:88:8B:C3:7A:3D, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA


  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1

```

```
robert@robert-workdesk:~$ sudo lshw -C network
[sudo] password for robert: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:bc00(size=256) memory:5fefff00-5fefffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:22:3f:ed:77:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-32-generic firmware=N/A ip=192.168.1.64 link=yes multicast=yes wireless=IEEE 802.11bg


```

---

### Post by mikewhatever on 2013-09-21
OK, how about the output of "dmesg | grep 8139"? The correct module for that NIC seems to be 8139too, so try loading it with
"sudo modprobe 8139too". Then check if it works, or if eth0 is in the output of ifconfig.

---

### Post by rdh61 on 2013-09-23
```
robert@robert-workdesk:~$ dmesg | grep 8139
[    1.775511] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.775582] 8139too 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.775604] 8139too 0000:03:02.0: Chip not responding, ignoring board
[    1.775619] 8139too 0000:03:02.0: PCI INT A disabled
[    1.775631] 8139too: probe of 0000:03:02.0 failed with error -5
```

Am I right in thinking that doesn't look too good?


```
robert@robert-workdesk:~$ sudo modprobe 8139too

```

Still doesn't work.


```

[sudo] password for robert: 
robert@robert-workdesk:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49241 (49.2 KB)  TX bytes:49241 (49.2 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:3f:ed:77:9e  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:feed:779e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2226154 (2.2 MB)  TX bytes:673697 (673.6 KB)

```

---

### Post by mikewhatever on 2013-09-23
Interesting output. I am no expert, but it might be broken. Let's wait and see what others think.
```

robert@robert-workdesk:~$ dmesg | grep 8139
[    1.775511] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.775582] 8139too 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.775604] 8139too 0000:03:02.0: Chip not responding, ignoring board
[    1.775619] 8139too 0000:03:02.0: PCI INT A disabled
[    1.775631] 8139too: probe of 0000:03:02.0 failed with error -5

```

---

### Post by varunendra on 2013-09-23
> **mikewhatever said:**
> Interesting output. I am no expert, but it might be broken. Let's wait and see what others think.
```

robert@robert-workdesk:~$ dmesg | grep 8139
[    1.775511] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.775582] 8139too 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.775604] 8139too 0000:03:02.0: **[COLOR="#FF0000"]Chip not responding[/COLOR], ignoring board**
[    1.775619] 8139too 0000:03:02.0: PCI INT A disabled
[    1.775631] 8139too: probe of 0000:03:02.0 failed with error -5

```

I concur with mikewhatever, the chip seems to be broken. If it is a PCI card, you may try pulling it out --> clean --> re-seat. If it is an onboard one, you may try resetting BIOS to defaults to make sure any IRQ issue is not causing that. If none of these help, it is most probably gone.

---

### Post by rdh61 on 2013-09-25
Thank you mikewhaterver and varunendra, It is a PCI card, dusting and re-seating no joy. I guess I'll have to buy another one. Can somebody please tell me (my ignorance is extreme), are there compatibility issues between PCI cards and mother boards (i.e. do I have to purchase a specific card designed for my board?) or are they pretty much universally compatible (like USB memory sticks)?

---

### Post by varunendra on 2013-09-25
Mind the size (full vs. half, whatever is applicable to you) and you should be okay if you purchase one from the retail market.

However, if purchasing from ebay, do some research beforehand. I've read many times that some brands encrypt the cards, while some (lenovo comes to mind) 'whitelist' some cards that can be used.

With the above being taken care of, a general list of cards supported in Linux can be found here : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Hope someone else can give you a precise and better advice.

Good luck !

---

### Post by rdh61 on 2013-09-26
Thank you for your reply Varun. The page you link to is actually about wireless cards, whereas the card that is an issue with me is an ethernet adapter. Is your preceding advice still valid?

---

### Post by varunendra on 2013-09-26
Wow, didn't know I can be so ignorant, this is the second post of the day where I suggested something stupid :redface:

Answer to your question - Nope! None of my last advice applies to ethernet cards as far as I know (except maybe the size thing). I have never heard of blacklisting/whitelisting issues with ethernet cards.

The only compatibility issues maybe the card vs pci slot's length (pci, pci-e etc.) and speed (1x, 16x etc.). You should be good to go with any Gigabit ethernet card that matches your PCI (or PCI-e) slot speed/specs. Realtek chips are pretty common and nicely supported, but so are others I guess.

Just make sure you don't buy some ultra-modern card which is not yet supported by linux drivers.

Once again, I hope for better inputs from others.

---

