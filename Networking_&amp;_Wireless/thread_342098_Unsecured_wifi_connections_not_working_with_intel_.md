---
title: "Unsecured wifi connections not working with intel 3945"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by lcaley on 2007-01-19
Hey everyone, I've seen a lot of threads about this exact subject, but I can't get anything so far to work for me. I have a HP dv5000 laptop, with an Intel PRO wireless 3945 wireless card. My wireless card works perfectly fine at home, but I can't connect to any unsecured public hotspots (internet cafe, library, etc). I have a G network, with a hidden ESSID and WEP at home. I read a thread that said that installing wifi-radar helped someone else, but the problem is that for me to test it, I have to go somewhere, and if it doesn't work, I have to come back home for more research, so I was hoping for a few more thoughts on the matter before I drive across town for a hotspot. Anyone have any magical fixes for this? Of all the problems I've had with linux in the past, this is probably the strangest. Thanks in advance for any ideas.

---

### Post by scrooge_74 on 2007-01-19
Wifi-radar will definetly give you a hand.  Ubuntu sometimes is tricky to connect to wireless, as an example yesterday I  was at my brother in law house and it took me a while before I got online, but the funny thing is that I have been online there in the past and had all the settings already.

In theory at most you should only need to pick the network you want to connect.

You should toy around with Wifi radar at home before going out

---

### Post by lcaley on 2007-01-19
Ok, perhaps I'm not using wifi radar correctly, but it doesn't look too complicated. Assuming there's no secret to wifi radar, I can't get it to connect to anything -- even my home network that I can make work correctly with the network-admin tool. What am I doing wrong? Do I have to enter the ESSID into the network-admin tool as well as connect with wifi radar?

---

### Post by scrooge_74 on 2007-01-19
Is a little of all of te above, sometimes wifi will get me connected right out, other times is the network manager.  Wifi radar has some options that you can put into it

also if you do iwlist eth1 scanning will get you all details about the networks you are trying to connect. Between all of them I have manage to connect to a couple of networks

---

### Post by lcaley on 2007-01-19
lol ok, thanks for the replies, I actually think I have gotten wifi-radar to work, though, I don't know what I'm doing differently now. Maybe some magic happened when I restarted for the 1001st time, who knows... hopefully wifi will get more reliable in future releases

---

