---
title: "How do I run vbeinfo to display by page?"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by bwallum on 2010-06-29
Hi

I'm trying to work out how my Plymouth screen displays jumbled pixels. In GRUB2 I run vbeinfo but the output pages away so that I only see the end of the report.

Do I need to pipe the command through something so that I can show the whole of the report or are there some key strokes that enable me to navigate the whole report?

---

### Post by sisco311 on 2010-06-29
> **bwallum said:**
> 

Do I need to pipe the command through something so that I can show the whole of the report or are there some key strokes that enable me to navigate the whole report?

Yep:
```
vbeinfo | less
```
Use the arrow keys to scroll the page & q to quit.

---

### Post by bwallum on 2010-06-30
Many thanks, works for me. hole in one!

---

