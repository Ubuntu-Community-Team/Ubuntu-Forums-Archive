---
title: "Problems with laptop wireless card"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by adamcknowles on 2007-06-19
Hi,

I've just got a D-Link DWL-G630 PCMCIA card for wireless networking.  

I've plugged it into my laptop and by going to Applications -> System -> Network, I can see an entry for a wireless connection, which I configure with the detail of my local network (SSID, WEP key, etc).  The problem is that I cannot get any web pages or e-mail to download onto my laptop.  

After I enable the wireless card, I can see the lights on it flashing.  I can also use wifi-radar to detect my wireless network and the wireless network next door, but I still cannot access any websites.  

Any suggestions on what to try next would be gratefully appreciated.

P.S. I'm using Xubuntu 7.04

---

### Post by lee_elenbaas on 2007-06-19
ubunto doesn't ship with a driver that support encription over wireless networks - there is a beta version of such a driver avalible to download as a tarball - but i used a simpler solution in my home wireless network - i removed the encription and used MAC filtering to ensure that only i (and those i allow) will use the network

---

### Post by mflint on 2007-06-22
> **lee_elenbaas said:**
> i removed the encription and used MAC filtering to ensure that only i (and those i allow) will use the network
... and anyone who can change the MAC address on their wireless card.

MAC address filtering really shouldn't be relied on to be anything more than a mild deterrant. It is no substitute for WPA or (if you have no alternative) WEP.

---

### Post by walkerk on 2007-06-22
follow the wifi-radar and wpa setup in here for encryption..

[http://ubuntuforums.org/showthread.php?t=478612](http://ubuntuforums.org/showthread.php?t=478612)

---

### Post by adamcknowles on 2007-06-26
Many thanks for your replies, but I've still got to get the laptop associated with the wireless router before I sort out security.  I fact I've disabled WEP / WPA on the router just for the time being, so it doesn't complicate things.

I've been following this guide [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").  When I run **iwconfig** I get: 

```
ra0       RT61 Wireless  ESSID:""  Nickname:""

          Mode:Managed  Frequency:2.437 GHz  Bit Rate=54 Mb/s   

          RTS thr:off   Fragment thr:off

          Encryption key:XXXX-XXXX-XX

          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


When I run **iwlist ra0 scan**, I get:

```
ra0       Scan completed :

          Cell 01 - Address: 00:18:F6:5D:2A:03

                    ESSID:"Next Door's Router"

                    Mode:Managed

                    Channel:1

                    Encryption key:on

                    Quality:0/100  Signal level:-69 dBm  Noise level:-256 dBm

          Cell 02 - Address: 00:14:7F:2B:17:62

                    ESSID:"My Router"

                    Mode:Managed

                    Channel:6

                    Encryption key:off

                    Quality:0/100  Signal level:-31 dBm  Noise level:-256 dBm
```


From this information I've got three observations:

[LIST=1]
[*]	The network card can see my network (and next door's).

[*]	It is not associated with my router, as it has no &#8220;access point&#8221; when I run iwconfig.  This is despite me entering the network details in the System>Network menu.  

[*]	I'm a bit worried about why Quality is 0/100.
[/LIST]

Any suggestions about what to try next would be appreciated.

---

### Post by t4thfavor on 2007-06-26
Try this from the command line. 
sudo iwconfig ra0 essid "your SSID" key "your wep key" ap "your AP's MAC ADDR"

then try iwconfig ra0 and see if it works. Remember you will have to issue a dhcp broadcast after the iwconfig command before you can get internet.

sudo dhclient ra0

---

### Post by adamcknowles on 2007-06-26
Thanks for the reply

> **t4thfavor said:**
> Try this from the command line. 
sudo iwconfig ra0 essid "your SSID" key "your wep key" ap "your AP's MAC ADDR"


I tried to do this but I kept getting a “bad address” error.

Just to see if it would work any better, I blacklisted the network card driver module (rt61) and installed the windows driver from the CD using **ndiswrapper**.  I now don't get any bad address errors, but I still cannot load any web pages.  When I try **dhclient** I get:

```
Listening on LPF/wlan0/00:19:5b:cb:cd:a0

Sending on   LPF/wlan0/00:19:5b:cb:cd:a0

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.

No working leases in persistent database – sleeping.
```

---

### Post by adamcknowles on 2007-06-27
Many thanks to everyone who replied.  I've got it working now.  I installed network manager which got me connected to my wireless network.  Even now I've switched WPA back on, the network card is still working fine. :D

---

