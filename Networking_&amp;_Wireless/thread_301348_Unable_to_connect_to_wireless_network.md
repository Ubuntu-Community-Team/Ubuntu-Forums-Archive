---
title: "Unable to connect to wireless network"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by 9mmCensor8aa on 2006-11-17
Ok, I am trying to connect to my wireless network at home with my laptop with a fresh install of Ubuntu 6.10.

I have a built in wireless card, broadcom chipset, its eth1.
I also have and want to use a Orinoco Gold card, its eth2.

iwconfig shows both cards.  Eth2 shows my ESSID as my networks name (its unprotected).  I am however unable to connect to anything.

What can I do from here to get this working?

---

### Post by frogotronic on 2006-11-17
> **9mmCensor8aa said:**
> Ok, I am trying to connect to my wireless network at home with my laptop with a fresh install of Ubuntu 6.10.

I have a built in wireless card, broadcom chipset, its eth1.
I also have and want to use a Orinoco Gold card, its eth2.

iwconfig shows both cards.  Eth2 shows my ESSID as my networks name (its unprotected).  I am however unable to connect to anything.

What can I do from here to get this working?

I've never done this, but do you have the correct firmware drivers installed for both cards/devices?  If so, you should get some kind of readout like this :

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"xxxx"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=189/100
          Rx invalid nwid:0  Rx invalid crypt:30  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

-ch

---

### Post by 9mmCensor8aa on 2006-11-17
> **cement_head said:**
> I've never done this, but do you have the correct firmware drivers installed for both cards/devices?  If so, you should get some kind of readout like this :

Yeah, it tells me all about the card nickname "Hermes I" and all the other headings have a value and its on on the supported device list and it says it should just work.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

But it still doesn't.

I noticed that near the time in the top right, there is a icon of two computers and when I mouse over it it says Network Connection lo.  Should there be a icon like that for eth2?

---

### Post by frogotronic on 2006-11-17
Hi,

Okay, that's good, because often that is the problem.  What you need is the ability to switch network on the fly.  I use the NetworkMangerApplet ( [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) ).  Just choose "Add to panel" and you'll find it there.  It should come up as a small icon with cingular type bars. Left click on it and choose your network.  I can't remember if networkmanager is automatically installed with dapper; I might have installed it via Synaptic.

If you don't see anything like what I described, or is on the gnome networkmanager applet website (above link); go into Network Monitor (different program) and choose the wireless device you want to use.  You may then be asked to configure the wireless device.  

-ch

---

### Post by heikkitoivonen on 2006-11-17
I think I might be having the same problem: [http://ubuntuforums.org/showthread.php?t=300004](http://ubuntuforums.org/showthread.php?t=300004)

As far as I can tell everything is working in my case, it just does not connect to wireless at my home location. Maybe interference from other wireless networks? Any debugging tools to find that out?

---

### Post by frogotronic on 2006-11-17
> **heikkitoivonen said:**
> I think I might be having the same problem: [http://ubuntuforums.org/showthread.php?t=300004](http://ubuntuforums.org/showthread.php?t=300004)

As far as I can tell everything is working in my case, it just does not connect to wireless at my home location. Maybe interference from other wireless networks? Any debugging tools to find that out?

this will sound stupid, but:

1) turn off & unplug your router

2) turn off & unplug DSL modem or Cable modem

3) wait fifteen minutes

4) turn on your modem

5) wait a couple of minutes for it to connect

6) turn on your router

7) boot your linux box.

Sometimes my wireless won't work on my Linux laptop, doing the above steps solves the problem everytime (maybe once a month).

-ch

---

### Post by dbott67 on 2006-11-17
I have a few questions:

1. Do you want to use both cards simultaneously?  If you do, you would need to '[bond]("http://www.ubuntuforums.org/showthread.php?p=1661684&highlight=bonding#post1661684")' the cards together, otherwise the computer would not know which interface to use.

2. Can you post the output of the following commands:
```
iwlist scanning
```
```
dbott@dapper:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:B2:YY:XX
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-48 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.
```

The output of **cat /etc/network/interfaces**:

```
dbott@dapper:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

and **route -n**:
```
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by Elvish Legion on 2006-11-17
It appears I am having the same problem

jduvall@jduvall-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      No scan results
sit0      Interface doesn't support scanning.

jduvall@jduvall-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface wlan0 inet dhcp
wireless-essid Chef at home
wireless-key superuberkey!









auto wlan0

iface ath0 inet dhcp
wireless-essid Chef at home
wireless-keySuperubersecertkey





auto eth0

auto ath0
jduvall@jduvall-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
jduvall@jduvall-laptop:~$

---

### Post by dbott67 on 2006-11-17
From your post above, it looks like your wireless interface is ath0, not wlan0.
```
iwlist scanning
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

**[COLOR="Red"]ath0 No scan results[/COLOR]** [COLOR="Blue"]<--- when you look in your /etc/network/interfaces file, the card is not automatically activated (via the [COLOR="Red"]auto ath0[/COLOR] command)[/COLOR]
sit0 Interface doesn't support scanning.
```

Try this:
```
sudo ifup ath0
```
```
sudo dhclient ath0
```

Post the output of:
```
iwlist scanning
```

If it works, modify your /etc/network/interfaces to:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

[I][COLOR="Blue"]auto wlan0
iface wlan0 inet dhcp
wireless-essid Chef at home
wireless-key superuberkey![/COLOR][/I]
[COLOR="Red"]# The wlan0 is probably not needed[/COLOR]

**[COLOR="Red"]auto ath0[/COLOR]**
iface ath0 inet dhcp
wireless-essid Chef at home
wireless-keySuperubersecertkey
```

-Dave

---

### Post by Elvish Legion on 2006-11-18
jduvall@jduvall-laptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 5325
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ath0/00:16:cf:73:c2:af
Sending on   LPF/ath0/00:16:cf:73:c2:af
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jduvall@jduvall-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      No scan results
sit0      Interface doesn't support scanning.

jduvall@jduvall-laptop:~$

---

### Post by dbott67 on 2006-11-18
What kind of wireless card do you have?
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
       resources: ioport:d000-d0ff iomemory:ed800000-ed8000ff irq:185

```

---

### Post by 9mmCensor8aa on 2006-11-21
Hi thank you all for your replys, but none of these suggestions got it to work, someone who never used Linux before did.  

I had my computer shut off, someone turned it on, said "Oh this looks different" and opened up FF and it worked.  Like magic.  And it hasn't stopped working, and works great now, so I think I am going to just let it work and not fiddle with it, lest I break it.

Thanks anyways,
9mmCensor

---

