---
title: "Cannot find network...HELP PLEASE"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Chessmaster on 2008-02-10
Hi, any help would be great! 

I have installed my TP-LINK Wireless USB adapter (TL-WN321G), but it cannot detect an network / wireless router. 

I installed the drivers (RT73) but RutilT does not detect any network when I scan (site survey). 

The output from iwlist scan, lshw -C network, iwconfig, are below. 

Any help please. I am starting to go mad after days of trying to sort this out! 

> 
XXXX@XXXX-desktop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



ppp0      Interface doesn't support scanning.



wlan0     No scan results



XXXX@XXXX-desktop:~$ sudo lshw -C network

  *-network               

       description: Ethernet interface

       product: 82801BA/BAM/CA/CAM Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@0000:02:08.0

       logical name: eth0

       version: 03

       serial: 00:08:02:ca:7b:9b

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:19:e0:8d:e5:2a

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN

XXXX@XXXX-desktop:~$ sudo cat /etc/network/interfaces

auto lo

iface lo inet loopback





iface ppp0 inet ppp

provider ppp0




iface wlan0 inet static

address 192.168.1.1

netmask 255.255.255.0

wireless-essid XXXX WIFI



auto wlan0



auto ppp0


XXXX@XXXX-desktop:~$ sudo iwconfig
lo        no wireless extensions.



eth0      no wireless extensions.



ppp0      no wireless extensions.



wlan0     RT73 WLAN  ESSID:"XXXX WIFI"  

          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   

          RTS thr:off   Fragment thr:off

          Encryption key:off

          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by Hightide on 2008-02-10
HI Chessmaster

in your iwconfig output I dont see any Access Point (your router) in other words you are not connected.

It should something like this  Mode:Managed  Frequency:2.462 GHz [B] Access Point: 00:18:4D:CC:30:C2 

Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=690697")

regards

:)

---

### Post by Chessmaster on 2008-02-12
Thanks for the reply. 

The thing is, I can sometimes pick up other networks (including my router) for a few seconds, make a very brief connection and then they disappear. This happens even if my wireless router is close or far away. 

Any suggestions why this could be happening? Or what diagnostics I could run.

Could it be the case that my USB wireless adapter is not getting enough power from the USB port? I have a few things running such as wireless keyboard, mouse etc. 

Cheers

---

### Post by Chessmaster on 2008-02-12
I have just found out that I don't have USB 2.0 ports!!!!! I only have USB 1.1 

1) Does anyone know if this will affect the USB wireless adapters ability to pick up the networks? I realise that it will mean that data transfer will be slow, but what about the signal strength etc?

2) Is I want to stream music wirelessly over a network (say to my stereo) will I need USB 2.0 ports? 

Most USB wireless adapters "say" they were 1.0 and 1.1 compliant, but you never know. I guess compliant is very different from "works very well with..."

Cheers

---

### Post by chaos315 on 2008-02-13
I have a similar problem, but I have a wireless Dell XPS M1330 -- sometimes I can pick my network and other times, there are none. I have another Dell laptop sitting right next to it and it works just fine. I am very confused. I can restart and maybe it will show the networks and maybe not any at all.  -- any help is greatly appreciated.

---

### Post by Chessmaster on 2008-02-15
The mucking around got too much for me and I went out today and purchased a ASUS 167g - and it was nice and cheap! 

And it picked up my network straight away and held the connection for as long as I wanted it to. Didn't need to install any new drivers either. 

I am assuming that the fault was with the TP-Link adapter I was using before. It used to get really quite hot and then it stopped working at all for a while (the light went out).

If you are having trouble identifying your network, and you have tried everything (as I had), then I recommend trying another adapter.

---

