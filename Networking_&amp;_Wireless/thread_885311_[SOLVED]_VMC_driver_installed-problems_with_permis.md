---
title: "[SOLVED] VMC driver installed-problems with permissions when opening"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by sunlover on 2008-08-10
I have Ubuntu 7.10 dual booted with Windows XP on my laptop and am accessing the Net thru Windows XP using an OPTION GX 0202 wireless card.
After some searching of various forums I have d/loaded and installed vodaphone-mobile-connect-card- driver-for-Linux _1.99.17_i386.deb that I believe will work with my telco and card.

When I try to open same the a window below is displayed with **twistd** in the top bar and text as  follows:
[B]Permissions problems:
Vodaphone Mobile Connect Card driver for Linux needs the following files and dirs with some specific permissions in order to work properly:/etc/ppp/pap-secrets should have 0660 mode,found 0600/etc/ppp/chap-secrets s/h 0660 mode,found 0600/etc/ppp/peers s/be readable and writable by group dip[/B]
Can I address these with terminal commands and as a new player an idea of what code to use would be great.

Any further help or suggestions much appreciated-Bruce

---

### Post by cariboo on 2008-08-10
It is pretty nice  that it sets everything out so nicely:

> /etc/ppp/pap-secrets should have 0660 mode,found 0600

```
sudo chmod 660 /etc/ppp/pap-secrets
```

> /etc/ppp/chap-secrets s/h 0660 mode,found 0600

```
sudo chmod 660 /etc/ppp/chap-secrets 
```

> /etc/ppp/peers s/be readable and writable by group dip

```
sudo chown <username>.dip /etc/ppp/peers
```

Make sure your are a member of the dip group. To do this go to System-->Administration-->Users and Groups, and add yourself to the dip group.

One final thing:

```
sudo chmod 755 /etc/ppp/peers
```

Jim

---

