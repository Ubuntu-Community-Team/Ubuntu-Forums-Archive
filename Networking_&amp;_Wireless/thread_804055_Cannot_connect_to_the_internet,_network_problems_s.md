---
title: "Cannot connect to the internet, network problems striker extreme."
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by TerabyteUK on 2008-05-22
Hi, I cannot connect to the internet on my new 8.04 installation.

It should be noted, this is a dual boot, with vista - which connects to the internet fine.
It has replaced a 7.04 installation which -also- worked fine, with no additional configuration required.

Situation:
ADSL bethere broadband connection
Connected to an adsl 4 way router whos IP is 192.168.1.254
I have always (and still do) connect using DHCP
The network cable is plugged in.
I have been paying my internet bills.
All other silly/sarcastic assumptions apply, as the connection does work perfectly on vista.

Computer spec:
Striker Extreme motherboard (nvidia nforce 6).
2 LAN connections (one of which is pluged in, assumed to be eth0).

Geforce 8800 GTS (does this matter? I should hope not but it wouldn't surprise me).

I have tried DHCP, I have tried Static IP.
In network settings, I have checked 1 connection, then the other, then both, tried DHCP and static with each combination, with the same addresses, with different addresses.
I have tried adding 192.168.1.254 to the DNS list, which seems to do nothing (and now removed it).

Never been able to ping the router, or get online with firefox.

Any help much appreciated as I ponder why I let my idle curiosity for 8.04 get the better of me.:confused:

---

### Post by tarutaruomen on 2008-05-22
I have been experiencing exactly the same thing.  I also have a striker extreme motherboard and a linksys w54 card.  No matter what I did.  I couldn't connect to ubuntu wirelessly.  Gave up and reinstalled windows on my desktop.  8.04 works great on my laptop

---

### Post by TerabyteUK on 2008-05-26
Ok so I've installed 8.04 again, from the Alternative CD.
And then again in 7.04 alternative CD.

Well, it's all about 8.04, during the installation:

7.04 No problem identifies my 2 LAN sockets, and is able to configure DHCP correctly, within a few seconds.

8.04, well... doesn't, and there's nothing you can do about it (so it seems) after the installation. You can either get by with "don't configure right now" or don't.

So I'm going back to 7.04. If any developers for ubuntu want to contact me to try out experiments or patches, feel free to do so. I would actually like to run 8.04

In short, Networking does not work in ubuntu 8.04 with Striker Extreme motherboards (nForce;680sli)

Shame

---

### Post by OnsoSan on 2008-09-21
answering the same subject on another thread
([http://ubuntuforums.org/showthread.php?p=5828297](http://ubuntuforums.org/showthread.php?p=5828297))
worked for me

---

