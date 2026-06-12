---
title: "can't connect to wireless network"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Tectuktitlay on 2006-11-19
Hi,

I'm having trouble connecting to my wireless network. I'm new to Ubuntu and Linux in general, so maybe my questions have been answered a million times already, but I've been looking through the forum all day and am no closer to fixing it.

I've got an adsl-router set up, with these settings:

```
Interface Enabled:	Yes
Physical Address:	00:11:F5:78:FF:ED
Network Name (SSID):	Nightwork
Interface Type:	802.11b/g
Actual Speed:	54 Mbps
Channel Selection:	Auto
Region:	Europe
Channel:	1
Allow multicast from Broadband Network:	Yes

Broadcast Network Name:	Yes
Allow New Devices:	New stations are allowed (automatically)
Use WEP Encryption:	Yes
WEP Encryption Key:	hello
Use WPA-PSK Encryption:	No
```

Iwconfig says:

```
lo        no wireless extensions.

wlan0     802.11b linked  ESSID:"Nightwork"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:78:FF:ED
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-111 dBm  Noise level=-246 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
```

Does this mean that wlan0 can at least see the network and the router?

ifconfig says:

```
eth0      Link encap:Ethernet  HWaddr 00:11:09:1E:48:0E
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe1e:480e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5892017 (5.6 MiB)  TX bytes:3005524 (2.8 MiB)
          Interrupt:209 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9384 (9.1 KiB)  TX bytes:9384 (9.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:50:FC:F2:34:CE
          inet6 addr: fe80::250:fcff:fef2:34ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1268 errors:0 dropped:572 overruns:0 frame:0
          TX packets:454 errors:235 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:461269 (450.4 KiB)  TX bytes:68344 (66.7 KiB)
          Interrupt:193 Memory:ffffc200000b8f00-ffffc200000b9000
```

It seems to me that wlan0 cannot obtain an ip by dhcp. eth0 is how I'm connected to the internet now, but I'd really rather lose the cable.

I've tried ```
iwconfig wlan0 essid Nightwork key s:hello
```, but it doesn't help.

Here is /etc/network/interfaces:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid Nightwork
wireless-key s:hello




auto wlan0

auto eth0
```

I hope anyone can help me or tell me what I'm doing wrong. My windows installation picks up the network effortlessly. Even my ancient old w98 laptop can access it.

Greetz,

Maarten

---

### Post by dbott67 on 2006-11-19
Try turning off encryption to see if you can make the connection.  If you are able to connect, then we know the problem is with WEP and we can proceed from there.

If you check [this thread (post #10 & #11)]("http://www.ubuntuforums.org/showthread.php?t=296394"), I provide a little walk-through on verifying if it's the encryption that is causing the problem.

-Dave

---

### Post by Tectuktitlay on 2006-11-19
Hello Dave,

Thanks for your help.
What I've done is:

1. turned off encryption on the router
2. deleted "wireless-key s:hello" from the wlan0 entry in /etc/networking/interfaces
3. ifdown wlan0
4. ifup wlan0

Results of ifup wlan0:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:50:fc:f2:34:ce
Sending on   LPF/wlan0/00:50:fc:f2:34:ce
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

It seems wep is not the problem.

Maarten

---

### Post by TasKiNG on 2006-11-19
I had the same messages and it wouldent connect.
Not sure if your using a USB wifi adapter but I am and found if I boot up then unplug it and plug it back in again it then connects after about 20 secs.

Doing it this way it worked perfectly with WEP enabled.

The only other thing I had to do was put the info in the /etc/network/interfaces file like you have done already.
I was using 128 bit wep key entered as HEX i.e.

iface wlan0 inet dhcp
wireless-essid Dreamnet
wireless-key 1f1d2e2d3f4d2f1df3d2f1d2f2

---

### Post by dbott67 on 2006-11-19
Hi Maarten,

Sometimes the router can get hung also... try TasKiNG's suggestion, as well as just resetting or cycling the power on your router.

I notice you're using channel 1 on the router... any particular reason?  You can try channel 6 (unless it's overwhelmed with other APs).

Also, distance can be a factor... try moving as close to the AP as possible.  Any sort of interference can cause problems (cordless phones, cell phones, microwave ovens, other wireless devices).  I can't connect if the cordless phone in my house is being used.

Another thing to try is setting the wlan0 IP address to static, as opposed to DHCP.

Do you have any restrictions set on your router, such as MAC address filtering, limited DHCP addresses, or whatever.

---

### Post by andreas64 on 2006-11-19
Hi, 

maybe there is a problem with your DHCP-service. Try to set a static IP-adress for your computer

Andreas

EDIT: oops, dbott67 was faster:)

---

### Post by dbott67 on 2006-11-19
> **andreas64 said:**
> EDIT: oops, dbott67 was faster:)

FINALLY!!!! :)

---

### Post by Tectuktitlay on 2006-11-19
Hi everyone,

Thanks for all your advise. It's really great to receive so much response and help. Kudos for this forum and its members!

I may be on to something:

I tried all your suggestions, but what seemed to work is assigning a static IP-adress, which I tried to do like this:

```
ifconfig wlan0 192.168.1.50
```

I just guessed an address within the range of the router.

Then I tried pinging the router avoiding the cable with the -I option.

```
~# ping -I wlan0 192.168.1.254
PING 192.168.1.254 (192.168.1.254) from 192.168.1.50 wlan0: 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=10 ttl=64 time=6.57 ms

--- 192.168.1.254 ping statistics ---
22 packets transmitted, 1 received, 95% packet loss, time 21023ms
rtt min/avg/max/mdev = 6.573/6.573/6.573/0.000 ms

```

It says only 1 packet is received! Maybe the problem is signal-strength. But the antennas are less than one meter apart. Under windows the signal strength is maximum.

Anyway, I still don't have a proper connection.

Gr,

Maarten

---

### Post by dbott67 on 2006-11-19
It might be interference...

What's the make and model of the router?

Also, can you post the output of **sudo lshw -C network** and **route -n**.
```
dbott@edgy:~$ sudo lshw -C network
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
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185
```
```
dbott@edgy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
dbott@edgy:~$ 
```

-Dave

---

### Post by dbott67 on 2006-11-19
Also, can you change the router to a different channel than 1.  Channel 6 would be preferable.
```
Interface Enabled:	Yes
Physical Address:	00:11:F5:78:FF:ED
Network Name (SSID):	Nightwork
Interface Type:	802.11b/g
Actual Speed:	54 Mbps
Channel Selection:	Auto
Region:	Europe
**[COLOR="Red"]Channel:	1[/COLOR]**
Allow multicast from Broadband Network:	Yes

Broadcast Network Name:	Yes
Allow New Devices:	New stations are allowed (automatically)
Use WEP Encryption:	Yes
WEP Encryption Key:	hello
Use WPA-PSK Encryption:	No
```

-Dave

---

### Post by Tectuktitlay on 2006-11-20
Hi Dave,

Inspired by TasKiNG's suggestion I took my wlan-card out of my computer and plugged it back in after having my computer boot up once. Everything seems to work fine now...

I don't understand it. Maybe it wasn't plugged in properly before. But you'd think you'd notice under windows.

Gr,

Maarten

---

### Post by dbott67 on 2006-11-20
Hi Maarten,

Glad it's working.

What king of card is it?  USB or PCCard / PCMCIA?

If you can post as much detail about your card and router, it may help others who end up searching this thread.

Thanks,
Dave

---

### Post by Tectuktitlay on 2006-11-23
Hi Dave,

Thanks for you all your help.

Information about the router:

```

System Information    
            
Product Name: SpeedTouch 716
Serial Number: 0528JTL69
Software Release: 5.3.2.6.0
Software Variant: AA
Boot Loader Version: 1.0.1
Product Code: 35920420
Board Name: BANT-T

```

Information about the network adapter (lshw):

```

  *-network:0
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@00:07.0
       logical name: wlan0
       version: 20
       serial: 00:50:fc:f2:34:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.64 multicast=yes wireless=802.11b linked
       resources: ioport:d400-d4ff iomemory:cfffbf00-cfffbfff irq:193

```

By the way, the router does not allow you to change the channel. It is fixed to 1, at least in its friendly web-based interface.

Greetz,

Maarten

---

