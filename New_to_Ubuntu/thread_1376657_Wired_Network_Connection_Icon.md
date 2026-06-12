---
title: "Wired Network Connection Icon"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by ambeanerxcore on 2010-01-09
[IMG]http://i49.tinypic.com/4j2xll.png[/IMG]

How do I change the icon into a different one? I'm installing Mac4Lin and I can't figure out how to change it. Any help would be appreciated, thank you.

---

### Post by warfacegod on 2010-01-09
I don't know about Mac4lin but with my gnome changing the icon theme almost always changes that too.

---

### Post by akrivitz on 2010-06-25
I also would like to know how to do this. Mine seems to be stuck on a theme i don't use anymore. Switching themes does not change the network icons for me. (On 10.04 lucid)

---

### Post by linuxman94 on 2010-06-25
Found a fix.  Open a terminal and copy and paste the following line.

```
killall nm-applet
```

Then hit alt + f2 and type "nm-applet" (without the quotes).

---

### Post by UnaXdk on 2011-02-19
Thank you very much linuxman, that solved it for me, this solution finally made it possible for me to finish customizing my theme.

---

