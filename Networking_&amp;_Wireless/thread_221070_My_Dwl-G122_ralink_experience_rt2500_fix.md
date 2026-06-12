---
title: "My Dwl-G122 ralink experience rt2500 fix"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by marchingon on 2006-07-22
Hi there I am very new to Linux and Ubuntu, so I am making a ton of mistakes and finding thru the incredible websites and chatrooms finiding direction to fix and fixes.
Most of what has gone seriously wrong I think has come back to something I have done. On that note.

The symptom of the USB wireless card  D-link DWL-G122 locking up my system and causing a hard lock requiring reboot. 

I believe was caused by trying to configure while something related was open,( browser window or such).

The fix for me was to get set up so I could log into root and manually edit the "interface" file under /etc/network

the " auto inet raub0 " was missing just before the WEP key enteries and need to be replaced??
final entry that worked looke like this

auto rausb0
iface rausb0 inet dhcp
wireless-essid "name of ssid here" without quotations
wireless-key s:"wepkey here" without quotations

I see the symptom has been out there but the fixes seem to be vaired so thanks for checkin into this one. 

As I am not a programmer I have no concept of how hard an entry in this file would be to to make it abort the process on error rather than lock up hard or what it would look like.

Thanks for all the great OS and all the help. 
Cheers

---

