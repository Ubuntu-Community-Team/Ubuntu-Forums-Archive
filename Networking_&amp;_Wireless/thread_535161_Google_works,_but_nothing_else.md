---
title: "Google works, but nothing else"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by erdalronahi on 2007-08-26
I installed Ubuntu on some computers that are connected to the same network. On one of them, a really strange problem occured:

The internet connection is incredibly slow, something like 1 byte per second. So the internet is unusable But: Google works! I can use Google search and news with full DSL speed - but nothing else!

I can ping every site on the internet, so there is no problem with the DNS. I already tried to blacklist ipv6, but that did not help. 

I tried Dapper, Edgy and Feisty all Live-CD and installation, and all have the same problem. They all hang at "scanning for mirrors" in the apt configuration if I do not cancel the network during the installation. 

Has anybody got an idea what causes this really strange situation?

---

### Post by K.Mandla on 2007-08-26
Could it be something ipv6-related? It's bizarre that only one of them has that problem, and across installations. Are you sure the network or a server somewhere isn't throttling that machine? Weird. ... :-k

---

### Post by erdalronahi on 2007-08-26
I don't think it's IPv6 related, though I am not sure. I don't know much about the network in the building. However, I blacklisted IPv6 in modprobe.d as shown somewhere in this forum, and it had no effect. 

On the same machine there is no problem at all under Windows XP, so even if there is a network related issue, there is still an Ubuntu specific problem in it.

---

### Post by K.Mandla on 2007-08-26
Is this machine different internally somehow? Is there a hardware difference or something? This is very strange.

---

### Post by punkrokk on 2007-08-26
are windows machines acting normal?

---

### Post by erdalronahi on 2007-08-27
There are no such problems under Windows. All machines are dual boot, so a comparison is possible.

The hardware of every machine is different, and some also turned out to have incompatible network hardware which was not recongized by the Debian installer. But this does not refer to the machine in question and should hardly produce this very problem.

It seems that virtually every connection (http, wget in Synaptic/apt-get or Aptitude) is kind of initiated, for instance the progress bar in Firefox shows 50% progress and the release.gpg files are downloaded. But after a few bytes eveything stops and nothing more is downloaded - Google being the only exception I have found so far.

---

### Post by punkrokk on 2007-08-27
Can you ping 4.2.2.2? Please post the output here.

Also, post the output of ip route and ifconfig here.

---

### Post by erdalronahi on 2007-08-29
I will, as soon as I have access to that machine again.

---

### Post by erdalronahi on 2007-09-04
I am sitting in front of that machine again. And I think the reason for the problem is the SIS191 PCI Gigabit card.

At the moment I can't even boot into Feisty, the boot process stops always a few milliseconds after it loads the driver for the network card. I have also found that lots of people have problems with that particular network card.

---

### Post by OneIdle on 2008-02-19
I have that exact same card and exact same issues with it. can connect to google/gmail/blogger
can also search in google but can not connect to any other links/sites

there is apperently a fix [***here***]("http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6") but it did not help me.

---

### Post by julien-1993 on 2008-02-20
exchange network card with one of the other pc, if the problem moves with the card then you are sure this is you problem, and then can replace the network card.

---

### Post by erdalronahi on 2008-03-17
The problem was probably the network card. I cannot remove it, because it is on the mainboard. The problem is the "sis190" driver.

In Ubuntu 7.10 I cannot boot the machine unless I blacklist the "sis190" driver. I have a second network card now, but this time the dhcp does not seem to work.

---

