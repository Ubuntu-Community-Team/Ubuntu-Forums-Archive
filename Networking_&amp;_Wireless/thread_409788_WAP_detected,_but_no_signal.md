---
title: "WAP detected, but no signal"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by reelbigjosh on 2007-04-15
I am using a Linksys wireless card (ndiswrapper) and connecting to my network at home using WPA encryption with no problems.  Getting ndiswrapper working, and having it autoload upon boot was no problem.  Getting Dapper to use WPA was slightly trickier, so my solution was to install [Network Manager for GNOME]("http://www.gnome.org/projects/NetworkManager/").  This seems to work fine at home: Network Manager not only finds my network, but automatically connects me (after I unlock my keychain).  My brother has an unrestricted wireless network using the same router I have (Linksys WRT54G).  Network Manager can see it, but shows no signal and cannot connect.  _sudo iwlist wlan0 scan_ returns this in the outptut: _Quality:0/100_ 
Before connecting to my network at home I also see no signal, but once connected it shows.  On the unrestricted network, Network Manager just attempts to connect but cannot.  I am able to get onto his network by going into "Networking" from my "System" menu in GNOME (sudo network-admin) and activating wlan0.  Ideally, Network Manager would handle wireless connections without issue.... can anyone explain this weirdness?

---

### Post by reelbigjosh on 2007-05-19
After many frustrations with wireless in Dapper Drake, I upgraded to Feisty Fawn.  Wireless SEEMED to work (basically) right away... after I installed ndiswrapper (naturally).  Now, I'm back at my brother's house and here's the deal:
Gnome Network Manager is in roaming mode.  At home, it detects my network right away, I punch up my password and I'm on, using WPA there.  Here (at my brother's), Network Manager shows me as connected to the network in the taskbar, it even properly shows the number of bars on the icon.  I cannot get web access, and when I ping the router, I get "Network is unreachable" ... here's the output of iwconfig:
eth1      IEEE 802.11g  ESSID:"simonweb"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:D1:DD:23   
          Bit Rate=48 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Help!

---

### Post by reelbigjosh on 2007-05-19
Problem solved.  How: sudo dhclient eth1 -- Why: I'm thinking it just needed to grab an IP?  Whatever the case, it's fixed.

---

