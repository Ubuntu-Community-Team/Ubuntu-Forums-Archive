---
title: "quick synergy start up"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by chozoboy on 2007-10-25
is there a way to have Quick Synergy start up at login and start using a Synergy Server right away? I run an Ubuntu screen right next to an iMac (which is the server). i want to just start up my Ubuntu box, have it log in, and connect to my iMac automatically.

---

### Post by staticsage on 2007-10-26
I've never used Quick Synergy, but I used to have Synergy connect at startup. I ran synergyc at startup and pointed it to my configuration file.

sudo apt-get install synergy

Then follow these instructions to create your configuration file and set autostart: [http://synergy2.sourceforge.net/running.html](http://synergy2.sourceforge.net/running.html)

You can have the program run at startup by adding it to your sessions autostart: System | Preferences | Session | Autostart

If you need any help configuring this, please post back.

---

### Post by chozoboy on 2007-10-26
that's exactly what i needed. it worked like a charm.

i'm still a relative linux noob, so i was unsure of how to command line synergy.

thanks

---

