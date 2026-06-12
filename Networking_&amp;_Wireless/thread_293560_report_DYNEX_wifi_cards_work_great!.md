---
title: "report: DYNEX wifi cards work great!"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by Beowulf.1000 on 2006-11-05
I am simply making a report here about a brand of wifi cards that work, to help others wanting to get wifi up and working on their Desktop PC or notebook computer.

DYNEX, the "house" brand of Best Buy electronics, wifi cards seem to work really nice out of the box with Ubuntu 6.06 and 6.10.  I put Ubuntu 6.06 on a second desktop PC and a $35 Dynex PCI wifi card worked out of the box, including 64 and 128 bit WEP encryption; atheros chipset, shows up as device ath0 for wifi/networking.

I also bought a new notebook PC (Compaq Presario V2000 series) that has a Broadcom chipset wifi built into it, and I gave up trying to get it working with ndiswrapper. I bought a Dynex pcmcia wifi card at Best Buy for $35 and it worked out of the box with Ubuntu 6.10, including WEP encryption. Has atheros chipset, very nice.

---

### Post by TrueJk7 on 2006-11-18
[http://ubuntuforums.org/showthread.php?p=1777420#post1777420](http://ubuntuforums.org/showthread.php?p=1777420#post1777420)

Hey, I'm using Edgy Eft too and Having some major issues with this card. 

Then one I got was DX-WGNBC It's listed on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D) saying it works to but that does not seem to be the case for me. Any suggestions (all my information is in the post listed above. 

Thanks in advance!
Jake

---

### Post by Beowulf.1000 on 2006-11-19
Well did you go into the Networking GUI and configure the card-- you have to activate it with the checkbox button, and of course coordinate it with your router, encryption on/off and type and key, etc.

How about showing us the output of 
 sudo iwconfig
to be of help. "Having some major issues with this card" does not provide enough useful info to help you.

---

### Post by DapperMe17 on 2006-11-19
Great info on the Dynex card for Compaq laptop w/built-in Broadcom!

---

### Post by TrueJk7 on 2006-11-20
Thanks DrapperMe17 :)
Hey Beowulf.1000 way ahead of ya. I also got my problem fixed. Thanks for the info though. Follow the link to my issue. Especially if you get lost.

Peace

---

### Post by Snoopy1966 on 2006-11-20
Hello,
I purchased the Dynex DX-WGDTC wireless G desktop card and I can not get it to work.  I am running 6.06 Dapper
Here are results from iwconfig and sudo iwconfig

```
ahmed@ahmed-desktop:~$ sudo iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys:) :) :)"
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:14:A5:CB:4C:85
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3139-376A-6939-3165-:cool:-6170-3631-6167   Security mode:restricted
          Power Management:off
          Link Quality=18/94  Signal level=-77 dBm  Noise level=-95 dBm
          Rx invalid nwid:279  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:20   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

ahmed@ahmed-desktop:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys :) :) :)"
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:14:A5:CB:4C:85
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=18/94  Signal level=-77 dBm  Noise level=-95 dBm
          Rx invalid nwid:285  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:20   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

It has the Atheros chip.  The gut at Best Buy pulled up some websites for Linux and found this was a usable card like Beowulf.1000 said.  Plug and play no messing around.

Am I missing something?  I used networking tools and Kwifi Manager and tried many combinations.  I see many reception errors in Networking tools.  Here is ifconfig -a

```
ahmed@ahmed-desktop:~$ ifconfig -a ath0      Link encap:Ethernet  HWaddr 00:14:A5:CB:4C:85
          inet6 addr: :)::214:a5ff:fecb:4c85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:80122 dropped:0 overruns:0 frame:80122
          TX packets:93 errors:22 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:27806 (27.1 KiB)
          Interrupt:217 Memory:f8c20000-f8c30000

eth0      Link encap:Ethernet  HWaddr 00:0C:F1:FB:86:42
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fefb:8642/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3737 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3049503 (2.9 MiB)  TX bytes:511854 (499.8 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1272 (1.2 KiB)  TX bytes:1272 (1.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Any suggestions out there?  I have been pounding my head on the desk for three days now and it hurts ](*,)

---

### Post by Beowulf.1000 on 2006-11-26
It looks to me like an invalid essid (invalid network id, invalide nwid), also you have some sort of encryption running. Try the KISS principle (Keep it sweet and simple)-- how about turning off your router's encryption to simplify things; also your router SSID (ESSID) is rather funky, maybe start out with it kept simple like change your router SSID to just "linksys", and turn off encryption. Be sure to save router setting changes.

Then reconnect/reconfigure
$ sudo iwconfig ath0 essid any
$ iwconfig
$ ifconfig

Your DYNEX card is being recognized as ath0, that is good news. It looks to me like an issue communicating with your router. Notice the 
  Rx invalid nwid:285

---

### Post by roadcone on 2007-08-24
OK, the problem I am having is with the card in my desktop. The network is on ath0, but when I run iwconfig, ath0 doesn't show. Only lo, eth0, and eth1. None of these are viable. Any advice?

---

### Post by Beowulf.1000 on 2007-08-26
Do you have the madwifi driver installed and loaded? Ubuntu 6.06 installed madwifi and worked with dynex and other atheros cards automagically, but I noticed that went away with 6.10 I think.  Once you get madwifi installed and the driver loaded atheros chipset wifi cards work fine. Study these two links, second one for quick install of madwifi:
[http://madwifi.org/](http://madwifi.org/)
[http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)
:guitar:

---

### Post by rustybronco on 2007-09-26
Just installed a dx-wgdtc card and I have to say it just works with 7.04. using wep and mac filtering on the router. (i'm on fiesty  posting this)
***EDIT*** and it works with gutsy out of the box! ( i'm on gutsy posting this)
KUDO'S DEVS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! and for free? WOW!

p.s. best-buy clearance,  09-25-07... 22.99 usd

---

### Post by rustybronco on 2007-10-15
Dynex dx-wgnbc works also, it also has the atheros chipset in it.
best-buy clearance 20.99.

---

### Post by rustybronco on 2007-11-11
add dynex dx-wgpdtc enhanced "g" desktop card to the list that work in 7.10 
see [http://ubuntuforums.org/showthread.php?t=595442&highlight=dynex](http://ubuntuforums.org/showthread.php?t=595442&highlight=dynex)

---

