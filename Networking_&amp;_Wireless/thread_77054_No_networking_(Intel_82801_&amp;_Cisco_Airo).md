---
title: "No networking (Intel 82801 &amp; Cisco Airo)"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by mbr on 2005-10-16
Dear (K)ubuntu guys, having a lot of trouble with Breezy;

I used to be happy with Hoary, although only my Cisco Airo Wifi card worked, wheras my LAN Intel card didn' work at all. However, I stuck with Wifi which was fine. 

I tried Breezy and guess what? NONE of these two interfaces were working, even after trying everything :confused: 
[LIST]
[*]Didn't get IP by DHCP with my Ethernet card
[*]Wasn't able to set essid & key with the WiFi card
[*]Of course I wasn't able to get an IP by DHCP with WiFi
[/LIST]

```
Facts:
Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)
Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

```

No I am back at 5.04, but I can still test networking issues with the 5.10 LIVE, if you have any specific suggestions ;-)

For my 5.04, Cisco Ario works fine with the "airo" kernel module, the Ethernet card doesn't work at all (e100 module is loaded).

Anyone seen this problem ?

---

### Post by Teroedni on 2005-10-16
hmm thats strange that Hoary supports it and not Brezzy. Have you looked in Bugzilla after your card?

If not submit the problems so the developer can now about it , and perhaps it will get an fix:p

---

