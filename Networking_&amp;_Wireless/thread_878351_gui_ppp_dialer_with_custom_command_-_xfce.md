---
title: "gui ppp dialer with custom command - xfce"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by fedoraboy on 2008-08-02
I am a longtime unix user -- but I am using ubuntu (8.04) for the first time.

What I am trying to do is do dialup ppp with some form of GUI and be able to customize the connection with some form of command.  In fedora, I would just use modem-lights, which uses ifup to bring up the connection... so ifup has provisions to run a custom script.

I dont seem to find modemlights applet that works on xfce/ubuntu, so I have tried kppp and gnome-ppp.  Both of these work as far as dialing and bringing up the network, but I cant for the life of me figure out how to run a custom script in the process of bringing up the interface.

The reason for all this is that this is a system for grandma.  It needs to restart ntp on interface restart, as this is a bit of junk pc that has a wildly swinging clock.  It must be a gui or grandma wont be able to dial out.

Am I missing something obvious?

---

### Post by hubiedo on 2008-12-28
i am having a similar problem. i can get into the unix system ok but i dont seem to be able to configure kppp to use a different emulator for vt102 or even to change it. any suggestions or help appreciated.

---

