---
title: "Averatec Built-in Wireless Problem"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by cpil on 2007-06-09
Ubuntu Feisty works well so far on my Averatec 3150p laptop, with the exception that I can't connect to my wireless router. I've looked around a bit to see if others have had the same problem, and I ended up editing the xorg.conf file with Option "DisableIRQ". I don't know if that was the right thing to do, but it didn't help. I'm new to the Ubuntu/Linux world and would really like to get this working. What's the next step?

---

### Post by ubunxpm on 2007-06-10
I'm using an Averatec 3250 with a wireless card from MSI which has wireless chip from Ralink. I believe yours has a wireless chip from broadcom(correct me if I'm wrong) I have edited the menu.lst you have edited xorg.conf to solve the problem (both are different ways to solve the same irq conflict problem) so "yes" that's fine. Now just give a little more information about what happens when you try to connect.

---

