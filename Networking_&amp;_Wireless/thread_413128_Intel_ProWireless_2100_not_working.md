---
title: "Intel Pro/Wireless 2100 not working"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by ryankhart on 2007-04-18
Hi, I have a problem with wireless and I've spent a LONG time trying to fix it.

When I first installed Ubuntu (Edgy), wireless worked out of the box (as it says here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel))

But now it doesn't work. I seems to have stopped working soon after I reverted back from XGL/Beryl. I tried that out and it was cool but was causing problems and crashing. I don't know if that could have done anything to it.

My wireless is set on eth1; I think that's default. Wired is eth0.

I even tried ndiswrapper. I didn't get that to work either. Now that keeps on saying "Permission Denied" every time I try to do something with ndiswrapper, and I was using sudo by the way.

But I don't think I should have to use ndiswrapper since the Linux Intel Pro/Wireless 2100 driver should make it work out of the box.

p.s. if you have the same problem, go ahead and make a short post saying so and maybe some of the experts will see it worth while to answer this thread. (Man I want to be a linux expert someday! I'm getting there, I only just switched from Windows to Linux in January 2007.)

---

### Post by SuperOmegaSlack on 2007-04-18
I had the exact same problem with my wireless after screwing up beryl...but it I got it and beryl to work after selecting the 2.6.17-10 kernel in grub when you boot.  I never figured out what I did wrong, but I gave up for a while, then I reinstalled ubuntu with the latest version of beryl, now everything works.

What I think happened was with the 2.6.17-11 kernel...when I reinstalled ubuntu, and updated, I made sure to install the driver for it after I installed beryl (although I don't think it matters), if you haven't, here is the link:
[http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

---

### Post by Undertwotimes on 2007-05-14
hmm My girl friends lap top has a problem with wireless after I upgraded to Feisty, and I did install beryl...  How could their be a connection though?  Seems odd to me.

---

### Post by kevmore on 2007-05-17
@ superomegaslack  I went to the link that you put in the post, and that is way above my skill level.  I am new to linux and only understand windows and dos.  Isn't there an easy way to do this??????

Pulling out what is left of my hair
Kevin.

---

### Post by ryankhart on 2007-05-17
btw. I got it working again. All I had to do was type in something about eth1 in the network config file thingy. Sorry I can't remember any more specifics. I thing beryl or some ubuntu update took out that eth1 line or something.

---

