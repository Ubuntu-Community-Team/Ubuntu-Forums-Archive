---
title: "hotspot shield ubuntu"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by WhatAreHackers on 2011-02-11
Hello,I followed tips from this site exactly.... [http://ubuntuforums.org/showthread.php?t=1655797](http://ubuntuforums.org/showthread.php?t=1655797)  ...So yeah... I wanted to change my Ip... did... didn't like the fact I did not have a dns... found google dns, followed their steps... checked out if my own ip changed through a site called Whatismyip.com... and it so happens it was my original ip... removed the google dns thing... killed vpnc... followed the same guide as mentioned in the beginning [http://ubuntuforums.org/showthread.php?t=1655797](http://ubuntuforums.org/showthread.php?t=1655797) ... and i get this message. vpnc-connect: Error binding to source port. Try '--local-port 0'Failed to bind to 0.0.0.0:500: Address already in use... did I mess up my Ubuntu?? What do i do now?   Tried to summarize the best that i could.
 Edit: I already know that adding --local-port 0 to sudo vpnc would make it work, but what I want to know is how to fix this

---

### Post by uRock on 2011-02-11
If you are trying to hide your IP, then why not use a proxy? I don't understand why you would be trying to change your own IP, when that is the job of your ISP.

---

### Post by WhatAreHackers on 2011-02-11
> **uRock said:**
> If you are trying to hide your IP, then why not use a proxy? I don't understand why you would be trying to change your own IP, when that is the job of your ISP.
 
 Oh lol... i reread my first post... sorry I like to have a little privacy... and I can't seem to find any proxies =( ... Tor nodes can't really be trusted, because anyone can be an exit Node meaning multiple people(I go online alot) can read what my browsing habits are -.-... jondofox I got it working but I didn't really like it that much... my ip is dynamic, i can't change it -.- even if it does change, it'd only change by like the last few numbers or something.  The point is, i'm not using a proxy... and I can't change it even if i wanted to, it's dynamic not static.  Meaning I can't turn off my modem for a few minutes and get a new ip.
 Edit: Did I mess up my Ubuntu... vpnc-connect: Error binding to source port. Try '--local-port 0'Failed to bind to 0.0.0.0:500: Address already in use... it wasn't like this before

---

### Post by uRock on 2011-02-11
This link may be helpful for setting up Hotspot Shield. [http://markusthielmann.com/blog/hotspot_shield_ubuntu](http://markusthielmann.com/blog/hotspot_shield_ubuntu)

---

### Post by WhatAreHackers on 2011-02-11
> **uRock said:**
> This link may be helpful for setting up Hotspot Shield. [http://markusthielmann.com/blog/hotspot_shield_ubuntu](http://markusthielmann.com/blog/hotspot_shield_ubuntu)
 
I already know how to set up Hotspot Shield, got it working even... All I am asking is why am I getting the error, that I didn't get before... I hope this clears any confusion.
 Edit: I already looked at this article... the comments were... tldr

---

