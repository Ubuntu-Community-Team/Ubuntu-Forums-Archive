---
title: "Can someone explain this?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by 4chan on 2010-10-06
I install kubuntu maverick and it feels like kubuntu are a little too heavy for my old computer and then i check system monitor to find out what's going on, i found xorg process consume almost 229 MB of memory. it's weird cause i don't see xorg process on Ubuntu.
can someone explain this? thanks

[ATTACH]171437[/ATTACH]
pic related

---

### Post by vaul on 2010-10-06
Xorg is a video system responsible for the drawing things you see on the screen, there won't be any good in disabling it.

If KDE (That's the desktop environment you see when you install Kubuntu) is too heavy for your machine you might want to try Gnome. 

Just type «Gnome» into the search box of the Ubuntu Software Center and then install before mentioned package. When it's done you'll have to select into what environment is to log in on the log in screen.

If you are logged in automatically, then you'll have to log out first.

If Gnome is too heavy for your machine too, you might want to try LXDE. Steps would be all the same.

And in the future, *please be more informative when naming your threads*. For example, a good name for this one would be «What is the function of Xorg process?» or «What is Xorg?».

---

### Post by philinux on 2010-10-06
> **4chan said:**
> I install kubuntu maverick and it feels like kubuntu are a little too heavy for my old computer and then i check system monitor to find out what's going on, i found xorg process consume almost 229 MB of memory. it's weird cause i don't see xorg process on Ubuntu.
can someone explain this? thanks

[ATTACH]171437[/ATTACH]
pic related

PC specs? I think that might be virtual mem not resident. Mine is at 61 MB. Gnome.

---

### Post by cascade9 on 2010-10-06
228.5 MB for xorg? o.O 

Xorg on my KDE 4.4.5 uses 34MB (+16MB shared).

---

### Post by 4chan on 2010-10-06
@vaul thanks, i will

@phil P4 2.4Ghz 1GB of RAM Nvidia 7200GS

@cascade yes

---

### Post by jtarin on 2010-10-06
Are you using special effects...like compiz? It will consume more memory through xorg.

---

### Post by 4chan on 2010-10-07
@jtarin yes i am, kwin is on but if i turn it off doesn't make any difference also why i don't see xorg process on ubuntu?

---

### Post by jtarin on 2010-10-07
In your terminal enter the command```
top
```  and get a true system picture. To quit top hit ```
q
```.

---

### Post by cascade9 on 2010-10-07
> **4chan said:**
> @jtarin yes i am, kwin is on but if i turn it off doesn't make any difference also why i don't see xorg process on ubuntu?

Kwin is on with my sytem as well. 

You will have an xorg process with ubuntu.

---

### Post by jtarin on 2010-10-07
No xorg....no screen....only terminal.

---

