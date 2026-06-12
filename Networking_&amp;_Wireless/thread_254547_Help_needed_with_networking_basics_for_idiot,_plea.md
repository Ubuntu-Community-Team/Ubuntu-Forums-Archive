---
title: "Help needed with networking basics for idiot, please"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2006-09-10
As the title says...

Here are the details + a silly little diagram just to help clarify the way different parts are associated.


The wireless connection between router/modem and desktop is not a problem. Have had it in place for a couple of years. Due to distances I don't intend to run any LAN cables (the desktop and phone point where the router is plugged in couldn't be further apart).

I've bought an old 2nd hand laptop for my non computer friendly partner to use for email and net but don't know about subnets, gateways , etc. and what IP numbers I should be setting in the first instance and what firewall considerations I'll come across either in setting the laptop up wirelessly on it's PCMCIA wifi device.

I know therefore I need to be sure I've configured the IP addresses etc correctly before I can move on but don't know how to do that .

---

### Post by linuxusr50 on 2006-09-10
As long as the laptop recignizes the network card you should be able to get a DHCP IP address that will be dished out from your router.  If you don't get an IP try running the following commands at a terminal window.

```
sudo ifup -a
```
```
sudo dhclient
```

and finally

```
ifconfig
```
to see if you are pulling a good IP from your router.

---

### Post by alanmzifa on 2006-09-10
Thanks for replying.

I'm posting from my desktop now.

Will post from the laptop (will connect vis LAN to the router) in a few minutes and copy/paste the terminal output.

---

### Post by alanmzifa on 2006-09-10
sudo ifup -a 

> joyce@joyce-desktop:~$ sudo ifup -a
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
joyce@joyce-desktop:~$

sudo dhclient   (when laptop conneted to router via LAN)

> joyce@joyce-desktop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:17:31:9c:8c:8d
Sending on   LPF/ra0/00:17:31:9c:8c:8d
Listening on LPF/eth2/00:06:5b:30:bc:3b
Sending on   LPF/eth2/00:06:5b:30:bc:3b
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.5 -- renewal in 38869 seconds.
joyce@joyce-desktop:~$

ifconfig

> joyce@joyce-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:06:5B:30:BC:3B
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe30:bc3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2219255 (2.1 MiB)  TX bytes:734355 (717.1 KiB)
          Interrupt:10 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

ra0       Link encap:Ethernet  HWaddr 00:17:31:9C:8C:8D
          inet6 addr: fe80::217:31ff:fe9c:8c8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:4 dropped:4 overruns:0 carrier:0
          collisions:14 txqueuelen:1000
          RX bytes:77445 (75.6 KiB)  TX bytes:38100 (37.2 KiB)
          Interrupt:10

joyce@joyce-desktop:~$


---

### Post by alanmzifa on 2006-09-10
and just for completeness (if there is such a word), here is *ipconfig/all* from my Windows XP desktop. 
The Bluetooth adapter has nothing to do with the network in case you were wondering. It's just a device for syncing my mobile phone.


> Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Monty>ipconfig/all

Windows IP Configuration

Host Name . . . . . . . . . . . . : office
Primary Dns Suffix . . . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

Media State . . . . . . . . . . . : Media disconnected
Description . . . . . . . . . . . : VIA Compatable Fast Ethernet Adapter

Physical Address. . . . . . . . . : 00-0C-76-56-ED-63

Ethernet adapter Local Area Connection 3:

Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Bluetooth PAN Network Adapter
Physical Address. . . . . . . . . : 10-11-11-11-11-11
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.50.1
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . :
DHCP Server . . . . . . . . . . . : 192.168.50.10
DNS Servers . . . . . . . . . . . : 127.0.0.1
Lease Obtained. . . . . . . . . . : 10 September 2006 10:05:38
Lease Expires . . . . . . . . . . : 19 January 2038 04:14:07

Ethernet adapter Wireless Network Connection:

Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : NETGEAR WG121 802.11g Wireless USB2.
0 Adapter
Physical Address. . . . . . . . . : 00-09-5B-D1-42-5D
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.0.2
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.0.1
DHCP Server . . . . . . . . . . . : 192.168.0.1
DNS Servers . . . . . . . . . . . : 127.0.0.1
192.168.0.1
Lease Obtained. . . . . . . . . . : 10 September 2006 12:16:25
Lease Expires . . . . . . . . . . : 11 September 2006 12:16:25

C:\Documents and Settings\Monty>


---

### Post by linuxusr50 on 2006-09-10
You are not getting a lease on the wireless.

Could you please post the results from:

```
iwconfig
```

Could be the wireless adapter is not set up.  This will tell us.

---

### Post by alanmzifa on 2006-09-11
here's *iwconfig*


> joyce@joyce-desktop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"W office"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:09:5B:CD:08:38
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level=-77 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

joyce@joyce-desktop:~$


and here's a screenshot I took at the same time showing the GUI. It shows a connection for ra0, if it's to be trusted.

---

### Post by alanmzifa on 2006-09-11
ifconfig now shows this when I connect the laptop to the router via a LAN, PCMCIA also plugged in.

I configured ra0 via static instead of dhcp.

ra0 now has an IP address showing 192.168.0.5.but when I disconnect the LAN I can't get an internet page to load.



> joyce@joyce-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:06:5B:30:BC:3B
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe30:bc3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2240267 (2.1 MiB)  TX bytes:438589 (428.3 KiB)
          Interrupt:10 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4473 (4.3 KiB)  TX bytes:4473 (4.3 KiB)

ra0       Link encap:Ethernet  HWaddr 00:17:31:9C:8C:8D
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe9c:8c8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:52 txqueuelen:1000
          RX bytes:24044 (23.4 KiB)  TX bytes:89004 (86.9 KiB)
          Interrupt:10 Base address:0x4000

joyce@joyce-desktop:~$

---

### Post by linuxusr50 on 2006-09-11
Interesting.  Looks like you assigned a static address in your dhcp pool and Eth2 grabbed the same address as your wireless network card. You may want to try assigning a static IP outside of the DHCP range of your router.

---

### Post by alanmzifa on 2006-09-12
When I connect the laptop to the router with the LAN it seems to assign itself the address 192.168.0.5 .

I've tried using that same IP (192.168.0.5) and assigning it manually to the PCMCIA wifi card (ra0 above) as it doesn't detect a dhcp lease so won't connect when set to dchp. Anyway, I couldn't ge web pages to load when I disconnected the LAN even though the PCMCIA seemed to be showing a signal strength bar.

Should I have assigned another IP address and if so what should I use or have I been correct in assigning that IP when configuring the PCMCIA card? 

> You may want to try assigning a static IP outside of the DHCP range of your router.

I don't know what that means. Well, I know how to assign an IP address manually to the PCMCIA card but which value should I use for it. I don't understand "out of DHCP range".

---

### Post by mips on 2006-09-12
Looks like your eth2 and ra0 have addresses in the same subnet. What happens when you disconnect the et2 ?

Have you setup any security encryption like WEP etc ?

---

### Post by alanmzifa on 2006-09-12
I set a static route up on the PCMCIA card with 192.186.0.5 set as the IP of the laptop, 255.255.255.0 as the subnet ans 192.168.0.1 as the gateway (I don't really know what those terms mean).

As I said in the previous post (maybe a bit ambiguously) when I disconnect the ethernet cable for eth2 I can't get any web pages to load.

I've got a screen-shot of ra0 signal strength (presumably meaning it's making some sort of connection even though no IP address shows for ra0 unless statically assigned). It's attached to post 7. It sits at idle for most of the time but it flashs to active for split seconds.

I have WEP 128 bit on. Managed. ascii. open.

---

### Post by linuxusr50 on 2006-09-12
alanmzifa:

What I was refering to was that most routers hand out IP's via DHCP from a range that is assigned by the router administrator.

Most consumer routers have a range of 50 IP's they will give you by default leaving approx 200 address that you can assign statically without conflicting (having two adapters fighting over the same address).

Going by the IP that your adapters picked up (192.168.0.5) I am guessing that your router is assigning IP's 192.168.0.2 through 192.168.0.50, or something close to that.

So what I am suggesting is that you add the following to your /etc/network/interfaces file, to give your adapter an IP that will not be conflicting with the range your routers DHCP server is using to hand out DHCP addresses.

The following should assign a static IP of 192.168.0.150 to your ra0 adapter.


```
sudo gedit /etc/network/interfaces
```

> auto ra0

#wireless network interface ra0
iface ra0 inet static
     wireless-mode managed
     wireless-essid youressid
     address 192.168.0.150
     netmask 255.255.255.0
     gateway 192.168.0.1

After you have saved this edit.  Run the command:

```
sudo ifdown ra0
```
then
```
sudo ifup ra0
```

This should cause the /etc/network/interfaces file to be reread and hopefully bring up your adapter on a static IP of 192.168.0.150

You should be able to verify if it worked by running:

```
ifconfig
```

---

### Post by alanmzifa on 2006-09-12
thanks for explaining that.

I did what you suggested and the interfaces file was edited. The new settings were confirmed in ifconfig but the activity light on the card went out. The GUI showed c.90% signal strength and 1 received packet and 20000 sent packets after a few minutes.

WEP was on but I tried with WEP off also. No change.

Does that eliminate anything else?


I might try tinkering again tomorrow evening (late here now 1am) and I can try any new suggestions left tonight.

thanks

---

### Post by alanmzifa on 2006-09-12
Actually I tinkered a bit rather than went to bed.

I tried 192.168.0.6 in the configuration, no WEP.

and.....I'm posting from the laptop wirelessly now!!


...but, of course, no WEP.  


Have you any suggestions for getting WEP to work?

(and thanks for the help so far, much appreciated).

Here are the screen-shots of the configuration (ipv4 protocol, not ipv6, is this significant?)

---

### Post by linuxusr50 on 2006-09-13
1.  Make sure wep is turned on in the router and you have a 128 bit (26 Hex characters) key set.  Note:  Some routers require a reboot (powercycle) after setting the key.

2.  On the laptop do the following, and also note the key I used should be replaced by your specific key.
```
sudo iwconfig ra0 key ABCDEF0123456789ABCDEF1234
```

```
sudo iwconfig ra0 key on
```

See if that works.

---

### Post by alanmzifa on 2006-09-13
The sudo command via terminal didn't work to change the key but I *was* able to do it using the GUI tool.

So, I now have wireless working!! 

I had been using an ascii key on 128 bit WEP, automatic. Didn't work.

Changed it to hexadecimal key on 128 bit WEP, open. Works like a dream (since 5 minutes ago anyway). Faster than my XP desktop.


Thanks for your help and patience **linuxusr50**.

---

