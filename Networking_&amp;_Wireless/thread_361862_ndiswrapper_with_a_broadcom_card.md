---
title: "ndiswrapper with a broadcom card"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by lepban on 2007-02-14
Hey guys, i was wondering if anyone knows the problem with my wireless card

it is a broadcom **bcm4306** card,i installed the driver that comes with the card using ndsiwrapper. In the network manager it shows up as **eth1** **status: disconnected**

Here's the thing; on a previous installation of the _same_ version (edgy) with the _same_ cd, the wireless worked **flawlessly** :mad: .  After installing edgy the second time it just didnt work :confused: 

I suspect that the problem has something to do with the auto updates after a brand new installation.

If you have a suggestion or a suspicion as to the cause of the issue i would appreciate it alot.

Thanx again
-lep

---

### Post by Floppyjoe on 2007-02-14
Are you using a repository version of ndiswrapper?

---

### Post by lepban on 2007-02-14
yes from synaptic.  Utils version 1.9

---

### Post by Floppyjoe on 2007-02-14
I was using non-repository versions of ndiswrapper and had to reinstall them to get ndiswrapper to work again because the kernel update broke them.

---

### Post by lepban on 2007-02-14
Is there some sort of order when installing cleanly?  Should i download all updates b4 setting up wireless?  or set up wireless b4?  

would it make a difference?

---

### Post by Floppyjoe on 2007-02-14
I don't know if it will make any difference. Have you tried reinstalling ndiswrapper?

---

### Post by lepban on 2007-02-14
yeah i have, multiple times

---

### Post by Floppyjoe on 2007-02-15
Maybe a newer version of ndiswrapper would make a difference.

I have a walk through Url here:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

---

### Post by Ephack on 2007-02-17
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-ea76065f30b99d3b8472289cd049e2b141856b55](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29#head-ea76065f30b99d3b8472289cd049e2b141856b55)

This tuto was very helpful to me (see the hint about the card showing up as eth1) and somebody with the same card as you could use it too. Perhaps you could give it a try.

---

