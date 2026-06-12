---
title: "I made a goof"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by neubert500 on 2007-11-27
When I upgraded to 7.10 I was tired and messed up my network configuration to my wireless on my Presario F500. When I boot into Ubuntu, i must go to my manual network configuration and input my correct information. How do I get rid of the incorrect information and save the correct info? Every way I have tried has left the old information as defaut.
thanks for any help for correcting a problem I caused.

---

### Post by x64Jimbo on 2007-11-28
You'll want to fire up GNOME's settings editor called "gconf-editor"
Go to System -> Networking -> Wireless -> Networks.
Delete the keys that are wrong by right clicking them and selecting "Unset Key"
If you want a simple way to delete all the settings for a network all at once, you can use a neat little perl script that I whipped up a few months back. Check out [this thread.]("http://ubuntuforums.org/showthread.php?t=385051")

---

