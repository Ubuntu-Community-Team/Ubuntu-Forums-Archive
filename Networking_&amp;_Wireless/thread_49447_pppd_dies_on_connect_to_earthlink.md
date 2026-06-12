---
title: "pppd dies on connect to earthlink"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by geocritter on 2005-07-16
Good morning all,

I need some help.  I'm so close yet so far away.  Finally got my modem to work.  I am running KPPP (yes, I've got both ubuntu with gnome and installed KDE, so I have both ubuntu and kubuntu! I love it!), and cannot for the life of me get it to talk to earthlink.  I'm at my wits end with it.

It dials in and gets the carrier, but when it starts up pppd, it times out and dies.  I've tried every option I can think of; made a resolv.conf, edited pppd to remove auth and lock, checked permissions, set it all for PAP authentication.  I don't know what else to do.

Does anyone with earthlink experience care to help me out?  Maybe send me your pppd script or something?  I've also run wvdial with the exact same problem.

Thanks so much in advance,
Dan

---

### Post by geocritter on 2005-07-18
Spent most of yesterday afternoon on it.  It's firing up pppd, but then gets to something like LCP request timed out or something like that.  A little research through google seems to imply that it's making the connection with Earthlink, then getting confused (i.e., the server is waiting for something or the computer is waiting on something, but they're both confused with it, so the connection dies).  Any thoughts?  I think it's a matter of getting the options in /etc/ppp/options correct, but I don't know which ones.  Please, I need to get this thing working. Any ideas?

Thanks so much in advance,
Dan

---

