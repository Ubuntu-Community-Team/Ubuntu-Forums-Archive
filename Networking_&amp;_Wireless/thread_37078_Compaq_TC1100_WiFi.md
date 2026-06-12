---
title: "Compaq TC1100 WiFi"
date: 2005-05-25
forum: Networking &amp; Wireless
---

### Post by cruteme on 2005-05-25
Hello All,

I am brand new to Ubuntu (not to Linux in general) and I really like what I see, you guys are doing an awesome job.

I have a Compaq TC1100 tablet PC and I am having issues getting the wireless network card to function properly. Rumor has it that this is an Intel ProLan 2100 miniPCI card. Hoary is detecting it as an Atheros AR5212 802.11abg NIC which fits the profile with the exception of the manufacture. 

Problem #1: The wireless card is turned off and I can't turn it on. The wireless card uses a software switch to turn the card on and off, there is no physical switch whatsoever, and when the card turns on a neat little light on the display lights up. Currently the card is off and I have no idea how to turn it on.

Problem #2: Before the card got turned off (I don't know how) I tried to connect to first my Linksys 11 Mbit wireless router then to my Apple Airport Express access point. Both where unsecured (no wep, no mac filter) and when I fed the SSID to Hoary it looked like it was going to work and then it timed out. How do I make this work? Also is there a tool out there to scan for Access Points in range and connect to them?

Right now I am running the LiveCD version of Hoary as my hard drive is toasted and I am waiting for the replacement to arrive but I would still like to get this working on the LiveCD before I try a full install, if I can't get this to work I am going to have to use Windoze (much to my dismay) as I MUST have Wifi. Anyone who can help please let me know. Thanks!

---

### Post by cruteme on 2005-05-31
Got this to work... as it would appear my card was looking on the wrong frequency so i changed it using iwconfig and it works like a charm. Thanks to hamstar on this thread... [http://www.ubuntuforums.org/showpost.php?p=132161&postcount=6](http://www.ubuntuforums.org/showpost.php?p=132161&postcount=6)

---

