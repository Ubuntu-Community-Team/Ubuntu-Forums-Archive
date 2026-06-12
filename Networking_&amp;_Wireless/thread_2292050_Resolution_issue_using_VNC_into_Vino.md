---
title: "Resolution issue using VNC into Vino"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by ryan179 on 2015-08-24
Hi everyone, 

I have recently got Vino working on my Linux server (Ubuntu Gnome), such that I can now successfully connect to my Linux server over LAN from my Mac (OSX) using either Chicken of the VNC or Real VNC.  

However, while the connection is successful, the resolution is not.  **I am unable to see the whole Linux desktop, and this is not something that I can adjust or control from the VNC client. **

Specifically:  When I log into my Linux machine from my Mac using VNC Viewer, while the "resolution" appears OK, about 80% of the content of the remote desktop is chopped off. You can see what I'm referring to in the screenshot link below. Note - there isn't a way to adjust this from within VNC Viewer application (ie, adjusting the size only adjusts the size of the whole VNC window and scales the content). Further to this (and I'm not sure if it's related), when I plug my server into my old TV screen via HDMI, I have a similar issue where about 50% of the screen is cut off. However, if I open Kodi (the primary use of my server through my TV), the screen is 100% OK. I thought this was just an issue with my old TV as there are no issues if I try my friend's newer TV screen, but since the issue seems similar to what happens when I connect via VNC I thought I'd share. Screenshot of what happens when I make the connection using a VNC viewer: [http://postimg.org/image/aqd4vok5x/](http://postimg.org/image/aqd4vok5x/)

Is this a limitation of Vino, or is there something I can try?  Please note - I'm new to Linux so any explanation should be beginner-proof!

Thanks!
Ryan

---

### Post by steeldriver on 2015-08-25
I wonder if it's something particular to the headless configuration? 

Actually I'm not sure what "headless" means in this context since vino-server is clearly relaying something on display :0

What are the outputs of 

```

xrandr -d :0 -q

sudo lshw -C display

```

---

