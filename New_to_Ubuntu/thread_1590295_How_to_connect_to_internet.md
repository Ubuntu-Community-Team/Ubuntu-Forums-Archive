---
title: "How to connect to internet?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Jeffreylb94 on 2010-10-07
I have a Westell versalink 327w router... I also have a wifi adapter Ralink RT2870... I can see the router available in range on linux, but when I connect we have a password... I know the password, and I think the encryption is WEP... I try to connect and have the correct password, but it loops back after a minute, and just asks for the password again... Why does this keep happening, and how do I fix this?

---

### Post by Hippytaff on 2010-10-07
Am I haveing a massive de ja vu - or did you post this earlier?

apologies if I've gotten confused :-)

---

### Post by Jeffreylb94 on 2010-10-07
> **Hippytaff said:**
> Am I haveing a massive de ja vu - or did you post this earlier?

apologies if I've gotten confused :-)

I posted a different question, but this time I re-worded it... So more people would answer it... By the way, went I type 
Code:
lsmod

I received "Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 001 Device 006: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 005: ID 03f0:4605 Hewlett-Packard ScanJet G4050
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
"

---

### Post by Hippytaff on 2010-10-07
looks like ralink problems...quite common

this is as far as I got last time with a similar problem - [http://ubuntuforums.org/showthread.php?t=1590000](http://ubuntuforums.org/showthread.php?t=1590000)

hope it helps :-)

---

### Post by silbak04 on 2010-10-07
Earlier you stated, "I think m encryption is WEP..." just to make sure you have everything right, go on a computer that has internet, and in the url, type in your defualt gateway ip, and make sure you have all your settings right. Check to really see if your encryption is WEP rather than WPA maybe.

if everything seems to be alright, read me your output for:

```

$ cat /etc/network/interfaces

```

Also, are you using Network Manager for your wireless configuration? or Wicd?

---

### Post by Jeffreylb94 on 2010-10-07
> **silbak04 said:**
> Earlier you stated, "I think m encryption is WEP..." just to make sure you have everything right, go on a computer that has internet, and in the url, type in your defualt gateway ip, and make sure you have all your settings right. Check to really see if your encryption is WEP rather than WPA maybe.

if everything seems to be alright, read me your output for:

```

$ cat /etc/network/interfaces

```

Also, are you using Network Manager for your wireless configuration? or Wicd?
Here are my results on the webpage " Wireless 
Help 

		
Wireless Operation 
Enabled
Network Name (SSID)
WEST6723
Channel 
6
Mode 
Mixed
4x Support 
Disabled
Hide SSID 
Disabled
	

	
Wireless Security

	
Wireless Security 
WEP
Key 1
---------- ----- (I blanked out the password)
MAC Address Filtering
Disabled"

Where do I find $ cat /etc/network/interfaces
On the site it shows me User ID
DSL Sync
Up
Device Name
Versalink
Internet Connection
Up
Model Number
C90-327W30-06
WAN IP Address

Serial Number

Downstream Rate 
8128 (Kbits/Sec)
Software Version
03.08.02
Upstream Rate 
512 (Kbits/Sec)
DHCP Server
Enabled
Warranty Date
April 25, 2006
Firewall Security Level
Basic 
Wireless Security
Security Enabled


And it shows me IP Address / Name
MAC Address
Connection
Status
Connection
Type

---

### Post by Jeffreylb94 on 2010-10-08
> **Jeffreylb94 said:**
> I have a Westell versalink 327w router... I also have a wifi adapter Ralink RT2870... I can see the router available in range on linux, but when I connect we have a password... I know the password, and I think the encryption is WEP... I try to connect and have the correct password, but it loops back after a minute, and just asks for the password again... Why does this keep happening, and how do I fix this?

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) I had a conflicting driver!!!

---

