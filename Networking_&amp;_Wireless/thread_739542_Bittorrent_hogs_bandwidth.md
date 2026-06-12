---
title: "Bittorrent hogs bandwidth"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by varangian on 2008-03-29
A common complaint from ISPs I know, but this is a more local nuisance. I've tried a few torrent clients under Ubuntu (Gutsy) and the behaviour is the same, if the client is allowed an unlimited u/l speed  (or a limit close to what's achievable on my ASDL connection) when seeding then the connection becomes pretty useless for anything else. E.g. Firefox takes minutes to load a simple page that should take seconds or just hangs.

Booting the same system into XP and allow utorrent (which I use under Wine on the flip side) the same unlimited u/l and the story is different, Firefox browsing is slower as you'd expect but it's 30 seconds tops for most pages. As the u/l speed achieved under both is about the same it doesn't appear to be the case that Ubuntu is making more efficient use of the connection, it just doesn't appear to share so well.

Currently I just toggle the max. u/l speed which works but isn't too elegant. Anything else that I can do with the current set up? I guess a smarter router with QoS would be the best bet in the long term.

---

### Post by Oldsoldier2003 on 2008-03-30
> **varangian said:**
> A common complaint from ISPs I know, but this is a more local nuisance. I've tried a few torrent clients under Ubuntu (Gutsy) and the behaviour is the same, if the client is allowed an unlimited u/l speed  (or a limit close to what's achievable on my ASDL connection) when seeding then the connection becomes pretty useless for anything else. E.g. Firefox takes minutes to load a simple page that should take seconds or just hangs.

Booting the same system into XP and allow utorrent (which I use under Wine on the flip side) the same unlimited u/l and the story is different, Firefox browsing is slower as you'd expect but it's 30 seconds tops for most pages. As the u/l speed achieved under both is about the same it doesn't appear to be the case that Ubuntu is making more efficient use of the connection, it just doesn't appear to share so well.

Currently I just toggle the max. u/l speed which works but isn't too elegant. Anything else that I can do with the current set up?** I guess a smarter router with QoS would be the best bet in the long term**.

yes i think thats the best bet. you could limit the amount of connections but the clients will still suck all the bandwith they can get.

---

