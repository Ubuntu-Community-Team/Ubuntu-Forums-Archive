---
title: "setting bluetooth OFF by default?  UB 15.10"
date: 2015-12-11
forum: Networking &amp; Wireless
---

### Post by dave205 on 2015-12-11
running 15.10. every time I turn on my notebook though I see that bluetooth is ON.  I do use it occasionally but in the interest of battery savings, I'd like for it to be OFF by default and only turn on when I tell it to. When I turn it off, its off but after I reboot/shutdown then its back on. 

Is there a way to get the setting to stick? 

(I searched "bluetooth" and didnt see this addressed anywhere)

thanks for any pointers!!!!

---

### Post by dave205 on 2015-12-13
[FONT=arial]after asking some friends, I was told to edit the /etc/rc.local  file.  Apparently the file by itself does nothing but is a place to put runtime changes you want. 

Add "rfkill block bluetooth" (no quotes) before the "exit 0" at the end of the file. 



I hope this helps others[/FONT]

---

