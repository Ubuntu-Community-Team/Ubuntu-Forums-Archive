---
title: "Problems with network key (WEP) in Xubuntu"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by d00derino on 2008-01-08
Suprisingly, I found installing Xubuntu far easier than Ubuntu, albeit I'm sure the computer it's running on can fair much better with Xubuntu than Ubuntu. Sadly, I have one more problem before I can play around with it. I can't get the damn thing to connect to the internet.

I was shocked when I saw that my wireless adapter was read right after plugging it in. I have a LinkSys WUSB54-GC bought specificially because it works well with Linux. The network manager sees 2 neighboring networks, mine, and another one (I assume the neighbors). Anyway, what doesn't work is entering the WEP key for my home network. I get maybe 30 seconds of it trying to connect, then it asking me for the key again. And again. And again. It's a 128-bit encrypted WEP -- your standard 24(?) character mess of random hex values. However, I can't tell if it's a passphrase, 128bit ASCII or 128bit Hex value. I tried two of them (after typing it in for ASCII, the connect button never became available, therefore I tried passphrase and Hex) and neither worked. How do I tell if the system is open or a shared key? I've never heard of that before. 

I also tried to connect to the other network (which has no password), but network manager kept trying to get the key for my home network and ignored my neighbors network. Why? 

Can anyone help me with this? Do I need to install anything? I didn't need ndiswrapper (which I dont think works with Xubuntu anyway) or anything else, so I could be missing drivers or whatever.

---

### Post by JanvL on 2008-01-17
I have the same problem, but I am not shure whether it is not the normal
settings for IP-adress submask etc.
I have only tried this from the livecd untill now.

Jan

---

