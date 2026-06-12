---
title: "Hostnames only seem to work with ping"
date: 2015-11-13
forum: Networking &amp; Wireless
---

### Post by agough on 2015-11-13
Evening all, I have weird computer problems..... :(

OS: Fully updated Lubuntu 14.04

This started off with a broken wifi printer...

So the rub of the matter is, NetBios hostnames don't work on my Lubuntu machine - no wifi printer using its hostname, can't access a webserver on a LAN machine using its hostname. nmap won't give me any hostnames. IP addresses for all of the above work fine. Samba is installed.

A bizarre exception is ping - ping works fine with NetBios names. E.g. "ping win8laptop" connects fine.

I've added "wins" to my nsswitch.conf, as I think I saw somewhere that was needed.

:confused:  I'm not really quite sure what to try nowThanks for your input! agough

---

### Post by TheFu on 2015-11-13
Did you setup a WINS server on your network? If not, that setting won't do anything.

Normally, Linux uses IP to communicate. Generally, that means using DNS and/or /etc/hosts files.
Windows has included a native IP stack since v3.11, so the equiv of the /etc/hosts exists there.

Some routers have support for DNS too. dd-wrt does. Setting it up isn't as easy as it could be.

---

### Post by agough on 2015-11-14
> **TheFu said:**
> Did you setup a WINS server on your network? If not, that setting won't do anything.

No, I didn't set up a WINS server. I think my router does have a custom DNS settings page, but unfortunately I can't access it at the moment.

---

