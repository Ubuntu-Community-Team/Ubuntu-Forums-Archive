---
title: "Connection issue with Firefox"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by lucid on 2009-12-16
I'm unable to add firefox addons; the connection just times out. I've attempted to install Ubuntuzilla but I encounter the same issue as the connection times out during the installation. This has only occurred since upgrading to Karmic. Any ideas?

---

### Post by llawwehttam on 2009-12-16
have you got proxy settings? is so the upgrade might have messed them up. Please be more specific. Where is this machine? for instance if its yours at home then i might have a different answer to if you were using it at work.

---

### Post by lucid on 2009-12-31
I use a dell inspiron 1520 laptop at home with a d-link modem/router dsl-540t. The only change I made was to install the latest ubuntu (last iteration worked just fine).

just upgraded the latest firefox and the problem still exists. Connection just hangs when trying to install an addon.

---

### Post by rustutzman on 2009-12-31
Sounds like a problem with your wireless card driver in 9.10. I know there are lots of threads about this. You might try a search of the group with your card type.

Russ

---

### Post by tom.swartz07 on 2010-01-01
> **rustutzman said:**
> Sounds like a problem with your wireless card driver in 9.10. I know there are lots of threads about this. You might try a search of the group with your card type.

Russ

Im not so sure.... I have a Dell 1521 and the wifi cards work perfectly from the install.

You say that you could navigate to the add on page? In other words, Is your internet connection working for other web sites?

Perhaps its just a problem with the server that hosts the Ubuntuzilla files?

---

### Post by tacantara on 2010-01-01
I had a similar problem when I upgraded to 9.10.  I had to modify some files that affect DNS.  Not only did I have a problem with downloading FF add-ons, I had trouble accessing several websites.  Here's a recap of the fixes:

1.  Using the terminal, execute the following command:

```
sudo gedit /etc/dhcp3/dhclient.conf
```

When the file is open, add the following line, verbatim, at the beginning of the file (after the comment lines):

> prepend domain-name-servers 208.67.222.222,208.67.220.220;

2.  Again, in the terminal, execute the following command:

```
sudo gedit /etc/nsswitch.conf
```

and in the document, change this line

> hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

to read > hosts: files dns

This fix has worked quite well for me.  I hope it does for you.

---

