---
title: "default network connection problems"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by elashish14 on 2007-11-26
Hi all

I think I have a serious problem. I live in an apartment with many wireless networks running. My computer is automatically connecting to some of them which have the same name as the networks that are running on my campus, and I'm certain that it's being done by some people that just want to hack into computers with unsuspecting users.

In essence, what I need to know is if there is any way that I can change/delete what networks my computer is automatically connecting to? It would help me out a lot, thanks.

ashish

---

### Post by spd106 on 2007-11-27
Yes you can, but it will require a bit of work.

What you need to do is contact the a network administrator and ask for a list of bssids, which are essentially the mac addresses of the wireless APs on the network. You then enter these into  gconf under /System/networking/wireless/networks/"network name". Make sure that you remove any bssids that are not in the list. See [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) for more details.

Now you should just connect automatically to the nearest AP.

Ideally there should be an encryption key or certificate based authorisation system for logging onto the network to prevent this kind of problem.

---

