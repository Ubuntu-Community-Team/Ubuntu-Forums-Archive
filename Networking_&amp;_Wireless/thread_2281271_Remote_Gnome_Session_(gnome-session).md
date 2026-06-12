---
title: "Remote Gnome Session (gnome-session)"
date: 2015-06-05
forum: Networking &amp; Wireless
---

### Post by motobeats on 2015-06-05
I would like to tunnel a remote Gnome session from a KVM to my local machine (Mint 17). I tried two different ways that did not work.

1. Switch to tty and create another virtual terminal (xinit -- :1). From the new terminal ssh -X to the remote KVM. Then run gnome-session. This "works" but the resolution is way off and thus I can only see part of the screen (upper right). No mouse or keyboard control (EDIT: Wrong, just had the mouse on the undisplayed portion of the screen).
2. From a terminal in Mint, ssh -X and then run gnome-session. When this "works" is crashes cinnamon (Mint desktop). When it doesn't I get "Could not open X display"

Is there something I am missing?

---

