---
title: "locked folder on desktop."
date: 2008-12-26
forum: New to Ubuntu
---

### Post by asaluth on 2008-12-26
i downloaded and installed java (my first "major task w/terminal). now I have a locked folder on my desktop (jre6.0...?) that i'd like moved to maybe the systems folder. i don't think i should delete it. im only 9yrs old so can it be easy?:confused:

---

### Post by taurus on 2008-12-26
Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Now, you should be able to move that directory to wherever you want since you have a root privilege.

---

### Post by waspbr on 2008-12-26
Í am not sure exactly what you have done with respect to installing java, but if you wanna move/copy/cut/paste/delete a locked folder you neet to have root (administrator priviledges).

The easiest way I can think of, is to open nautilus as an admin. 

press ATL+F2 then type

```
gksu nautilus
```

input your password and a nautilus window should appear. There, navigate to /home/YourUserName/Desktop (don't bother with the Bookmarks).

then copy the folder to your home directory (I guess), not your system. I don't know what kind of files you have in that folder, you need to reinstall java, can't really say...

anyway, remember to close that nautilus window, any changes you make in that nautilus window are going to be (somewhat) permanent.

gl

---

### Post by asaluth on 2008-12-26
YOWSERS!!  ur my new super hero... captain taurus! ok, maybe i'll keep ths os for a while. it's def. fun!:P

---

