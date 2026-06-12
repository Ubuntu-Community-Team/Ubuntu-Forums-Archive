---
title: "New to Unix"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by quista345 on 2010-04-12
[COLOR=#231F20][FONT=Arial]What would the permission section of an ls -l listing for filex look like after setting the following permissions

[/FONT][/COLOR]  [COLOR=#231F20][FONT=Arial]chmod 764 filex[/FONT][/COLOR]

 [COLOR=#231F20][FONT=Arial]chmod 666 filex[/FONT][/COLOR]

---

### Post by r_s on 2010-04-12
rwx-rw_-r__
rw_-rw_-rw_
in the order user ,group, others

r for read, w for write, x for execute
their values are 4,2,1

---

### Post by nothingspecial on 2010-04-12
> **r_s said:**
> rwx-rw_-r__
rw_-rw_-rw_
in the order user ,group, others

r for read, w for write, x for execute
their values are 4,2,1

4+2    = 6 = read write
4+2+1  = 7 = read write execute
4+1    = 5 = read execute

see [[COLOR="Red"]here[/COLOR]]("http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php")

---

### Post by quista345 on 2010-04-12
[B][COLOR=#231F20][FONT=Arial]I am trying to rewrite these commands using sort as a filter but I should end up with a single command line for each.
[/FONT][/COLOR][/B]
**[COLOR=#231F20][FONT=Arial]$ [/FONT][/COLOR]**[COLOR=#231F20][FONT=Arial]sort roster > temp [/FONT][/COLOR]
  **[COLOR=#231F20][FONT=Arial]$ [/FONT][/COLOR]**[COLOR=#231F20][FONT=Arial]lp temp[/FONT][/COLOR]
  **[COLOR=#231F20][FONT=Arial]$ [/FONT][/COLOR]**[COLOR=#231F20][FONT=Arial]rm temp[/FONT][/COLOR][COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by Chronon on 2010-04-12
By the way, Ubuntu is a GNU/Linux operating system.  It isn't Unix.

---

### Post by srs5694 on 2010-04-12
Quista345, [please read this.](http://www.catb.org/~esr/faqs/smart-questions.html)

---

