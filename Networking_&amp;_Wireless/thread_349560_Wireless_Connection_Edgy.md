---
title: "Wireless Connection Edgy"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by acheton on 2007-01-30
Hi all,

I'm gradually making progress on getting my Edgy install connecting to my wireless network. Basically my Belkin Wireless G USB Network Adapter is now set up with the correct driver. Running an **iwlist scan** produces similar results to windows which would seem to indicate that the adapter is working okay:

[INDENT]lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:7F:99:0F:72
                    ESSID:"BTHomeHub-7659"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Extra:SignalStrength=53%,LinkQuality:84%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

          Cell 02 - Address: 00:09:5B:6D:03:96
                    ESSID:"Deepdale"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Extra:SignalStrength=38%,LinkQuality:72%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

          Cell 03 - Address: 00:09:5B:DC:80:C8
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Extra:SignalStrength=23%,LinkQuality:8%
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

          Cell 04 - Address: 00:09:5B:CE:AE:B0
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Extra:SignalStrength=30%,LinkQuality:64%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
[/INDENT]

I've followed the sticky at the top of this forum on setting up access using WPA, used instructions from help.ubuntu.com and used Wifi-Radar but I cannot seem to get connected. Even if I remove WPA security from the router and run with WEP or unsecured access I still cannot get access. I've tried to use network-manager-gnome to access the network as well, however this doesn't seem to work. 

I even reinstalled Edgy from scratch, updated it with all of the latest patches using Update Manager and then followed the links below to get everything set-up from scratch:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

So I've currently got a fresh install where I've followed the above and installed wifi-radar. I'm pretty much a newbie at this. Does anyone have any thoughts as to what I might be doing wrong or what I can do to further diagnose the problem? 

Thanks,


Ach

PS My Access point's SSID is netgear.

---

### Post by jshein on 2007-01-30
Take a look at the WPA key in the configuration file, and see if it is formating it incorrectly.

See my post here
[http://ubuntuforums.org/showthread.php?t=278190](http://ubuntuforums.org/showthread.php?t=278190)

---

### Post by acheton on 2007-01-30
Thanks for the really quick reply. I've moved the router over to WEP and set up a password, I've used your suggestion for the format of the wireless key but it doesn't work. Can you see anything wrong in my interfaces file?

[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key FE:ED:18:9E:27


auto eth0[/INDENT]

---

### Post by spd106 on 2007-01-30
First I suggest that you change the essid on the AP to something other than NETGEAR, i'm not sure whether that will solve the problem, but it should help during the association process. SSIDs should be unique, unless you are extending the network.

I don't think the colons will help in your case, the linked post was showing that they changed from ascii to hex format. This was done by removing the s: prefix.

---

### Post by acheton on 2007-01-30
Thanks for the reply. I've changed the SSID to something more unique and removed the unnecessary colons. However I still don't appear to be having any luck. iwconfig and iwlist scan show the newly renamed network and my etc/network/interfaces file is shown below. Are there any more diagnostic steps I can take?

[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid kyrios
wireless-key FEED189E27

auto eth0

auto wlan0[/INDENT]

---

### Post by spd106 on 2007-01-30
When you say iwconfig shows the ssid, does it also show your APs MAC address? If so then you are associated and just need an ip address. Try **sudo dhclient wlan0**.

---

### Post by acheton on 2007-01-31
> **spd106 said:**
> When you say iwconfig shows the ssid, does it also show your APs MAC address? If so then you are associated and just need an ip address. Try **sudo dhclient wlan0**.

Thanks for the response, running iwconfig produces the following:

[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"kyrios"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:09:5B:CE:AE:B0   
          Bit Rate:54 Mb/s   
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=46/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:566  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/INDENT]

Which seems to indicate that the router is associated correctly. Now if I run the command you suggested the result it:

[INDENT]Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:3f:4e:75:9f
Sending on   LPF/wlan0/00:17:3f:4e:75:9f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/INDENT]

Which I think may mean that it's not connecting via DHCP - is this correct?

Thanks,


ach

---

### Post by spd106 on 2007-01-31
I am confused as to which AP you are trying to connect to. From the scan output earlier it looks like WPA is on. This means you need to configure wpa_supplicant in order to connect. See the WPA sticky.

---

### Post by acheton on 2007-01-31
> **spd106 said:**
> I am confused as to which AP you are trying to connect to. From the scan output earlier it looks like WPA is on. This means you need to configure wpa_supplicant in order to connect. See the WPA sticky.

Sorry about that. I was running with WPA, however in an attempt to simplify the issue I switched to WEP which seemed to be supported more easily. However I have in the past followed the instructions and been unable to get WPA working. At this point I would be happy to get something working.

---

### Post by acheton on 2007-02-02
OK, I'm making progress on this finally. I've disabled WPA and WEP and have finally been able to make a connection to the wireless router. Now this is obviously a far from ideal situation, but at least I can get on the net from Ubuntu. I'm going to try and follow the WPA instructions in the sticky at the top of this forum and see if I can get that working.

---

### Post by acheton on 2007-04-12
Well I just thought I would update you all about this problem. Basically I gave up for a while and then decided to try the Beta of Feisty, which I am pleased to say recognised my wireless setup right out of the box and connects to WPA without any effort at all :D Great work!

---

