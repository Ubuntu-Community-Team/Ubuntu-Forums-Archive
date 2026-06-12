---
title: "uninstall/reinstall modem driver"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by lee292 on 2009-03-21
I've been trying to get my Dell Inspiron 8500 laptop's modem to work instead of having to pack around my old clunky USR Sportster.
I found a package that would work (slmodemd)that had alsa support, but it looks like I botched my installation.  I got it to dial out, but the second it connects, wvdial tells me "the ppp daemon has died.", with an 02 exit code.  This code says something about something in its config file being mutually exclusive.  A peek at a system log file showed pppd couldn't start its alsa protocol and exited.  Obviously, I've botched the installation somehow.  I'd like to flush everything that slmodemd has installed and start over.  How do I do that?

---

### Post by yeats on 2009-03-21
If you installed it with Synaptic, you would just select to "completely remove" it. Alternatively:

```
sudo apt-get purge slmodemd
```

in the terminal.

---

### Post by lee292 on 2009-03-21
Thanks!  Since it was installed in terminal, sudo apt-get purge should get rid of it and I can start over.  Will keep the group posted if it works.

---

### Post by lee292 on 2009-03-22
Tried your suggestion but got this in Terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package slmodemd

Suggestions?

---

### Post by lee292 on 2009-03-25
Found the answer I needed on [www.linmodems.org](www.linmodems.org).  My problems was with permissions.  I followed their suggestions for running wvdial as root, and it worksed.

---

