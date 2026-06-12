---
title: "Wpc54g"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Ravengbc on 2007-04-24
I know that there have been a few posts for the Linksys WPC54G laptop card. But, I'm creating a new post for a different reason.

I'm relatively new to not just Ubuntu, but Linux as well. I've currently got 7.04 installed on an HP Pavilion ZE5385US laptop, with plans to install it on a couple of desktops also.

I think that after a while I have finally gotten the ndiswrapper to work with the Linksys drivers. However, it seems that it will only allow me to use WEP for encryption. Surely Linux can support WPA 1 or 2, right? Did I do something wrong, or is this some type of inherent flaw with doing ndiswrapper? Is there any way to get this Linksys WPC54g card to work properly with all of he encryption options that it offers on a Windows machine? i.e. WEP, WPA1/2, AES, TKIP, ect? If it is not possible to do this, can any one make any suggestions of some known laptop wireless cards that I could look into buying that are 1. supported by Linux, especially Ubuntu, and 2. does offer all the options for wireless encryption.

Thanks guys.

---

### Post by trubblemaker on 2007-04-24
[WPA 1 or 2 with ndiswrapper.]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28WPAHowto%29")

---

### Post by Ravengbc on 2007-04-24
Thanks for the link to that. Although, now I'm starting to wonder if I've done ndiswrapper correctly.
When I go into /etc/ndiswrapper and do an ndiswrapper -l i get the following result:

lsbcmnds : driver installed.

however, when I do an ifconfig i get the following: (I've x'ed out the actual ip addresses since i'm currently at work.

eth0      Link encap:Ethernet  HWaddr 00:0B:CD:8A:1E:A1  
          inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe8a:1ea1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6192168 (5.9 MiB)  TX bytes:1626459 (1.5 MiB)
          Interrupt:10 

eth2      Link encap:Ethernet  HWaddr 00:02:8A:92:51:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2:avah Link encap:Ethernet  HWaddr 00:02:8A:92:51:81  
          inet addr:169.254.6.150  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1000 (1000.0 b)  TX bytes:1000 (1000.0 b)

if I do an iwconfig, i get the following:

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.432 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:3993  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If I do a iwlist wlan0 scan i get:

wlan0              Interface doesn't support scanning.

and, for now, lastly, if I do a sudo ifup wlan0 I get:

wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


Does any of this help in trying to figure out my problem? aside from the fact that I'm so tainted by M$.

---

### Post by trubblemaker on 2007-04-24
well you don't have wlan0 anymore in fiesty they've reverted to eth1 and eth2

look like you have to wireless drivers installed you have two cards?

i noticed you have:

```
eth2:avah Link encap:Ethernet HWaddr 00:02:8A:92:51:81
inet addr:169.254.6.150 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

```

I recently noticed that coming up when I'm around a wireless wpa connection at home... so it's a good sign.

If you want to know what driver are installed you can simply do

ls /etc/ndiswrapper

it doesn't tell you if their present and working link 'ndiswrapper -l' does 

look like you need to decide what driver to use....

I'll be back in a bit , but what driver are you using and how many wireless drivers where you expecting to load?

---

