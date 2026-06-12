---
title: "[SOLVED] QuickSynergy - Ubuntu to SynergyKM - Leopard"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by canoo on 2008-10-29
Hello,

I'm looking to setup synergy on my desktop (ubuntu) and my macbook.

i'm going to use my ubuntu desktop as my server. in quicksynergy i have the "Right" set as "MacBookPro" (name of my macbook in leopard). on my macbook i set the server ip as the internal ip address for my ubuntu machine (192.168.1.100). in ubuntu the server appears to start (running in the background im assuming). in leopard when i turn synergy on it says "connection refused".

I cannot for the life of me figure it out. any help would be appreciated.

- Jon

---

### Post by canoo on 2008-10-30
I managed to get things working.

just a note if anyone goes to do this setup anytime soon. i named my macbook "MacBookPro" but leopard adds ".local" on the end.

so if your using leopard as your server, when you go to give the client the host name you have to add ".local" on the end. for me it was "MacBookPro.local"

im glad i have this working now. who needs windows when youve got leopard and ubuntu?! :p

---

