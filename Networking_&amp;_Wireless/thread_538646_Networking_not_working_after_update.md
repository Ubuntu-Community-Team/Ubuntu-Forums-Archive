---
title: "Networking not working after update"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by NaturalSelector on 2007-08-30
Just started my linux journey a few weeks ago, so I'm a little new to this. Feisty has been working fine with no problems until I installed one of the automatic software updates last night. The update said something about TCP, but I didn't pay too much attention because I trust the Ubuntu staff over my own limited knowledge.

My wireless card has continued operating flawlessly, but when I came into work today I cannot seem to get an IP address on my wired nic. For unknown reasons, I am able to get an IP address using Windows through VMWare (bridged through the same wired nic).

I am using a Dell Latitude D800 with (and without) the dock. Any ideas on how to roll back the update, figure out what exactly it was (logged somewhere?), or troubleshoot the problem I have?

---

### Post by noob12 on 2007-08-30
Most likely you saw the TCP wrappers update recently (libwrap).  You can look at the log in /var/log/dpkg.log for recent updates.  

I don't think that is your problem, however. So you'll probably need to engage in more diagnosis.

Posting these would help:

```

lspci -nn

sudo lshw -C network

ifconfig -a

grep dhclient /var/log/syslog | tail -50

```

---

