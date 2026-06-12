---
title: "auto eth0"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by mistypotato on 2009-05-31
Anyone got any clue as to why ubuntu insists on creating an auto eth0 network connection even though I have a manually configured network connection?

Can't seem to get networking to take on one of my machines.

Can't ping the router.  My guess is it seems to be a botched install and the default ubuntu firewall is wacked.

thx

---

### Post by coffeeaddict22 on 2009-05-31
Hi,
A bit more info would help.  If I had to guess, you've got a driver problem.  What's the output of ```
lspci
(just the network controller bit/s is fine)
lshw -C network
ifconfig
route -n
```
That's four separate commands, btw.

---

### Post by mistypotato on 2009-06-01
thx coffee.

After pounding my head against the pavement for abot 3.5 hours...it turned out that it just started working and I have no clue why.  Didnt really do anything.

The ethernet port lights were on, no firewalls blocking....just a ghost in the machine I guess.

Thx for the reply

---

### Post by coffeeaddict22 on 2009-06-01
I'm NOT a linux guru.  However, all the changes in networking have left a few hotspots.  I think there's a "workaround" in place in the networking protocols somewhere. What seems to happen is if you should have a connection set up but the driver isn't available the connection is taken by wmaster0, which is essentially a dummy connection that is used to link all the connections together (as far as I can make out).  It seems to turn up when the card is turned off in hardware/ loose connection, that sort of thing- and I'd guess that's what was happening.  However, on the "if it aint broke don't fix it" principle, go for it!

---

### Post by indrajit_1 on 2011-11-29
could someone please post a pointer to a correct auto eth0 for a home Computer?

---

### Post by coffeecat on 2011-11-29
@indrajit_1, please start your own support thread. You will need to give more information for people to help you.

Closed for necromancy.

---

