---
title: "ipw2200 wep trouble?"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by ked on 2005-10-14
I rearly give up something, but now I'm pretty close. No matter how much I try I can't connect to my wireless router when I use WEP. It works just fine with an open unsecured network. I'm using the ipw2200-1.0.6 driver.

Here is what I do:

$ sudo iwlist eth1 scan

Cell 01 - Address: 00:C0:02:C2:AB:BC
ESSID:"<my wireless network>"
Protocol:IEEE 802.11bg
Mode:Master
Channel:7
Encryption key: on
Bit Rate:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
Quality=42/100 Signal level=-75 dBm
Extra: Last beacon: 239ms ago

$ sudo iwconfig eth1 essid <my wireless network>
$ sudo iwconfig eth1 key 0123456789
$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID:"<my wireless network>"
Mode:Managed Channel=0 Access Point: 00:00:00:00:00:00
Bit Rate=0 kb/s Tx-Power=20 dBm
Retry limit:7 RTS thr: off Fragment thr: off
Encryption key:1234-5678-90 Security mode: open
Power Management: off
Link Quality=42/100 Signal level=-75 dBm Noise level=-86 dBm
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag: 0
Tx excessive retries: 0 Invalid misc: 463 Missed beacon: 4


sit0 no wireless extensions.

$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:58:d6:f9
Sending on LPF/eth1/00:12:f0:58:d6:f9
Sending on Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 192.168.1.104
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
$

As you can see - no sucess. (Without encryption everythings great.)

What puzzles me is that the key is changed from:

0123456789 to 0123-4567-89 (look in the output from the iwconfig command). And yes, I've tried:

$ sudo iwconfig eth1 key s:0123456789

without success. The iwconfig command then returns for the key:

Encryption key:3078-3132-3334-3536-3738-3900-00

HELP! What is wrong here????

---

### Post by jakev383 on 2005-10-20
Not sure if you got this working or not, but the s: flag in iwconfig is to specifiy a ASCII key (passphrase is currently unsupported).
The key xxxx-xxxx-xx should work, or you can use xxxxxxxxxx. It may rewrite it when you do the iwconfig, but don't worry about it.
It looks like you're not telling it what channel to use. Your AP looks to be on channel 7, so you would want to do 'iwconfig eth1 channel auto' if your hardware supports is.  Otherwise do 'iwconfig eth1 channel 7' to set it to channel 7.
Hope that helps.

---

### Post by kingsidy on 2005-10-20
try a tool called "wifi radar". I use it with my Wep encrypted network never had a single problme with wireless. its a tool tahat help configure wireless networks. You can install it from the "Add Application" tool.

---

### Post by ibanez88 on 2005-10-21
I'm having the exact same problem with ipw2200.  I've tried every solution that I could find.. still nothing.  

One thing though, can the people who posted that WEP is working confirm that they're using ipw2200?  Or are you using some other card?  At this point I suspect that its a bug in the driver.

I can get WEP working with 64 bit / open / broadcast essid.  But not with anything stronger than that.

see my thread:

[http://ubuntuforums.org/showthread.php?t=78162](http://ubuntuforums.org/showthread.php?t=78162)

---

### Post by jakev383 on 2005-10-21
[QUOTE=ibanez88]I'm having the exact same problem with ipw2200.  I've tried every solution that I could find.. still nothing.  

One thing though, can the people who posted that WEP is working confirm that they're using ipw2200?  Or are you using some other card?  At this point I suspect that its a bug in the driver.

I can get WEP working with 64 bit / open / broadcast essid.  But not with anything stronger than that.

see my thread:

[http://ubuntuforums.org/showthread.php?t=78162](http://ubuntuforums.org/showthread.php?t=78162)[/QUOTE]

I am on a Dell 600m laptop, with the ipw2200 B/G drivers.  I connect to multiple 64bit WEP / open / broadcasted essid APs.  The only major issue I still have is that the card will sometimes crap out during large file transfers (error is dmesg about restarting the driver).  If I try the hwcrypto=0 hack it stops this problem, but when I move to a diffrerent AP I can no longer connect until I remove that directive.

---

### Post by jakev383 on 2005-10-24
As an update: I tried to roll back the ipw2200 driver to version 1.0.0 as per another thread.  Boy, was that a mistake. I was never able to get the thing to connect to anything after that.  My ultimate solution was to pull the Intel 2200B/G card out, and put the Broadcom back in.  Have not had a single hiccup since. 14+ Gigs moved on my LAN, email, surfing, etc., with NO PROBLEMS.  I know this isn't really a viable solution for most, but maybe it's worth noting.
Hopefully by the next release the ipw2200 drivers will have matured a little more and be a little friendlier.

---

