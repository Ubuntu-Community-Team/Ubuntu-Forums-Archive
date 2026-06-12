---
title: "Wi-Fi radar cannot find ip address?"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by PsychoticSheep on 2007-02-27
How can i correct this or find out what the ip address should be and enter it manually? I am trying to connect dapper to xp using ad-hoc connection.

Thanks in Advance

---

### Post by sythem on 2007-03-19
I've tried every wireless lan manager available from the default repositories and NONE of them will connect to my XP shared wireless network. One will make a successful conection, but then not get an ip address or gateway, the rest won't even connect. Wireless works fine when connecting to the campus wireless in the lobby and at the library, but not my ad hoc. Any suggestions? I'm running 6.10.

---

### Post by sythem on 2007-03-20
Ok PsychoticSheep, I figured this out manually.
Do an iwlist to get all the info about your ad hoc network. In another console window, do this with your own information. You don't need the quotes.
```
iwconfig "eth1" essid "potato" mode "ad-hoc" channel "9" key "s:12347" ap any
``` The s: in the key is for ancii, if you use a hex key you won't need that if you don't use encryption at all you won't need the key section at all. After you have that set up correctly do this.
```
ifconfig eth1 up
dhclient eth1
```
That should get your computer connected. It worked for me when nothing else would.

---

