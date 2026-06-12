---
title: "Newbie Apache2 won't find localhost"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2007-11-21
I got a weird problem...I just installed Ubuntu Server 6.06 and Apache2.
I can view from a client station, the server on local IP set aside for the server, but I cannot view it from localhost or 127.0.0.1 .

Is this a firewall or an Apache2 config problem?  My /etc/hosts shows both local IP, localhosts, and my domain.

 I once had a running website from a Ubuntu 6.06 Desktop, but had to redo machine to be dual boot.  I thought I saved config files but didn't and can't find my notes for Apache2 setup.

Here's the physical setup:

INTERNET
   |
DSL MODEM/ROUTER-----(wireless)------>WIN2k & WINXP
   |
(wired)
   |
UBUNTU SERVER

Thanks - and sorry to repost (need help fast!)****

---

### Post by Hyssar on 2007-11-22
test the state of the server

```
ps aux
```

---

### Post by flyinggreg on 2007-11-22
> **Hyssar said:**
> test the state of the server

```
ps aux
```

I am pretty new to setting up the server....is there anything in particular I should look for?

I see apache started. postfix started,courier, samba, etc.

I am pretty sure I have a simply mess up in one of the apache config files....I just can't seem to find it.

---

