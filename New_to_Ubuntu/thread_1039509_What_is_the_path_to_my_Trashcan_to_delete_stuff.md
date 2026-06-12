---
title: "What is the path to my Trashcan to delete stuff?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-14
Hello,


There are two folders in my trashcan which I don't have the rights to delete. I now wanted to do it with the command line but I can't find the path to my trashcan. I read elsewhere that it is /home/username/.Trash but that doesn't seem to exist. Because my system is in Dutch I tried the Dutch version (prullenbak) but that doesn't work either.

Can anybody help me out here?

---

### Post by jerome1232 on 2009-01-14
Should be under

~/.local/share/Trash

btw ~/ = /home/currentuser/

---

### Post by newbee70 on 2009-01-14
> **kramer65 said:**
> Hello,


There are two folders in my trashcan which I don't have the rights to delete. I now wanted to do it with the command line but I can't find the path to my trashcan. I read elsewhere that it is /home/username/.Trash but that doesn't seem to exist. Because my system is in Dutch I tried the Dutch version (prullenbak) but that doesn't work either.

Can anybody help me out here?

```
 sudo nautilus 
```

then empty with the trashcan there. "where you have root rights temporarily.

---

### Post by Michael.Godawski on 2009-01-14
hi,

try this.

But please can somebody double check the rm command. 

I have always a bad feeling using sudo rm;)
```

sudo rm -rf ~/.local/share/Trash/*
```

here is a nice guide too:


[LIST]
[*][http://www.thegoss.com.au/modules/planet/view.article.php/406](http://www.thegoss.com.au/modules/planet/view.article.php/406)
[/LIST]

---

### Post by jerome1232 on 2009-01-14
> **newbee70 said:**
> ```
 sudo nautilus 
```

then empty with the trashcan there. "where you have root rights temporarily.

```
gksu nautilus
```

the reason being is sometimes with graphical apps and sudo, some of the apps config files in your ~/ end up being owned by root and cause problems when you try to run the app as a normal user. gksu avoids this.

--edit-- and yes that rm command is pointing at the correct path ;)

---

### Post by kramer65 on 2009-01-14
Grrrrrrrreat! Thanks a lot!

Btw. I did use sudo nautilus now. Is that a problem..?

---

### Post by newbee70 on 2009-01-14
> **jerome1232 said:**
> ```
gksu nautilus
```

the reason being is sometimes with graphical apps and sudo, some of the apps config files in your ~/ end up being owned by root and cause problems when you try to run the app as a normal user. gksu avoids this.

--edit-- and yes that rm command is pointing at the correct path ;)

Thanks jerome, I keep forgetting that it is gksu for nautilus.

I'll try to remember it for the next time.

---

### Post by newbee70 on 2009-01-14
> **kramer65 said:**
> Grrrrrrrreat! Thanks a lot!

Btw. I did use sudo nautilus now. Is that a problem..?

Not a problem but you should use gksu instead of the sudo command.
It is accepted practice.

---

### Post by chriscross93 on 2009-01-14
just be careful with sudo nautilus, you can do serious accidental damage...

---

### Post by jerome1232 on 2009-01-14
And I forgot to mention, deleting files in a root nautilus will have an unexpected affect. (oh and ditto on being careful)

As you know when you delete a file in nautilus it actually get's moved to the user's trash, same is true of root nautilus. So when you "delete" a file in root nautilus what your really doing is moving it to the root users trash located at /root/.local/share/Trash

To remove the file permanently then
A) use the rm command, "sudo rm -rfv /root/.local/share/Trash/*"

B) Bypass the trash this time in nautilus, hit alt+f2, type gksu nautilus, hit enter, hit ctrl+h to view hidden files, browse to /root/.local/share/Trash/ and hold shift+delete to bypass the trash when deleteing (should be info and files directories it's safe to delete both directories.

This is why I never recommend root nautilus for this type of thing, that and you should try to avoid running your file manager as root unless you really need to. (Using limited users is one major factor in Unix like operating systems that contributes to them being a hostile environment for malware to foster) Doing stupid things as root = broken system, doing stupid things as a limited user can only bork that user and that users files, see the difference?

---

### Post by Drubie on 2009-01-14
> **Michael.Godawski said:**
> 
here is a nice guide too:


[LIST]
[*][http://www.thegoss.com.au/modules/planet/view.article.php/406](http://www.thegoss.com.au/modules/planet/view.article.php/406)
[/LIST]

Great guide, but one thing: 
> 
    * /home/username/.share/local/Trash User's Trash (hardy and later)

something is fishy here...   the actual path to the user's trash is ~/.local/share/Trash, not the other way around.

I tried to follow that and almost freaked...

> **Michael.Godawski said:**
> 
I have always a bad feeling using sudo rm

I hear ya there!

---

