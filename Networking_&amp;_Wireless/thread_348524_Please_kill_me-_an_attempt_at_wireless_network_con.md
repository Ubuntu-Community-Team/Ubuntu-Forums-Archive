---
title: "Please kill me- an attempt at wireless network configuration"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by zalberico on 2007-01-28
Welcome to hell with wireless networking in ubuntu thanks for your help in advance, here's whats going on...
1. My friend needed to be liberated from his disgusting microsoft windows operating system, so I installed linux.  He has a Belkin FD57000 PCI card,(for people in need of a how to, the best one I found is here: [http://www.jinx.com/forum/topic.asp?TOPIC_ID=45498](http://www.jinx.com/forum/topic.asp?TOPIC_ID=45498)) 
2. Interestingly enough that how to worked! we thought we were complete, finished.  We had been working on the computer at my houseand the card was recognized and we were online, life was good.
3.  We brought the computer back to my friends house where internet worked on initial configuration, but then stopped.  The card is recognized.  Internet just stopped.  We moved the computer thinking it may have been a router range problem.  What  now?
4. We are contemplating reinstalling ubuntu and starting that how to from scratch at my friends house and not mine.What do you think?
5.  Don't get me wrong, I love linux, but its a good thing my friend his patient because the claws of microsoft were so bad he doesn't want to go back even after this.  What I don't understand and think is weird is that it was working and for no reason stopped!
6.  On another note, his ethernet (built into motherboard) was seen by linux initially, but now is not.  We cannot connect to ther internet at all.  Even the live cd doesn't see his ethernet for some reason.  Thanks!

(running on an i386 edgy ubuntu)

zman:(

---

### Post by yigal.weinstein on 2007-01-28
DO NOT REINSTALL.  Your card is well supported in the wiki section.  
What does your /etc/network/interfaces look like it sometimes gets messed up if there are multiple times you configured the card.

You can use ndiswrapper and follow this link:
[https://help.ubuntu.com/community/WifiDocs/Device/F5D7000](https://help.ubuntu.com/community/WifiDocs/Device/F5D7000)

Or use,
[https://help.ubuntu.com/community/Rt2500WirelessCardsHowTo](https://help.ubuntu.com/community/Rt2500WirelessCardsHowTo)
if the wifi is version >= 3 which it probably is as this is the driver you want (the link to this site is on the above link).

best

---

### Post by zalberico on 2007-01-28
Thanks, it may be too late because my friend is not online and I can't reach him.  He may reinstall.  I hope I get to him before he does so we can check it out.  and we already installed ndiswrapper from synaptics package manager as I was instructed to do so in the above how to.  Who would've thought getting a broadcam apple card to work would've been easier??
zman

---

