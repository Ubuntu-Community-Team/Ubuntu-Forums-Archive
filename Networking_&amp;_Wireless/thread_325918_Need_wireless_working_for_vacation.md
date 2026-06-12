---
title: "Need wireless working for vacation"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by nalmeth on 2006-12-26
```
ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:9532  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
The external card that slides into the PCI slot is a D-Link AirPlus XtremeG (DWL-G650). I remember that this card is supposed to be natively supported, or out-of-the-box supported. That and atheros is supposed to be supported natively aswell. 

When I plug it in, the light bounces between 'Act' and 'Link'. It seems to be searching, or working to connect but doesn't connect. This may be due to my wireless router settings.

The thing that puzzles me is that in System-Admin-Networking, my wireless device is listed as 'not configured'. Enabling it doesn't change anything.

If it was only a router problem, wouldn't the card still appear as configured/enabled properly? 

BTW, I have network-manager installed, and all I get is 'no network connection'. I thought there was a GUI to this program, but can't seem to open it?

I hope someone can point me the right direction, I leave early tomorrow morning. I will provide any additional info needed. 
Thanks for anything you might know! :-k

---

### Post by meng on 2006-12-26
Looks like you have no network name/ESSID.
What I would try is this:
sudo iwconfig ath0 essid (network name) key restricted (hexadecimal key)
assuming you have WEP encryption

if you need to specify an alphanumeric key, what you want is:
sudo iwconfig ath0 essid (network name) key restricted s:[alpha key]

---

### Post by nalmeth on 2006-12-26
OK, you made some sense of it, thanks meng!

I managed to connect (I think) to the router, and the card now blinks 'act' and 'link' simultaneously, rather than back and forth. 

Network-manager says I still have 'no connection' though.. I seem to remember a friend getting little/no connection to our router before as well, so I guess this could be a router problem.

Does this confirm that the card works in any case?

Anyway, I must have misunderstood network-manager, I thought it was supposed to automatically connect you to a wireless network, or at least show you the available connections and their signal strength! I've seen screenshots of this, but I don't see any such window at all. Do I have the wrong applet? 

When I'm at the hotel, how would I connect to the free wireless Internet there, not knowing the network name or password?

---

### Post by meng on 2006-12-26
Try
sudo dhclient ath0

as the next step.

When at a hotel, you would be able to ask for the network name or password, if network-manager is not working for you.

---

### Post by nalmeth on 2006-12-26
OK, thanks for the pointers meng

With the last command I can't connect to anything:
```
$ sudo dhclient ath0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:3d:52:58:b1
Sending on   LPF/ath0/00:0f:3d:52:58:b1
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
```
I will just blame this on my router. I've seen others struggle to connect aswell.

I'm just kind of confused with network-manager. Thru the terminal I can detect my home network and my neighbors network, but I don't get any indication thru network-manager that these networks exist. 

I just get the two-screens icon in the taskbar, no strength meter or available networks. And when I click on it, it just says 
Enable Networking (check)
Enable Wireless (check)
(i) Connection information (grayed out)

Comparing to network-manager screenshot (attached comparison), they don't look at all similar.
This is why I wonder if I have the wrong applet..

I guess I will find out when I'm there :KS

---

### Post by Floppyjoe on 2006-12-26
Try:

```
sudo iwlist ath0 scan
```

to see if your wireless device can see your router.

---

### Post by nalmeth on 2006-12-26
yep, when I run iwlist I get my home router and my neighbors router.

I guess the fact that the card can scan means its working correctly right?

I just can't connect to my network, or have network-manager pick up those networks. :-k

A lot of missing links

---

### Post by Floppyjoe on 2006-12-26
I believe your card is working properly but you need additional setup to connect to the router.

/etc/network/interfaces is the file where your network interfaces are defined, eth0 being the standard wired interface. To make the wireless network come up when you start your computer put # in front of 'auto eth0' (to stop it automatically starting) and add something like the following lines after this code.

```
sudo gedit /etc/network/interfaces
```

auto ath0
iface ath0 inet dhcp
wireless-essid   MYNETWOTK
wireless-channel 11
wireless-mode    managed

You need to enter your specs instead of the ones liste here.

Then save this file and exit. then reboot.

---

### Post by nalmeth on 2006-12-26
Thanks for helping FloppyJoe

I added these lines as you recommended (the others including WEP password were added in System->Administration->Networking):
```
wireless-channel 11
wireless-mode managed
```And I commented out auto eth0, and started icewm so that network-manager wouldn't start.

The card flashes both 'act' and 'link', which I think means its working, but I have no connection, and running  'sudo dhclient ath0' gave me the same outcome:
```
 wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:3d:52:58:b1
Sending on   LPF/ath0/00:0f:3d:52:58:b1
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received. 
```

Perplexing :-?

---

### Post by scrooge_74 on 2006-12-26
Did you took down the security of the router, just to rule that out?  You should be online by now from all that I read.

Sometimes Gnome network manager can be a little frustrating (that has happend to be before) You could try using Wifi-radar to connect.  Sometimes i get online using it, but I can with the network manager from gnome.

It sometimes picks up networks the network manager doesnt

---

### Post by Floppyjoe on 2006-12-26
Can you post the result of :

```
sudo iwlist ath0 scan
```

You need to set the channel to that of the one your router is using and also the Essid has to be set to the one your router is called.

---

### Post by nalmeth on 2006-12-26
```
Cell 01 - Address: 00:0F:3D:5B:28:5A
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/94  Signal level=-68 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100170000
```
Doh! The channel is 6 as far as I can see. I put 11 thinking it was a default. My mistake. I will try with 6. 
This is my interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

##auto eth1
##iface eth1 inet dhcp

##auto eth2
##iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid default
wireless-key (snipped, who knows whos reading this :p )
wireless-channel 6
wireless-mode managed 

auto wlan0
iface wlan0 inet dhcp


##auto eth0
```
Looks about right, yes?

---

### Post by Floppyjoe on 2006-12-26
That looks right.

---

### Post by nalmeth on 2006-12-26
Dang, I thought that might have done it.
```
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:3d:52:58:b1
Sending on   LPF/ath0/00:0f:3d:52:58:b1
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

> Did you took down the security of the router, just to rule that out?  You should be online by now from all that I read.

Sometimes Gnome network manager can be a little frustrating (that has happend to be before) You could try using Wifi-radar to connect. Sometimes i get online using it, but I can with the network manager from gnome.

It sometimes picks up networks the network manager doesnt
I haven't tried taking the security down, but if I had the wrong password, that should be noted in an error shouldn't it? It seems the router just isn't answering my requests..
I think I'll take a look at Wifi-Radar, or bring it along as network-manager hasn't thrilled me yet. Though its probably not its own fault.
Thanks for the post :)

You must be right, that its the router at fault, in one way or another. All the help I've gotten here should be all or more than I need to get things right on my side, yet it still doesn't work.

I guess that now I have enough ammo to try it on a different network, I can't complain :)

Any other interpretations or ideas? 
Mega-thanks everyone for the input :D

---

### Post by Floppyjoe on 2006-12-26
Go into System/Administration/Networking and make sure your interface is activated and set the properties the way you want. Deactivate the Wired connections.

---

### Post by nalmeth on 2006-12-26
Tried again, then killed nm-applet, and tried again. 

System->Administration->Networking says that wireless connection is configured properly, eth0 is not (its not plugged in either, and reads as disabled) but theres no actual connection.

'Act' and 'Link' are simultaneously blinking on the card. 

Wireless is set to DHCP, but its supposed to be right?

The password consists of letters and numbers only. Is this hexadecimal or alphanumeric? I haven't had luck with either setting, but I'm going to try both, and restart the wireless networking after each.

---

### Post by nalmeth on 2006-12-26
I can't seem to get anything right to connect to my wireless network, and I will just have to concede or guess that its the router at fault.

Thanks for everyones help, this actually was a very educational experience :mrgreen:
I think I'm prepared to use Ubuntu wireless in the future.

Much appreciated homies 8)

---

### Post by scrooge_74 on 2006-12-26
One more read for the road [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by nalmeth on 2006-12-26
Never seen that wiki before, cheers!

Merry Christmas Scrooge ;)

---

### Post by junk269 on 2006-12-30
got a sec? i need wireless help an i see your on i have an ibmstinkpad a22m pent3(600-800m i forget)the mem on it is 384 the wireless card is one that i've read will work motorola wn825g
i no it works on knoppix linspire even backpack but i cant get it to work for ubuntu an i plan on gettin christian ubuntu tomarrow pls help an remember i am noooo teckie....:D thanks
> **Floppyjoe said:**
> Try:

```
sudo iwlist ath0 scan
```

to see if your wireless device can see your router.

---

