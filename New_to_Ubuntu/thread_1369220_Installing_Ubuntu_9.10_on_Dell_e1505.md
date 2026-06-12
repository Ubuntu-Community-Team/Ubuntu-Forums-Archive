---
title: "Installing Ubuntu 9.10 on Dell e1505"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by davidvaldez on 2009-12-31
I just installed Ubuntu on my Dell e1505. I noticed that my USB ports and my WIFI is not working. I'm new to lynux, is there something I'm missing. Do I need a seperate package installation or is everything on the CD?

---

### Post by gordintoronto on 2009-12-31
Many wifi cards "just work" in Linux.  If that is the case, right-click on the network manager icon (top right, next to the volume control) and select "edit connections." Click on the Wireless tab, select "add" and enter your router's ID, encryption type and password.

If that isn't available on your installation, open an Accesories/Terminal session, type in the command:
lspci

and I think it will tell you your wifi card is a Broadcomm 4311.  This web page might be helpful:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The help begins about 60% of the way through the page, at "step 1."

When you say something "is not working," it is difficult to help you.  It is much better if you say, "I did such and such and expected the result to be xxx, but what happened was yyy."

In the terminal, the command
lsusb
should show your USB ports and what is attached to them.

You might also tell us how you installed Ubuntu: with the computer dedicated to Ubuntu, as a dual boot or under Wubi.

---

