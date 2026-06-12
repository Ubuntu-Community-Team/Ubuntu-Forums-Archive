---
title: "Conflicting Applications"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by ParadoxMDB on 2007-08-28
Hi,

Just recently I have had some very odd problems with my Ubuntu Feisty Fawn box. I have a ircd running on ports 6667 and 7000 (for ssl), when ever I try connect to the ircd from any other machine on the LAN it just times out, dont get me wrong, the ircd has been setup correctly and does listen on the LAN ports. This doesnt just limit to the ircd, but it seems as if the entire network for the ubuntu box has gone haywire (I find this odd because I havent logged into it for months), I cannot access the apache2 server on it through the LAN anymore either, as well as ssh into it.

Last night I was on the verge of ripping my hair out, when I decided to restart samba and apache2 as a last resort - everything seemed to work perfectly fine there after, i could ssh in, view the apache2 www dir through http protocol and even connect to the ircd.

This morning I woke up and noticed the laptop (on which the server is installed on) was off, after coming to realize that the AC power cord wasnt plugged in.

Now its back to square one, it seems as if some application is conflicting on the server and causing the haywire of communication to the server. I tried restarting samba once again, and even killing it, but nothing happens or changes.

Could any one possibly help me out? Please!

---

