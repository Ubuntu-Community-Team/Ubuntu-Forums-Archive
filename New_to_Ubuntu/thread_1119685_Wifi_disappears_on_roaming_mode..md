---
title: "Wifi disappears on roaming mode."
date: 2009-04-08
forum: New to Ubuntu
---

### Post by mistaPJ on 2009-04-08
First of all I am still a learner so simple explanations would be great thanks. I have recently been changing the channel my wifi broadcasts on to try to reduce interference. I have installed kismet to monitor the channels my neighbours use, so I can try to minimise interference. Often it seems to work fine but occasionally the network disappears, and sometimes the SSID we have given it ("Forrest Palace") is replaced by the generic "Linksys", although I can't connect to the "linksys" network. This happens on channels 1, 6 and 11, so changing channel hasn't solved the problem. My flatmates use XP and Vista and have less connection problems than me.

I use a dell inspiron 6000
IWP2915 wifi card
Linksys WRT54g Ver.7 wireless router
Ubuntu 8.4

I have tried disabling the roaming mode and manually configuring, but don't know how to do it, so it didn't work. Would learning this reduce interference anyway?

Are there any other tips or tricks anyone can think of that could help resolve the issue, reinstall drivers? Update firmware? Install ubuntu 8.10? It can be very annoying, sometimes it keeps jumping around for days on end.

Thanks.

---

### Post by zerhacke on 2009-04-08
I'll bet you a cup of coffee that there's another network with the SSID of Linksys near you and you're too far from Forrest Palace to connect to it.

Also, Linux wifi does not like spaces in the name of the network.

---

### Post by mistaPJ on 2009-04-08
When it's there "Forrest Palace" is the strongest network, it has happened with the laptop less than 1 metre from the router, when I occasionally see linksys it has the same signal strength as Forrest Palace should, depending on which room I am in, furthermore the two never co-exist, I would add that kismet never picks up a signal from any network called linksys, so I guess you owe me a cup of coffee?

However, I'll try changing the SSID to one word, if that works then I guess we can call it quits, but I'm not convinced yet...

---

### Post by mistaPJ on 2009-04-08
Right I've done that and changed the SSID to "Palace", if the network starts to alternate between all 3 names from now on I think you owe me 2 cups of coffee...

---

### Post by fatdadkev on 2009-04-13
A couple of things I did - My network uses WPA2 and I sometimes had it drop and then reconnect which I put down to the key rotating in WPA and somehow the two loose sync.

I installed WICD [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) which replaces the standard Ubuntu network manager, however ... I find it more robust on my network and the problem has gone away.
One advantage of WICD is that you can pre-configure networks so it remembers the ones you prefer to connect to and it makes roaming around a breeze.

I also changed the key rotation time in the router from the default 30 seconds to slightly longer - not really advised if you don't need to, the longer your key remains active the easier it is for someone to hack and identify it - this seemed to help even more, it just seemed to make the connections totally stable and no dropping off. I will say an XP machine had the same issues so I think it was a router problem not particularly isolated to the client machines and changing the key rotation time was the bit that helped the XP machine.

Kismet is handy to locate everything around and channel they are using etc , but a good program to check if anything is connected to your network that shouldn't be is etherape (Ether Ape) it graphically shows the network, you might be having issues because something else is trying to connect or interfere ? I use Etherape to check what's active on my network and very handy it is (it's in the Ubuntu Repositories for 8.10).

---

