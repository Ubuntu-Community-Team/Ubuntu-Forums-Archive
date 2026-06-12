---
title: "USR 56K Faxmodem v.92 not working in Dapper"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by remle on 2007-02-24
Hi, i've been using a broadband connection as my internet connection even before i installed Dapper. But now i want to use my USR 56k v.92 (firmware upgraded from v.90) on my Dapper installation, for times when i have to go online even when my broadband is down. I tried installing the modem via the guide i saw somewhere in this forum. I guess i have installed it right, even tried using pon, but the problem remains the same. The system can detect my modem, it can even dial-out, but after a few seconds of the ISP computer responding to my modem, the sound just shuts-off, and it will not connect. I have tried using this modem in win xp, and red hat 7, and it works fine. Are there any particular installer for v.92 modems? If yes, where can i download one suitable for my modem? 

P.S. 
 My modem's a USR 56k Faxmodem Serial modem, 245630-00

---

### Post by _duncan_ on 2007-02-25
It's probably an initialization string problem specific to older models of USR faxmodems. Please take a look at [[COLOR="DarkOrange"]this[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=271111") thread. The 4th post contains the init string needed to get the modem working.

The 2nd link on my signature (Dial-Up Modem Wiki) contains a wealth of information about setting up dialer programs.

---

