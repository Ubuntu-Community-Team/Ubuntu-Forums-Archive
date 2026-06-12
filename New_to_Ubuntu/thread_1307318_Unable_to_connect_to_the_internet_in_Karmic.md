---
title: "Unable to connect to the internet in Karmic"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Viva on 2009-10-31
I just installed Karmic Koala and I can't connect to the internet. I have a broadband connection(I connect through a USB modem) that requires me to login, so as I did with jaunty, I opened the network manager, went to the DSL tab and entered my username and password. I'm still unable to connect to the internet. I have a motorola surfboard SB5100 USB cabel modem(according to windows xp:()

---

### Post by Viva on 2009-10-31
Sorry to bump this, but could it be a problem with the privileges? When I try to edit the connection, it is giving me an error that I have insufficient privileges. It is also asking me for the password every time I mount a partition(I had an option to remember the password in jaunty). I'm attaching a screenshot of the error message.

---

### Post by nialui on 2009-10-31
i have same problem...

---

### Post by Viva on 2009-10-31
Looks like there is a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205"). Hopefully they'll fix it soon.

---

### Post by nialui on 2009-10-31
@viva:
Actually someone in that thread ([Alexander Sack)]("https://launchpad.net/%7Easac") offer some solution, and many users fixed the problems. 

But not for me, since i don't really understand how to patch in linux.

---

### Post by Viva on 2009-10-31
Neither can I. I guess we'll have to wait for the updates.

---

### Post by skyiscrying on 2009-10-31
Did you try SYSTEM->PREFERENCES->NetworkConnections? There is something there about DSL which might help you. I have an earlier model of that modem and now use an ethernet connection cable from it to the computer. I have had no problems.

---

### Post by Nightstrike2009 on 2009-10-31
Me too use vodaphone 3g worked with Jaunty 9.04 borked with Karmic 9.10 many users have same problem. For some inserting MicroSD card inside its reader before attaching makes it work but doesn't work for me.

In my view this should have been sorted out as bug was reported before Karmics release, but still there, this will annoy many new users and discourage people from installing Karmic on notebooks/laptops. I for one Iam not impressed at this at all, release should have been delayed until sorted. :-(

PS: does anyone know the names of .deb packages affected so know which updates to look for? & how can we update with no internet connection? 
(I write this on Windows XP, as dual boot set-up)

---

### Post by Viva on 2009-10-31
I fixed it for now using ppoeconf. I'm posting this from karmic right now. It is a network manager error.

---

### Post by Nightstrike2009 on 2009-10-31
How do you do that? what is ppoeconf? could you please advise? many people have this problem

UPDATE:I have located ppoeconf .deb package here [http://packages.ubuntu.com/karmic/pppoeconf]("http://packages.ubuntu.com/karmic/pppoeconf")

Let hope this works :-)

---

### Post by Viva on 2009-10-31
I just ran **sudo ppoeconf**. It takes you through a wizard that asks for your dsl username and password and a few more questions I couldn't understand. I don't know how safe and secure it is though. I guess it is only a temporary solution until network manager is patched.

---

### Post by nialui on 2009-10-31
in other thread, user k3lt01 mention this:

> 
Try [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and see if it helps. If it does let us know, I use it anytime I have this problem with a new release.

I tried, and it worked like charm!

---

### Post by Viva on 2009-10-31
ppoeconf is already available in your default install, you don't need to download any package

---

### Post by Nightstrike2009 on 2009-10-31
Found Networkmanager .deb package at:
[http://packages.ubuntu.com/karmic/network-manager]("http://packages.ubuntu.com/karmic/network-manager")

think this is the one in karmic though lets hope updated package it posted soon

---

### Post by Viva on 2009-11-01
This is fixed in the [daily builds of network manager]("https://edge.launchpad.net/~network-manager/+archive/trunk/"). The "insufficient privileges" bug is still there, but you can temporarily fix it by making sure the connection is NOT available for all users. You can not connect if you check the "Available to all users" box.

---

