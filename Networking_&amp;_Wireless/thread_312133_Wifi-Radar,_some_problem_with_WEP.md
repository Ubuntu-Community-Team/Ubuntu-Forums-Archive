---
title: "Wifi-Radar, some problem with WEP"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by zpro on 2006-12-03
well, I do have a wireless connection working, using dhcp,
and NO wep

Network setting for wireless card:
essid: linksys
dhcp
---
wifi-radar see the connection, and connect automatic.. good.
plus it see a near by connection as well. ( not mine )
-------------------------
NOW the problem
when I turn on the wep in the linksys router, using 128bit encryption
(lets say password: blueberry ) there are generated key codes
key one: 123d3d3d698s87d7d555.....(etc)

I have tried both ways, password and key one code to access the network,
via wifi-radar.

I try putting the password into the Network Setting (xubuntu),
nope, so no matter which way I go, the connection via wifi-radar can't pull a ip address, with wep security turn on.
--------------
There no doc on what to put what where ??? :-(

So, anyone that can help to connect the two, networking setting and wifi-radar usingwep.... 

TKS ](*,)

---

### Post by SuperMike on 2006-12-04
Did you hear the news? A woman recently beat those bad guys at the [RIAA]("http://en.wikipedia.org/wiki/Riaa") and [MPAA]("http://en.wikipedia.org/wiki/MPAA") by not turning on any encryption with her Wifi router. She played dumb in court and won the case. She was being sued for downloading music and videos and all she had to do was claim she didn't know who was doing it and her lawyer suggested that it was because she used wireless Internet and didn't realize she had to turn on the encryption to keep herself secure. (I bet the woman was smarter than this, but it's a fantastic defense.)

Here's what I'm suggesting instead. Learn how to make an [iptables script]("http://supermikenews.blogspot.com/2006/03/roll-your-own-linux-firewall-script.html") and turn on a local firewall. Then, just leave your Wifi unencrypted. At that point, you can download songs and videos and do any other activity you want on the Internet. You'll end up getting off the hook in court if the RIAA or MPAA take you there.

Here's what I found after doing some distance testing with the Linksys. You'll find that people can get on your Wifi from a distance of only about 400 feet with a clear line of sight. If they add a Cantenna-brand cantenna, they'll be able to go about 600 feet with clear line of sight, and only about 300 feet without clear line of sight. If they get a yagi antenna high up on a pole, and with a dish behind it, they might be able to pick up your Internet from about a half mile away, but no further unless they have a clear line of sight. Even if they do pick it up, it will be spotty and you really won't have much of a bandwidth hog on your network.

So, figuring with those stats, you could share your Internet with "the needy", which is sort of like a good cause. Plus, with the firewall on your local system, they can't touch you.

---

### Post by zpro on 2006-12-04
> **SuperMike said:**
> Did you hear the news? A woman recently beat those bad guys at the [RIAA]("http://en.wikipedia.org/wiki/Riaa") and [MPAA]("http://en.wikipedia.org/wiki/MPAA") by not turning on any encryption with her Wifi router. She played dumb in court and won the case. She was being sued for downloading music and videos and all she had to do was claim she didn't know who was doing it and her lawyer suggested that it was because she used wireless Internet and didn't realize she had to turn on the encryption to keep herself secure. (I bet the woman was smarter than this, but it's a fantastic defense.)

Here's what I'm suggesting instead. Learn how to make an [iptables script]("http://supermikenews.blogspot.com/2006/03/roll-your-own-linux-firewall-script.html") and turn on a local firewall. Then, just leave your Wifi unencrypted. At that point, you can download songs and videos and do any other activity you want on the Internet. You'll end up getting off the hook in court if the RIAA or MPAA take you there.

Here's what I found after doing some distance testing with the Linksys. You'll find that people can get on your Wifi from a distance of only about 400 feet with a clear line of sight. If they add a Cantenna-brand cantenna, they'll be able to go about 600 feet with clear line of sight, and only about 300 feet without clear line of sight. If they get a yagi antenna high up on a pole, and with a dish behind it, they might be able to pick up your Internet from about a half mile away, but no further unless they have a clear line of sight. Even if they do pick it up, it will be spotty and you really won't have much of a bandwidth hog on your network.

So, figuring with those stats, you could share your Internet with "the needy", which is sort of like a good cause. Plus, with the firewall on your local system, they can't touch you.

Thanks Mike,
however, this is not what I'm looking for.. just need wifi-radar working with wep key. as stated above.

:)

---

### Post by zpro on 2006-12-04
Some one has to be using this application wifi-radar... :-k

---

