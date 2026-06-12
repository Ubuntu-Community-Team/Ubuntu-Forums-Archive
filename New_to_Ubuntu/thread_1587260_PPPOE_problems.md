---
title: "PPPOE problems"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Falc7 on 2010-10-03
Trying to connect to a PPPOE network, i put sudo pppoeconfig into the terminal, followed all the instructions, putting in the name of the network and the password, and followed recommended settings.
 
But there is no way to connect to the network now that i have done that, and on top of that, the network indicatior (not sure quite what its called) in the top right hand corner of the screen has dissappeared

---

### Post by andrewthomas on 2010-10-03
let the router/modem handle the connection.

[http://ubuntuforums.org/showthread.php?t=1582853](http://ubuntuforums.org/showthread.php?t=1582853)

---

### Post by Falc7 on 2010-10-03
I am in China, their internet setup seems to be different here, there dosen't seem to be a router as such, its just an adsl cable, going into this tiny grey box, smaller than a pack of cards, and then another wire going into the wall. Guessing that tiny grey box is the modem, i'll try and find out the right number to change its settings

---

### Post by Falc7 on 2010-10-04
I am having some trouble finding the right number to log into the modem, and i have a feeling that even if i am sucessfull, all the options will be in Chinese anyway. Is there a way to set it up from within ubuntu? Or at least get my network indicator applet back?

---

### Post by dineshs on 2010-10-04
Try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2").
If there is no progress post the result of ```
sudo lshw -C network
```

---

### Post by Falc7 on 2010-10-04
I did as you said, i have got the network applet back now :)

But it still won't connect to the network, I followed the instructions exactly

```
song@song-laptop:~$ sudo lshw -C network 
[sudo] password for song:  
  *-network:0              
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:03:02.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 
       resources: irq:21 memory:b0200000-b0201fff 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:03:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:0f:b0:75:63:a9 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s 
       resources: irq:22 ioport:a000(size=256) memory:b0203000-b02030ff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:90:4b:f4:a4:a8 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
```

---

### Post by dineshs on 2010-10-05
Please run```
sudo dhclient eth0
```and post the output
> Guessing that tiny grey box is the modemIs there a model name or number on the device?

---

### Post by Falc7 on 2010-11-06
I've only just been able to access the computer in question again, here is the output:

song@song-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:0f:b0:75:63:a9
Sending on   LPF/eth0/00:0f:b0:75:63:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
song@song-laptop:~$ 

I would really like to be able to connect ubuntu to the internet for this computer, the windows partition is a pain to deal with, even though it is able to access the internet. No make or model on the router

---

### Post by dineshs on 2010-11-06
what is the output of ```
ipconfig /all
```in[COLOR="Red"] windows[/COLOR]
Note:You may try
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
Now connect and see if it works.If not post the result of```
ping 4.2.2.1 -c3
```

---

### Post by Falc7 on 2010-11-06
The contents of that thread didn't work for me, here is the result:
```
song@song-laptop:~$ ping 4.2.2.1 -c3
connect: Network is unreachable
```

```
Microsoft Windows XP [&#29256;&#26412; 5.1.2600]
(C) &#29256;&#26435;&#25152;&#26377; 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrator>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : PC2010082713kcu
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter &#26412;&#22320;&#36830;&#25509;:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physical Address. . . . . . . . . : 00-0F-B0-75-63-A9
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.166.97
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

Ethernet adapter &#26080;&#32447;&#32593;&#32476;&#36830;&#25509;:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Dell TrueMobile 1300 WLAN Mini-PCI
&#21345;
        Physical Address. . . . . . . . . : 00-90-4B-F4-A4-A8

PPP adapter &#23485;&#24102;:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 119.4.54.219
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 119.4.54.219
        DNS Servers . . . . . . . . . . . : 119.6.6.6
                                            221.10.251.52
        NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Documents and Settings\Administrator>^A^Aipconfig /all
```

---

### Post by dineshs on 2010-11-06
Just do (do not run pppoeconf again) ```
sudo pon dsl-provider
```wait for a minute and see ```
ping 4.2.2.1 -c3
```gets reply

---

### Post by Falc7 on 2010-11-28
This is the output

```
song@song-laptop:~$ sudo pon dsl-provider 
[sudo] password for song:  
Plugin rp-pppoe.so loaded. 
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5 
song@song-laptop:~$ ping 4.2.2.1 -c3 
connect: Network is unreachable 

```

---

### Post by Falc7 on 2011-02-02
bump

---

### Post by dineshs on 2011-02-02
After running sudo pon dsl-provider what do you get for ```
ifconfig -a
```?

---

### Post by Falc7 on 2011-02-03
hi here is the output:

```
song@song-laptop:~$ sudo pon dsl-provider 
[sudo] password for song:  
Plugin rp-pppoe.so loaded. 
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5 
song@song-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:75:63:a9   
          inet6 addr: fe80::20f:b0ff:fe75:63a9/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:5490 (5.4 KB)  TX bytes:1440 (1.4 KB) 
          Interrupt:22 Base address:0xa000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1104 (1.1 KB)  TX bytes:1104 (1.1 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:90:4b:f4:a4:a8   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
song@song-laptop:~$  
```

---

### Post by dineshs on 2011-02-04
perhaps ```
plog
``` can tell us why the connection was not established.Are you trying via wired or wireless?What is the output of```
sudo cat /etc/ppp/peers/dsl-provider
```

---

### Post by Falc7 on 2011-02-08
I am trying through a wired connection, in windows I just put the wire in, then bring set up the connection and put the username and password in, and it connects.

Its actually my girlfriend's mother's laptop I am trying to set this up on, so I can only try stuff on the machine when I am at their house

---

