---
title: "WiFi on Dell Latitude C400 with 3com-card"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Grimmhoff on 2008-05-17
(It seems quite typical for a new member's first or one of the first posts to be a new thread asking for help, but I'll just elegantly ignore this.)

I have long been waiting for a chance to install linux on a PC, and yesterday at last, I did so. The trouble is, I can't get WiFi.

OS: ubuntu 7.10 (Gutsy Gibbon)
Hardware: Dell Latitude C400 (Unlikely modified)[specs]("http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000338,10000055,00.htm")
Wireless card: 3com 3CRXJK10075

I have searched around for this, found [this post]("http://ubuntuforums.org/showthread.php?t=786369&highlight=3CRXJK10075") (asking about the card in 8.10) and [this one]("http://ubuntuforums.org/showpost.php?p=1252863&postcount=9") saying it works nearly out of the box with Dapper.

I've been confused by [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), looked at supported WiFi-cards and entered iwconfig and other stuff into the commandline.

I have never set up a computer to WiFi, and generally don't have a lot of experience with hardware (never having owned a computer myself), add that to the fact of me being extremely new to ubuntu and linux, and the cluelessness should be welldescribed.

Suggestions, tips, walkthroughs (ooh, yes!), tutorials and so on are extremely welcome. Linux is to be learned, and I am ready.

Grimmhoff

---

### Post by chili555 on 2008-05-17
According to this: [http://209.85.215.104/linux?q=cache:WEdDhX1TPn4J:linux-wless.passys.nl/query_chipset.php%3Fchipset%3DAtheros+3CRXJK10075&hl=en&ct=clnk&cd=7&gl=us](http://209.85.215.104/linux?q=cache:WEdDhX1TPn4J:linux-wless.passys.nl/query_chipset.php%3Fchipset%3DAtheros+3CRXJK10075&hl=en&ct=clnk&cd=7&gl=us) your card uses the madwifi drivers. The madwifi drivers can probably be activated by going to System -> Administration -> Hardware Drivers and checking a box next to Atheros or madwifi or similar.

Network Manager, which is installed by default, will not allow a wireless connection as long as you have a good, working IP address from an ethernet connection, so before you proceed to configure the wireless, detach the ethernet cable, if any.

You should then be able to go to System -> Administration -> Network, enable the wireless, give, at a minimum, your ESSID and connect.

---

### Post by Grimmhoff on 2008-05-17
It seems the menu "Hardware Drivers" is not present...

---

### Post by chili555 on 2008-05-17
Oops! Sorry.

Please hook up an ethernet cable and do:```
sudo apt-get install linux-restricted-modules-`uname -r`
```The operator *`uname -r`* with those little backticks , is a way to say 'match my running kernel.' Let us know.

---

### Post by Grimmhoff on 2008-05-19
Response I got:

Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-restricted-modules-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Meaning... I have already got the latest version and the problem lies elsewhere?

---

### Post by chili555 on 2008-05-19
> Meaning... I have already got the latest version and the problem lies elsewhere?Exactly. May we please see:```
sudo lshw -C network
iwconfig
ifconfig
```Thanks.

---

### Post by Grimmhoff on 2008-05-20
```
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:02:b8:06
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.112 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:0f:cb:b0:1b:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-87 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:0F:CB:B0:1B:27  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:06:5B:02:B8:06  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe02:b806/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1704457 (1.6 MB)  TX bytes:250070 (244.2 KB)
          Interrupt:11 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-CB-B0-1B-27-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:4044
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2064 (2.0 KB)  TX bytes:6624 (6.4 KB)
          Interrupt:11

---

### Post by chili555 on 2008-05-20
Looks like Network Manager is using the wired connection, instead.> eth0 Link encap:Ethernet HWaddr 00:06:5B:02:B8:06
inet addr:192.168.1.112 Bcast:192.168.1.255 Mask:255.255.255.0Please see here:[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) especially: > The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themPlease detach the wire. Did your wireless spring to life?

---

### Post by Grimmhoff on 2008-05-20
> **chili555 said:**
> Please detach the wire. Did your wireless spring to life?No, it didn't. There is a green diode on the card, and it blinks coninually.

---

### Post by chili555 on 2008-05-20
The title of your thread is '3com card' but we are actually trying to activate your Atheros wireless card, correct?

May I please see:```
sudo iwlist ath0 scan
```Wow! It's a bit late in Norway!

---

### Post by Grimmhoff on 2008-05-21
ath0      Scan completed :
          Cell 01 - Address: 00:02:72:50:43:A0
                    ESSID:"Jensen AirLink 6954"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-50 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

(only worked with the card in (tried all 4 combinations of plugging and unplugging), probably meaning it has detected it, but can't...use it?)

---

### Post by chili555 on 2008-05-21
Two minor issues here: first, the ESSID has spaces in it, so we must confine the ESSID in quotes. Second, the scan says, 'key: on.' That indicates the router or access point is encrypted with WEP. We must have the key to unlock the door. Please do:```
sudo iwconfig ath0 essid "Jensen AirLink 6954"
sudo iwconfig ath0 ap 00:02:72:50:43:A0
sudo iwconfig ath0 key <ur_wep_key>
sudo dhclient ath0
```Did you connect?

---

### Post by Grimmhoff on 2008-05-27
> **chili555 said:**
> Two minor issues here: first, the ESSID has spaces in it, so we must confine the ESSID in quotes. Second, the scan says, 'key: on.' That indicates the router or access point is encrypted with WEP. We must have the key to unlock the door. Please do:```
sudo iwconfig ath0 essid "Jensen AirLink 6954"
sudo iwconfig ath0 ap 00:02:72:50:43:A0
sudo iwconfig ath0 key <ur_wep_key>
sudo dhclient ath0
```Did you connect?Just tried it. I plugged out the cable, open a random link in a new tab (in this case your profile), and waited. "Damn" I think. It's trying, but it won't get an answer. Just as I am about to plug the ethernetcable back in to write another doubting comment... CONNECTION!

Thankyou very much chili555. Someday I will know what exactly I have done, and be able to use it constructively. 

Response I got after "sudo dhclient ath0":

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:cb:b0:1b:27
Sending on   LPF/ath0/00:0f:cb:b0:1b:27
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.254
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.111 -- renewal in 355182 seconds.

```

Wait: if I upgrade to 8.04 (Hardy) now, will the changes still be present? Or do I have to go through the whole process, just the last bunch of code, or even a new one?

---

### Post by Grimmhoff on 2008-11-09
After upgrading to 8.04, it still worked, unsure if this was because of changes made in 7.10, or if it came with the package. After this I installed Mint 5, which picked it up immediately. Seeing as it's quite an old computer, I wanted something even more lightweight, and now try fluxbuntu.

Fluxbuntu does not automatically detect wireless, nor does a wired connection work. I tried the steps above, but they didn't work either.

Suggestions?

---

