---
title: "problem with chatsniff"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by franestepona on 2007-01-10
I just installed chatsniff to monitor instant messages in my network and when i run it i get:

```
fran@fransmachine:~$ sudo chatsniff

(chatsniff:13648): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Preferences file doesn't exist or couldn't be read!
Could not read preferences file!
/bin/sh: tethereal: not found
fran@fransmachine:~$ 

```

I get an error complaining about tethereal, but is already installed.

Anyone know how to fix this? thanks.

---

### Post by franestepona on 2007-01-10
I've already solved, I posted a bug and the solution at [http://sourceforge.net/tracker/index.php?func=detail&aid=1632508&group_id=142800&atid=753726](http://sourceforge.net/tracker/index.php?func=detail&aid=1632508&group_id=142800&atid=753726)

---

### Post by moonliter on 2007-06-16
Thanks It works!!!

---

