---
title: "Network Manager"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Boule on 2007-04-29
So Network Manager keeps trying to connect to the neighbor's network before mine... How can I get it to stop ? Isn't there a config file containing all the networks it tries to connect to ?

---

### Post by kelbizzle on 2007-04-29
I know it stores the information in Gconf.
```
/system/networking/wireless/networks

```
 I don't know how to get rid of it.

---

### Post by kelbizzle on 2007-04-29
Right click on the values on the left. Then choose the option to unset them. Thats how you get rid of it.

---

### Post by Boule on 2007-04-29
What's the path ? I'm using Edgy, I don't have /system...
And when u said right-click on the values on the left, what values are u talking about ?

Thx for ur help

---

### Post by TrinitronX on 2007-04-29
It's not a path, it's in gconf... basically a configuration tool used in gnome that works much like the windows registry.  Find it under Applications>System Tools>Configuration editor.  Or, just run "gconf-editor" from a terminal.  (of course, add sudo or gksu to the front if it needs root)

---

### Post by Boule on 2007-04-29
Oh ok. I found it, I unset all the keys and the folder disappeared ! Thanks.

---

