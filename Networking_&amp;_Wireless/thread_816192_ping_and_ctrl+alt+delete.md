---
title: "ping and ctrl+alt+delete"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by menschtx on 2008-06-02
Where do I find the function for the ubuntu alternative for ping and ctrl+alt+delete. Usually when trying to organize links in firefox 3, the hand+ will hang - locking up firefox and ubuntu. Any suggestions?

---

### Post by jetsam on 2008-06-07
The system monitor in Gnome (**system-->administration-->system monitor**) is similar to the windows task manager.  

I stick a launcher on my panel for it.  You can do this by just right clicking on the menu item, and selecting "add this item to panel."

For a ping alternative, try-- **ping**!

Open a terminal and type:
```
ping -c3 google.com
```

**-c3** says to ping 3 times.  It will ping infinitely otherwise (quit pinging with **ctrl-c** if you do this.) 

There's a gui ping available in **System-->Administration-->Network Tools-->Ping Tab**.  It's faster and more flexible to use the terminal, though.

---

### Post by menschtx on 2008-06-07
Thanks JetSam

---

