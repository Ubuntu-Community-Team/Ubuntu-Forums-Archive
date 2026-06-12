---
title: "Screen Resolution over LAN using Remmina"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by Kansasguy on 2015-11-11
In short, resolution problems using vnc/Remmina over my home LAN

It started with me trying to make a Raspberry Pi headless.

Most of my computers are dual booted Windows/Linux.  I have successfully linked them (Linux side) with tightvncserver, xrdp, and Remmina.  The problem is with the resolution of some of the connections. I thought it was just an issue of choosing the right resolution in the Remmina connection screen, but then found I could make the connection the right resolution (but not the right size) by changing the "color depth" from "256 colors (8 bpp)" to "hi color (16 bpp)"

back when I was starting with the Raspbery Pi there was a command like:

         vncserver :0 -geometry 1920x1080 -depth 24

but I can't figure out how that came into play

will try to attach some photos/screenshots to help explain


Next will be connecting the windoze side, Thanks in advance

---

### Post by obtim on 2016-01-04
I have the same problem. The problem is in the program. On the other VNC-clients there is no such problem.

---

