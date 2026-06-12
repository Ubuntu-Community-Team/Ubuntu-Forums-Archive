---
title: "Connecting to wireless university network (BGU)"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by EliBaskin on 2008-02-19
Hi,

I am new to Ubuntu and Linux, so bear with me please :

I am studying in BGU university (Israel) and just moved to Ubuntu. Been trying to work out the wireless connection (works fine at home!), but without success. Tried several configurations from the tutorial, but still none worked.

Here are the helpdesk instructions for Windows, so maybe you can help me to figure out what is the correct configuration (translated from hebrew. Original guide with pictures and pretty much self-explainatory located [HERE]("http://cmsprod.bgu.ac.il/computing/Templates/GeneralWord.aspx?NRMODE=Published&NRORIGINALURL=%2fcomputing%2fsupport%2finternet%2fWireless%2ehtm&NRNODEGUID=%7b095559E7-DE8F-46C3-A5FE-36FA4BEF223F%7d&NRCACHEHINT=Guest#Segel") ):

1. Select "Use Windows to configure my wireless network settings" in "Wireless Network tab" which is located in "Wireless Network Connections", "Properties" button.
2. Set SSID to WL_BGU
3. Network Authentication: Open
4. Data Encryption: WEP
5. Select "The key is provided to me automatically"
6. Select "Enable IEEE 802.1X authentication for this network"
7. EAP Type: Protected EAP 
8. Uncheck "Validate server certificate" and "Enable fast reconnect"
9. Uncheck "Automatically use my Windows logon name and password"
10 . When you try to connect, a new window appears, with user name, password and domain. Put your regular user name (the one used for logging in to university computers and email), password and "BGU-USERS" as domain.
11. Done.


So, this is the configuration I figured:

My wireless adapter is at eth1:

========
auto lo
iface lo inet loopback  #those two lines were there before

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid WL_BGU
wpa-ap-scan 1
wpa-eap PEAP
wpa-key-mgmt IEEE8021X
========

So, what do I do from here? Naturally, I don't want to put my password in this file, and I have no idea where I should put all the login information, since no window pops up, like in Windows (doh).

I am kind of lost here. Help please?



Additional information:
1. route gives an empty table.

2. iwconfig:
eth1 
IEEE 802.11g  ESSID:off/any
Mode: Managed  Frequency: 2.412 GHz Access Point: Not-Associated
etc (please tell me what you need, I am not copy/pasting - those are two different computers :))
3. sudo iwlist scan
Regarding WL_BGU:
ESSID:"WL_BGU"
Protocol:IEE 802.11g
Mode: Managed
Encryption key:on
Extra: bcn_int=100
Extra:atim=0

3. sudo ifdown -v eth1
ifdown: interface eth1 not configured

3. sudo ifup -v eth1
All tests were ok.
After this I got:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Hope it will do it...

---

### Post by EliBaskin on 2008-02-19
Never mind, found a local guide that explained how to use nm-aplet for this. It works now, thank you all!

---

### Post by morbid88 on 2008-03-16
Could you post a link to the guide you found?
I've been trying myself and I can't figure it out, the forums at bgu.co.il weren't very helpful in this matter.

J.

---

### Post by EliBaskin on 2008-03-16
Here is the guide. I understand you are from BGU, so Hebrew isn't foreign for you. If it is, let me know and I will translate it for you.


[http://forum.bgu.co.il/index.php?showtopic=129133&st=0&p=1399446&#entry1399446](http://forum.bgu.co.il/index.php?showtopic=129133&st=0&p=1399446&#entry1399446)

---

