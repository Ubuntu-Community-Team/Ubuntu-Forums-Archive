---
title: "Wireless RTL8187 with Ndiswrapper Disconnects"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by Jexel on 2007-12-26
Okay I've had problems with RTL8187 drivers before but ever since Gutsy it's gone downhill once more.

Using the default gutsy drivers for RTL8187 fails miserably. I can connect for around 5 minutes and I get disconnected and I can't even reconnect...so I gone back to this guide:

[http://ubuntuforums.org/showthread.php?p=2973537#post2973537](http://ubuntuforums.org/showthread.php?p=2973537#post2973537)

I did everything in the guide except I compiled my own Ndiswrapper. It worked fine. However, what I've noticed is that it stills disconnects me, but every few hours...this is much better than every few minutes but it can still get annoying at times as I'll have no idea when it disconnects me. I'll be using Pidgin and all of a sudden nobody is replying to me even though Pidgin is still "connected", I would try and go onto google and nothing would appear.

I would then run the command```
 sudo /etc/init.d/networking restart
```
to try and fix my problem and around 1/3 times it works. The other two times it doesn't and I've noticed that when it fails to restart there is a line that reads

```
There is already a pid file /var/run/dhclient.wlan0.pid with pid #######
```

So my question is this. What does this mean? And how do I fix it?

Your help is greatly appreciated.

---

### Post by kevdog on 2007-12-26
When you get the pid message, try typing 
sudo dhclient -r

Also someone in another post mentioned compiled the realtek drivers from the realtek website.  I asked for specific instructions and they never posted back.  Sorry. I dont own a realtek wireless chipset.

---

### Post by Jexel on 2007-12-27
thanks a lot, i'll give it a go once I get this problem again

---

