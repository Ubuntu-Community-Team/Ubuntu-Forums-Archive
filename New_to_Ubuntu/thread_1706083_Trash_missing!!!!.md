---
title: "Trash missing!!!!"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-03-13
Hi, all I am hoping for some help with a weird problem.

  My trash bin has gone. Can't find it with gksudo nautilus.
The icon in bottom panel is gone however when i click where the icon should be it opens with this error:  ```
Sorry, could not display all the contents of "trash": The specified location is not supported
```

  The same thing happens if I use the icon I made visiable on desktop. 

I am running a fairly new install of Lucid although I have been using Ubuntu for a year.
I have been having some permission problems and from my research I think it may have something to do with the .gvf file in the home folder.

The folder appears and has permission only to access files and I can't change them to delete. During the gk sudo I can not even see it. (with cntrl + h).
Once again any ideas would be greatly appreciated.

---

### Post by ron999 on 2011-03-13
Hi
Try making a new trash can.
Right-click on top panel.
Then 'Add to panel'.

---

### Post by hakermania on 2011-03-13
Hey, open a terminal and type:
```
mkdir -p ~/.local/share/Trash/{files,info}/
```and try again.

---

### Post by Vege 4wd on 2011-03-13
Hi still happening after running the code.

Tried to add to top panel but behaves like the one on the bottom panel.

---

### Post by hakermania on 2011-03-13
Open nautilus, press Ctrl+L , type trash:/// and press [Enter].
What's happening?

---

### Post by Vege 4wd on 2011-03-13
Hi, the code returns no such file or directory.

Can we just create one?

---

### Post by SEECo on 2011-03-13
You can have it on your Desktop by pressing Alt+F4 type gconf-editor. Press enter a dialog box will appear now Browse down to key apps/nautilus/desktop and tick the trash icon.

---

### Post by Vege 4wd on 2011-03-13
Just tried it but it is already ticked.

Perhaps I am missing a file.

---

### Post by Vege 4wd on 2011-03-13
Just found out that the same thing is happening when I click on computer under places.

Hopefully this info will be of some help. I had some back up home folders on an external disc when I loaded Ubuntu. Could this have be the problem?

---

### Post by Learning Linux 2011 on 2011-05-18
This post is kind of old now, but I just found out you can't use "sudo gconf-editor" command to get the trash can on the desktop.

just type in "gconf-editor" in a terminal, no sudo or gksudo

if you use sudo, you are modifying the root's desktop, not the user's desktop

---

