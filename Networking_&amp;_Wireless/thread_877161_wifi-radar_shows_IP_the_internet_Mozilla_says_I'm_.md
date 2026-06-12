---
title: "wifi-radar shows IP the internet Mozilla says I'm still offline"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by sirjanselot on 2008-08-01
Hey guys,

I installed wifi radar and I was able to obtain an IP but when I use firefox, it says that I'm offline.  How can I fix this?

---

### Post by Ferux on 2008-08-02
I always have to hit the button 3 times: connect, disconnect, connect.

Then, it seems to work.


But I found a better program that allows you to connect at startup: Wicd
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by Tom--d on 2008-08-02
Remove Network Manager

```
sudo apt-get remove network-manager network-manager-gnome --purge
```

Done :D
No more Offline!

---

### Post by CatSpin on 2008-08-02
> **Tom--d said:**
> Remove Network Manager

```
sudo apt-get remove network-manager network-manager-gnome --purge
```

Done :D
No more Offline!

I'm not sure how wise it was to just paste in a terminal line found in a forum, but I was having similar problems as the OP. I tried the sudo line above and now not even a wired connection works.

As a linuxnewb, I'm just going to come out and say it, how do I undo what the above terminal line did?

My wireless issue hasn't gone away so I'm having to use a different (xp) computer to write on the forum... help would be apprieciated here!

---

### Post by Ferux on 2008-08-03
The 'inverse' of remove is 'install' (as far as I know since i'm still a noob too).

So:

sudo apt-get install network-manager network-manager-gnome

would do the job, but it's possible that this removes the wifi-radar since Linux doesn't like more than one wireless network manager..

---

### Post by CatSpin on 2008-08-04
> **Ferux said:**
> The 'inverse' of remove is 'install' (as far as I know since i'm still a noob too).

So:

sudo apt-get install network-manager network-manager-gnome

would do the job, but it's possible that this removes the wifi-radar since Linux doesn't like more than one wireless network manager..

Yeah, this would make sense, but I think that the '--purge' bit means that the install files are also wiped (does that make sense?), which means to get them it requires an internet connection.

---

