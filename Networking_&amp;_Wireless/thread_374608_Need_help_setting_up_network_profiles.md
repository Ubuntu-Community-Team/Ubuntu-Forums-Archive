---
title: "Need help setting up network profiles"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by whayong on 2007-03-02
I FINALLY got my wireless card up and working but now I've run into another problem.  I followed the RT61 how to found here:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29)

Now my problem however is I want to be able to use different AP's since this Edgy installation is on a laptop.  I have no problem connecting to my home network WPA via DHCP but I can't seem to connect to my work using WEP via static IP.  I've inputed the necessary information in Settings>Administration>Networks into a different profile but can't connect.  I have a feeling the culprit maybe the .dat file that the how to asked to edit via vi.

Here's the command
```
$ sudo vi -b /etc/Wireless/RT61STA/rt61sta.dat
```

and here's the file (edited version working with WPA at my home network)
```
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
**[COLOR="Red"]SSID=MAKS[/COLOR]**
NetworkType=Infra
Channel=0
[COLOR="Red"][B]AuthMode=WPAPSK
EncrypType=TKIP[/B][/COLOR]
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
[COLOR="Red"]**WPAPSK=emezini11**[/COLOR]
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0

```

My question is are those highlighted parts causing the problem?  By doing this, did I "lock" my wireless card to a single network?  Would editing it make me access other AP's like "hotspots" or access my work AP?  How should I edit it (what should I put)?

---

### Post by whayong on 2007-03-03
Well what do you know............

I edited the file /etc/Wireless/RT61STA/rt61sta.dat and removed the values in those highlighted fields.  I was able to connect to schools AP (DHCP with no security).  This should mean that it can work in other hotspots.  I just need to try it at work now with WEP and static IP.

---

### Post by whayong on 2007-03-07
I don't think this solution is a permanent one.  I sometimes get a lock up and Edgy freezes when the .dat file is edited.

---

### Post by whayong on 2007-03-10
Is there anyone using RT61 drivers in multiple AP's?  How did you do it?

---

