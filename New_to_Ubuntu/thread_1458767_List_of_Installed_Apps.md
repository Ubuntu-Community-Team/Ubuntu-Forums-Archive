---
title: "List of Installed Apps"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by sturdy on 2010-04-20
Hi all,

Is there a way to get a list or file of installed (less libs, etc.) applications. Sure would make it easier for a clean install of 10.04. Thanks.

---

### Post by jaco223 on 2010-04-20
> **sturdy said:**
> Hi all,

Is there a way to get a list or file of installed (less libs, etc.) applications. Sure would make it easier for a clean install of 10.04. Thanks.

Try this :

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

I guess this is what you meant?

Hope that helps.


Jaco

---

### Post by sturdy on 2010-04-20
Thanks Jaco, that's exactly it. I thought I had looked everywhere.

---

### Post by Drenriza on 2010-04-20
try ```
[FONT=Times New Roman][SIZE=3]apt-cache showpkg *[/SIZE][/FONT]|less
```
and see if that gives you the information your looking for
 
EDIT: readed the link, nice.

---

### Post by sisco311 on 2010-04-20
Synaptic  Package  Manager -> File menu -> Save Markings As... -> Save full state

[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]-> Read Markings...[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jaco223 on 2010-04-20
> **sturdy said:**
> Thanks Jaco, that's exactly it. I thought I had looked everywhere.

Glad you found your list!

Jaco

---

### Post by jim Kane on 2010-04-20
> **sisco311 said:**
> Synaptic  Package  Manager -> File menu -> Save Markings As... -> Save full state
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]-> Read Markings...[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

                                       thats interesting is there any way of saving _only_ the user installed apps, 
    [LEFT]for future clean install of 10.04 



Jk
[/LEFT]

---

### Post by klytu on 2010-04-21
> **jim Kane said:**
> thats interesting is there any way of saving _only_ the user installed apps, 
    [LEFT]for future clean install of 10.04 



Jk
[/LEFT]

I've attached a script (written by another forum member whose name I've forgotten and whose original thread I can't seem to locate ...) that could easily be modified to do this.

---

### Post by jim Kane on 2010-04-22
> **klytu said:**
> I've attached a script (written by another forum member whose name I've forgotten and whose original thread I can't seem to locate ...) that could easily be modified to do this.

Ok thanks for that, i will give it a go

Jk

---

