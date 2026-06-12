---
title: "Can I set a preferred wireless network?"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by egruber on 2008-04-29
When I boot up Hardy, it connects to my next-door neighbor's wireless even though my signal shows as stronger.  Is there any way to specify that it should connect to mine first?

---

### Post by skiss on 2008-10-25
I had the same problem. I found a work around ([http://brainstorm.ubuntu.com/idea/497/](http://brainstorm.ubuntu.com/idea/497/)).
Basically:
Run gconf-editor: ALT+F2 "**gconf-editor**"
Go to **system -> networking -> wireless -> networks ->** <select the one, that you want to get rid of>
Right click on each of the property names (bssids, essids, etc.) and selct "**Unset Key**" for each.
Done.

--
Sandor

---

