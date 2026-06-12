---
title: "How to fix source code"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by xjsquarred on 2009-07-15
Hi, I am new to Ubuntu and linux.  I was trying to install "ubuntu tweak."  I messed up the source code.  I thought i was supposed to delete the comments about this and that being unsupported and such.  Now I am unable to install new software and the auto update does not work.  Can I repair the source code or do I need to do a fresh install? I am away for a couple weeks and I don't have realiable strong internet so it would be inconvienent to dl UNR again.  Any help would be great, thanks.

---

### Post by anim on 2009-07-15
Did you build it from source? Can you post what source you modified? Sorry I'm just a bit confused at the moment. A good way of putting it is:

1. What you did.
2. What you expected to happen
3. What actually happened.

Thanks! Hopefully we can help.

---

### Post by 3rdalbum on 2009-07-16
In future, don't manually edit your "/etc/apt/sources.list" as a lot of new users make mistakes and then find that their package management system stops working because it can't understand the modifications their made to the file.

Instead, use the Software Sources program to add and remove repositories.

When you try to install software, the system will tell you the line number in the sources.list that it can't understand. Go to that line and put a # at the start of it; that will tell the package manager not to read that line.

EDIT: What you modified was not a program's source code, but just a list of repositories.

---

