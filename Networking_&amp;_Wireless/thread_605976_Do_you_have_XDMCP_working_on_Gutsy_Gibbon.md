---
title: "Do you have XDMCP working on Gutsy Gibbon?"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by mts-fi on 2007-11-07
I can't get my XDMCP working... and I'm not the only who can't.  

I know this is reported bug: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193) (importance low?)

I'm curious to see how many of you have XDMCP working on Gutsy Gibbon.

---

### Post by robsyd on 2007-11-08
The bug importance is very high for me and for a lot of people I know.

Never forget that the separation between the GUI and the kernel is one of the most important difference between Linux and Windows.

This bug is very relevant mainly In the education environment, where often many clients refers to one server.

I guess the education environment should be considered a strategical target by developers.

---

### Post by maximwirt on 2007-11-09
It's been working for me at last. I don't know what exactly made it working, but I'm connected via XDMCP to my server host actually.

on the server: replaced remote login style from "as local" to "simple"
on the client: when login window appears I press ctrl+alt+f1, login to terminal, execute following:
sudo X :1 -query xxx.xxx.xxx.xxx

Xnest works as well.

---

### Post by mrtisoy on 2007-11-23
maximwirt,

Thank you, your work around worked for me.

mrtisoy

---

### Post by Loranga on 2007-12-03
> **maximwirt said:**
> 

on the server: replaced remote login style from "as local" to "simple"


This made it work for me too!

---

### Post by Samizdata on 2007-12-03
> **Loranga said:**
> This made it work for me too!

The only issue I had was editing gdm.conf to enable remote login.

---

### Post by JoseArmandoJeronymo on 2007-12-14
Regarding XDMCP, a patch was created and tested: please see [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193) for details.

---

