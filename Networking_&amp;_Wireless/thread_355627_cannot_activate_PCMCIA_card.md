---
title: "cannot activate PCMCIA card"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by cari on 2007-02-07
Hi,

I have read through dozens of tutorials, but nothing seems to fit, can anyone help?
Heres the deal:

I have HP omnibook, it has canyon cn-wf513 wireless pcmcia card.

Previously I had ubuntu 6.06 and it worked ok, then I installed xubuntu 6.06 and still ok. After upgrading to xubuntu 6.10, I cannot activate the card. The interesting thing is that if I type

sudo iwlist scan

then
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:14:7F:26:B9:A0
                    Mode:Managed
                    ESSID:"SpeedTouchC2FB9D"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-24 dBm  Noise level:-205 dBm
          Cell 02 - Address: 00:14:7F:78:B4:B2
                    Mode:Managed
                    ESSID:"SpeedTouch8275E7"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-75 dBm  Noise level:-204 dBm
          Cell 03 - Address: 00:14:7F:25:6F:A4
                    Mode:Managed
                    ESSID:"SpeedTouchA3167F"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-74 dBm  Noise level:-204 dBm
          Cell 04 - Address: 00:A0:C5:65:A4:02
                    Mode:Managed
                    ESSID:""
                    Encryption key:off
                    Channel:6
                    Quality:0/100  Signal level:-86 dBm  Noise level:-205 dBm
          Cell 05 - Address: 00:14:BF:6B:A6:AE
                    Mode:Managed
                    ESSID:"linksys"
                    Encryption key:off
                    Channel:6
                    Quality:0/100  Signal level:-93 dBm  Noise level:-206 dBm

```

ifconfig -a

```

eth0      kapseldus:Ethernet  HWaddr 00:E0:98:35:4E:39  
          inet aadress:192.168.1.65  bcast:192.168.1.255  mask:255.255.255.0
          inet6 aadr: fe80::2e0:98ff:fe35:4e39/64 skoop:ühendus
          UP BROADCAST RUNNING MULTICAST  MTU:1540 meetrika:1
          RX pakette:5182 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:4103 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:1000 
          RX baite:3674609 (3.5 MiB)  TX baite:651680 (636.4 KiB)

lo        kapseldus:Kohalik loopback  
          inet aadress:127.0.0.1  mask:255.0.0.0
          inet6 aadr: ::1/128 skoop:host
          UP LOOPBACK RUNNING  MTU:16436 meetrika:1
          RX pakette:0 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:0 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:0 
          RX baite:0 (0.0 b)  TX baite:0 (0.0 b)

[COLOR="Red"]ra0       kapseldus:Ethernet  HWaddr 00:10:A7:2C:B9:7C  
          inet6 aadr: fe80::210:a7ff:fe2c:b97c/64 skoop:ühendus
          UP BROADCAST RUNNING MULTICAST  MTU:1500 meetrika:1
          RX pakette:0 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:17779 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:1000 
          RX baite:0 (0.0 b)  TX baite:711160 (694.4 KiB)
          katkestus:10 baasaadress:0x4000 [/COLOR]

sit0      kapseldus:IPv6-in-IPv4  
          NOARP  MTU:1480 meetrika:1
          RX pakette:0 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:0 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:0 
          RX baite:0 (0.0 b)  TX baite:0 (0.0 b)

```

sudo network-admin

shows Wireless connection, which is configured and "can be enabled" but nothing is happening after enabling. My USB ethernet driver works fine.

Can someone help and tell me how to get life back in my wireless card. Thanks in advance!

Oh btw, I downloaded the newest ralink rt2500 drivers, which, I read from somewhere, should do the trick, but no avail.

---

### Post by Floppyjoe on 2007-02-07
Have you tried disabling your ethernet connection and then issuing a:
```
sudo dhclient ra0
```

---

### Post by cari on 2007-02-07
sudo dhclient ra0

```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:10:a7:2c:b9:7c
Sending on   LPF/ra0/00:10:a7:2c:b9:7c
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

As I understand this means that my card cannot get DHCP from the router. Question arises, why? I mean, the settings are the same as they were with ubuntu and xubuntu 6.06.

There was a case with xubuntu 6.06 when router was shut down and then enabling "worked" the same way, nothing happened, no led on the card was lit.

---

### Post by Floppyjoe on 2007-02-07
I am assuming this is a laptop you are using. So are you using it just at one network or do you roam around with it? What program do/were you using to connect with it?

The sudo dhclient ra0 could fail if the /etc/network/interfaces file is not set up properly.

---

### Post by cari on 2007-02-07
interfaces:

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

auto wlan0
iface wlan0 inet dhcp

auto eth0

iface ra0 inet dhcp
wireless-essid SpeedTouchC2FB9D
wireless-key **********

auto ra0

```
..and router says:

WLAN: SpeedTouchC2FB9D
(54Mbps)

And still the same case..

Right now I have to enter essid name manually, previously network-admin offered available networks.

edit:
I use my laptop only in home network.

---

### Post by Floppyjoe on 2007-02-07
Try adding:
```
wireless-mode managed
```
to your /etc/network/interfaces file to get something like this:
```
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

auto ra0
iface ra0 inet dhcp
wireless-essid SpeedTouchC2FB9D
wireless-mode managed
wireless-key **********

```

---

### Post by cari on 2007-02-07
First of all, thanks for quick responses

but

added the wireless-managed to interfaces and rebooted. Still no avail:(

---

### Post by Floppyjoe on 2007-02-07
> **cari said:**
> First of all, thanks for quick responses

but

added the wireless-managed to interfaces and rebooted. Still no avail:(

You mean wireless-mode managed right? Not wireless-managed.

---

### Post by cari on 2007-02-07
My bad, not wireless-managed but

wireless-mode managed

but it did not work.

---

### Post by Floppyjoe on 2007-02-07
What type of encryption are you using? Wep or Wpa?

---

### Post by cari on 2007-02-07
wep key

---

### Post by Floppyjoe on 2007-02-07
Try adding another line into your /etc/networking/interfaces file:
```
sudo gedit /et/network/interfaces
```
add the line:
```
wireless-channel 6
```
where you enter the channel of your router to get something like this:
```
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

auto ra0
iface ra0 inet dhcp
wireless-essid SpeedTouchC2FB9D
wireless-channel 6
wireless-mode managed
wireless-key **********
```

I think it should work then after a reboot.

---

### Post by cari on 2007-02-08
Neither adding the channel has an effect.

I started to think that could there be a "sleep mode on" or something.
As I run

```
sudo iwconfig ra0 power on
```

the terminal responses: Error for wireless request "Set Power Management" (8B2D) :
    GET failed on device ra0 ; Operation not supported.

I'm still in a dead-end situation, theres not much more to configure. Maybe the only solution would be to install xubuntu 6.10 from scratch, since there could have been a problem during the update (my browsers homepage says, "welcome to xubuntu 6.06")

---

### Post by cari on 2007-02-08
Thanks for all the help, but I could not resist the urge to use a fresh install which did the job to be honest. 

Most probably I messed something up with the upgrade.

Case closed.

---

### Post by dannyboy79 on 2007-02-08
oops, didn't realize this issue was solved with a fresh install.

---

