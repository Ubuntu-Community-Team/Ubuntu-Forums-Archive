---
title: "Network Manager won't connect wireless"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by hedgefighter on 2007-01-11
Hi,
I'm trying to get my wireless setup on my Dell E1405. I'm pretty much done but I have one snag. I got my Broadcom 4311 card working with ndiswrapper and the wireless was working fine without network manager.  But I wanted network manager. So, I turned off the interfaces in /etc/network/interfaces and installed network manager. After reboot the manager came up and it handles my wired connection just fine and it sees my wireless network correctly, but when I try to connect it just sits there trying to get an ip. I'm not sure what's the issue. Thanks a lot.

---

### Post by @trophy on 2007-01-11
> **hedgefighter said:**
> Hi,
I'm trying to get my wireless setup on my Dell E1405. I'm pretty much done but I have one snag. I got my Broadcom 4311 card working with ndiswrapper and the wireless was working fine without network manager.  But I wanted network manager. So, I turned off the interfaces in /etc/network/interfaces and installed network manager. After reboot the manager came up and it handles my wired connection just fine and it sees my wireless network correctly, but when I try to connect it just sits there trying to get an ip. I'm not sure what's the issue. Thanks a lot.

Does your AP use WEP or WPA?  If it's WPA, that could be why.  I'm in pretty much exactly the same boat as you right now, except with an orinoco card.  Finally got the card + network manager to work, and now it won't connect to any WPA networks... ](*,)

---

### Post by hedgefighter on 2007-01-11
It uses WEP but I turned the encryption off. But I just don't understand why network manager has a problem when iwconfig works fine.

---

### Post by triwave on 2007-01-22
I have same sort of issues.

I did not previously use Network Manager and just manually configured my WEP enabled network. It connected fine and reliably for several months.

Then I discovered Network Manager and thought that would be a better way to move from a WEP network to a hotspot and back and forth without re-typing 128 bit WEP key all the time.

Edited my config file and network manager scanned all the near-by networks (there are at least 15 - I live in an apt). I added another connection because I don't broadcast my SSID and everything connected fine. I got asked for a password for a token ring application ?? Not sure what that was but I entered one ... :confused: 

Now whenever I try to re-connect to that network in my apt my network manager by default connects to my neighbors unprotected AP not mine. If I select mine from the drop down list it never connects anymore ... says it's trying to exchange keys with the AP.

Anybody have any suggestions?

---

