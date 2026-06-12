---
title: "Accessing an Anonymous Samba Share from a Mac"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by Tsuki on 2008-02-09
Apologies if this is a Mac issue and I'm posting to entirely the wrong place, but Mac forums are a weird alien world to me =p

I've got an Ubuntu 7.10 machine running Samba with an anonymous share.  Other Linux machines on the network pick it up fine, and connect to it without asking for a usename or password.  For example, here's a line from a client's fstab that has it working fine:

```
//server/stuff /media/stuff smbfs guest,uid=1000,umask=0000	0	0
```

However, my girlfriend's new Macbook won't connect - it picks up the machine on the network, but claims the server "does not allow Guest access" when we try that, and says Invalid Username/Password if one attempts to log in with one of the user accounts on server.

The relevant bit of server's smb.conf is:

```
[stuff]
path = /media/stuff
available = yes
browsable = yes
public = yes
writable = yes
```

Is there something special I need to do to Samba to make it Mac-friendly, or is something weird going on at the Mac end?

---

### Post by swerdna on 2008-02-10
I saw a similar situation where the mac reacted to a corrupt Samba user database with that message. Maybe lots of things will cause that message. But what do you get in a terminal when you query the Samba user database with this:
**sudo pbdedit -L**

Swerdna

---

