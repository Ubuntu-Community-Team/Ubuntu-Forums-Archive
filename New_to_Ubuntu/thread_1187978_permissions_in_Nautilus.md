---
title: "permissions in Nautilus"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-15
I would like to use Nautilus to move a few files from one user's directory to another.  I have administrative priveleges, but when I click on a file in one user's directory and try to "drag and drop" it into another's directory, a message box pops up and says "permission denied".

Is there a way to open Nautilus (the "places" menu on the taskbar) so that I can move things around?

If not, I can open a terminal window and do things that way, but with Nautilus it is pretty easy to see the "from" and "to" directories, etc.

---

### Post by theozzlives on 2009-06-15
Hit Alt+F2 and type ```
gksu nautilus
```

---

### Post by MrWES on 2009-06-15
> **raymondvillain said:**
> I would like to use Nautilus to move a few files from one user's directory to another.  I have administrative priveleges, but when I click on a file in one user's directory and try to "drag and drop" it into another's directory, a message box pops up and says "permission denied".

Is there a way to open Nautilus (the "places" menu on the taskbar) so that I can move things around?

If not, I can open a terminal window and do things that way, but with Nautilus it is pretty easy to see the "from" and "to" directories, etc.

Nautilus has a plugin for gksu too. It'll allow you to right click on the file and 'open as root".

```
sudo apt-get install nautilus-gksu
```

---

### Post by halitech on 2009-06-15
you only have admin rights if you invoke sudo (or gksudo) for a program, otherwise you are just a normal user and have no rights outside your home. 

To MrWes, he's not asking about opening files as root but needing/wanting to move the files so while the plugin you mention is handy it won't really help him much in this case.

---

### Post by raymondvillain on 2009-06-15
Thanks for all the help!

alt+F2 and gksu nautilus was just what I needed.

---

### Post by knomaly on 2009-06-16
With respect to the first paragraph written under the topic heading gksu on the live.gnome.org website @ [http://live.gnome.org/gksu](http://live.gnome.org/gksu) , what part of the nautilus file manager is "not written to take advantage of the [PolicyKit]("http://live.gnome.org/PolicyKit") framework"? 

With respect to the aforementioned paragraph, Ubuntu 9.04, and raymondvillain's issue, is the gksu command valid?

---

