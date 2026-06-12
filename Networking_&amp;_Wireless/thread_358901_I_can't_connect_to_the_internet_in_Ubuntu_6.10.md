---
title: "I can't connect to the internet in Ubuntu 6.10"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by mrmonday on 2007-02-11
Hi Everyone,

I recently decided to install Ubuntu 6.10. I have never used Linux before and would like some help.

I am having problems connection to the internet. In windows, I can connect wirelessly to my WPA-PSK secured wireless network, and I can also connect via an Ethernet cable. This allows me to have access to the internet and access to shared resources such as printers and folders.

In Ubuntu I have followed instructions in the support section of the site to connect wirelessly. Ubuntu picked up two wireless cards, (I only have one, a PCI Gigabyte Technology GN-WP01GS), Which I configured with my network settings. I launched Firefox, and was unable to connect to any site, not even my routers page. Using the network tools to ping computers didn't work either. After lots of messing around using different tutorials, (and lots of entering commands in the terminal, which I still have no idea of what they do), I remember using wifi radar and ndiswrapper. Ubuntu now picks up no wireless cards.

I plugged in an Ethernet cable, and I am now able to connect to my routers page and ping any IP address I enter. Both connections still work in windows and I have no idea what to do now.

Any help would be appreciated. Thanks in advance.

PS I think i posted this in the wrong place before which is why its here

---

### Post by floof on 2007-02-11
Hello,

When you try connect under linux, do you get an IP address from the server ?

to find out, connect using wifi-radar, and then :

```

user@host> sudo ifconfig

```

whats the output of this command ?

---

### Post by floof on 2007-02-11
> **mrmonday said:**
> 
and lots of entering commands in the terminal, which I still have no idea of what they do


whenever you'd like to know what a command does (let's say the ifconfig command above), just type :

```

user@host> man ifconfig

```

---

### Post by mrmonday on 2007-02-11
In wifi radar when I try to connect it says 'could not get IP address.'

the output from ifconfig is:

```
eth0      Link encap:Ethernet  HWaddr 00:14:2A:B1:E0:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

It does not seem to mention the wireless card. Note that the ethernet cable is currently unplugged.

---

### Post by mrmonday on 2007-02-11
In case it helps I ran ifconfig with the the ethernet cable plugged in, here are the results:
```
eth0      Link encap:Ethernet  HWaddr 00:14:2A:B1:E0:61  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:feb1:e061/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1598 (1.5 KiB)  TX bytes:1854 (1.8 KiB)
          Interrupt:217 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

Also if it helps, I believe that my card uses the Ralink RT61 chipset.

---

### Post by mrmonday on 2007-02-12
I have just seen another thread, which suggested using lspci to see if my device is listed, it returned:
```
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 81)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)
02:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
My card seems to be listed, but it still isn't listed in the networking section. Hope this helps.

---

