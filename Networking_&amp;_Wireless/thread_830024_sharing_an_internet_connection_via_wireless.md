---
title: "sharing an internet connection via wireless"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by onemanclapping on 2008-06-15
hi,

I have 2 computers, one is a desktop, the other a laptop (with wifi). Both have Ubuntu 8.04 (hardy) on them.

The desktop one has a USB wireless stick (D-link DWL-G122) compatible with Ubuntu and is connected to the internet via wired newtork (a ADSL modem connected to a router, connected to the PC by a Ethernet cable).

I want to share my desktop internet connection via wireless (ad-hoc) so I can connect my laptop to it. With windows this is really easy to do but I can't seem to do it with Ubuntu.

Can someone tell me how to?

Thanks in advance!

Andre

---

### Post by issih on 2008-06-15
One hopefully simple way to achieve this (without resorting to lots of editing of config files) is to install firestarter. In a terminal, run:

```
sudo apt-get install firestater
```

Enter your login passeord when prompted.

Once it is installed, start it from System->Administration->Firestarter

When it is first run it will guide you through set up, the package is really a firewall configuration tool, but it offers ics as one of its feature. Just use the wizard :)

Hope that helps

---

### Post by superprash2003 on 2008-06-15
if firestarter doesnt work then [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

