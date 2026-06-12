---
title: "Starting to dispair"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by hcorey on 2007-10-24
After spending hours on google and this forum, I am surprised that problems in Gutsy's wireless capabilities has not yet been solved. I have a new install, and I am using a NEC/Aterm WL11CB Warpstar networking PC card. I believe this card uses the Orinico_cs driver.

The card is recognized on boot-up, and I am able to connect initially, but the connection is always dropped within a few minutes. This is true weather I use Network Manager, use roaming or not-roaming, substitute WICD, or the command line (as posted in this forum for "command line" troubleshooting). This is true if I comment out I comment out IVP6 reference in  modprobe.d/alias, restart the network and wireless by the command line, or try to connect at home or try to connect at work. 

The card itself works well, and I can connect well using a Mandriva 2008 live CD.

I would be delighted if anyone has any thoughts. I have looked at the confirmed bug reports in launchpad, and I don't know if this problem has been confirmed/escalated.

thanks.

---

### Post by gb5uqx on 2007-10-24
There are hundreds of posts regarding this problem. Like you I have tried everything to no avail. I did think it was specific to RT61 cards but there are examples of many others being affected by the identical problem so it definately looks like a Gutsy issue. Damned annoying because I now have everything else just perfect.

Fingers crossed and waiting................................

---

### Post by chili555 on 2007-10-24
> There are hundreds of posts regarding this problem.???? There are only two posts on the whole forum about the WL11CB, both from hcorey. As well, the orinoco_cs and the RT61 are two *very* different animals.

I have an orinoco_cs card that works perfectly with a bit of fiddling on one of my machines, and, so far, won't work with massive amounts of fiddling, on another.

What got it to work was to add to /etc/modprobe.d/blacklist the following:```
blacklist  hostap
blacklist  hostap_cs
```Just because I'm overly careful, I restarted the machine and it works fine. I doubt I could state any scientific reason why this works, but it works for me. I hope it works for you.

---

### Post by gb5uqx on 2007-10-24
Go back and read my post again comrade. I was not, for some time aware that the problem of random unexplained disconnection was not limited to the RT61 card for which there are litterally hundreds of posts, but it is now clear that other examples are appearing, as I outlined above. We do though, seem to be looking in the same area.

It would be interesting to see if others with affected RT61cards beside myself can restore the connection with a simple 'modprobe -r iwl4965' command.

---

### Post by hcorey on 2007-10-25
What I meant by despair (sorry for the spelling) is that I count over one hundred bug reports in Launchpad on the general issue of Network Manager, nm-applet and connection issues. While I am well aware that these may be due to a variety of causes, none have risen above "undecided" and "medium" in importance. I, for one, rely on wireless networking and I expect a full release for a mature distribution to make wireless networking "just work", without haveing to spent hours on this forum hoping for a solution (like Network Manager 0.7) to pop up.

---

### Post by hcorey on 2007-10-26
(Parital solution): I tried a new(er) wireless card, the Netgear  WG 511T, and things have improved significantly (but still not perfect). The connnection stays up longer, but does still drop out periodically without automatically reconnnecting. Rebooting solves ths problem. 

I suspect  there is something in nm behavior, when trying (and failing) to connect to the best possible network if the signal weakens. Perhaps the newer card maintains a better connection, making dropouts less common.

---

