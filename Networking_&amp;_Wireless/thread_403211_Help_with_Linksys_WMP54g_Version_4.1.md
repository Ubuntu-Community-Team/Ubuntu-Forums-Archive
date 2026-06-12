---
title: "Help with Linksys WMP54g Version 4.1"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by a65bugman on 2007-04-06
So I see a lot of people on this forum have been having the same issue as me with getting this card to work. The problem I'm running into is the fact that Ubuntu recognizes the card as a RT2561 card but sees it as a wired conection and will not let me browse for a network. When I manually scan for networks it gives this output:

wlan0 No scan results

I have run sudo iwconfig wlan0 essid XXXXXXXX with no error generated and then tried sudo dhclient wlan0 and I recieved this output:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:14:41:4f
Sending on LPF/wlan0/00:18:39:14:41:4f
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20

I'm running a brand new build of Ubuntu 6.10 and have Network Manager loaded via Automatix2. I have followed the process listed in this thread:
[http://ubuntuforums.org/showthread.p...=1#post2404516](http://ubuntuforums.org/showthread.p...=1#post2404516)
But I have the same issue as before.

When I go into the Device manager I see that there is a listing for an unknown device under the wireless card. Could this be the issue? If so then what is the resolution? If you need more information please let me know what you need and I will post it here but please tell me the command to use since I'm fairly new to Linux. Thanks

Update:
Command - iwconfig:

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 IEEE 802.11g Frequency:2.412 GHz
RTS thrff Fragment thr=2346 B

wlan0 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
RTS thrff Fragment thr=2346 B

sit0 no wireless extensions.

Command - lspci:

00:13.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by dbarcena on 2007-08-10
sorry to tread on your post for help, but i too am using the very same card, and it really did work on PClinuxOS and on WinXP (sorry) and now im using ubuntu in the guest bedroom thinking of just setting up a desk in here, and forgetting about this demonic linksys card. 

mine, when installed w/the README from ralink's daily tar, it is labeled ra0.

i see my network, but thats it. nothing more, but the knowledge that it exists.

I haven't found a soloution yet, since my return from new england, and i have been working on this everyday since....no joke wake up to pass out, every day for over a week.

i want this to work, and i cant afford to just go out and get a new wifi card, and my parents are very upset that i am taking over this room and my room.

can someone help us all with ONE blanket fix? or is linksys so shoddy that each person really would have a different issue and thus generate a need for a different fix?

sos?:confused:

---

