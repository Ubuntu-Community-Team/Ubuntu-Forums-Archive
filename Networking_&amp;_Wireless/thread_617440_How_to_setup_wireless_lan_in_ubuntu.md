---
title: "How to setup wireless lan in ubuntu?"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by bme on 2007-11-19
I use my laptop to connect to my school's wireless network on Vista. I have feisty installed on a separate partition. I want to use ubuntu on the wireless network but being new to linux networking, I don't know how to setup. My latop has an Intell 3945 wireless installed.

The XP procedure is here-http://www.squ.edu.om/cis/wirelessE_Netsetting.htm

How to do that procedure in ubuntu I have no idea....

Help

---

### Post by farruinn on 2007-11-19
I don't have Ubuntu in front of me right now, but I would suggest trying the instructions on [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) first.

Good luck!

---

### Post by bme on 2007-11-20
Thanks!
I read the instructions on the link and tried connecting using ubuntu but was stumped .
The following are the settings in windows:
Wireless Network Key:
-Network Authentication: WPA
-Data Encryption:TKIP
key is provided to me automatically
Authentication: PEAP
Authentication Method: Secured Password(EAP-MSCAP v2)

Where to put in all these in ubuntu I have no idea

---

### Post by farruinn on 2007-11-20
Did a bit of googling and it seems you should investigate the wpa_supplicant package. I think that will help you with the PEAP authentication. Maybe search for 'ubuntu tkip' for the encryption.

There was this howto:
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

Note, what I found was about a year old. I don't know if there is a gui for doing this.

---

