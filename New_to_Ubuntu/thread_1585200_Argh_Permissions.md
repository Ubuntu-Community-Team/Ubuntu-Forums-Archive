---
title: "Argh: Permissions"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Sgele™ on 2010-09-30
Hey guys, 

After finally being able to setup most of the stuff, i still have a feeling i have loads to learn :)

Why can't i copy something from the desktop into the /usr folder? I keep getting messages that i don't have any permissions to create/put the files into that folder. What i do is drag&drop the files from the desktop into the /usr/share/gnome-screensaver folder.

All i want to do is apply a screensaver to this Ubuntu build :) Though i am not giving up, because although it's quite hard understanding all of this, i don't want to go back to Windows :P

Can sombody help? please? :(

---

### Post by Hippytaff on 2010-09-30
Move the file with root priveleges in the Terminal
CD to the directory where the file is
```

 
sudo mv filename placemovingto/foldername

```

---

### Post by Verbeck on 2010-09-30
enter into terminal:
```
sudo nautilus
```it will open nautilus with root privileges, so you can copy the screen saver to that folder.

edit: remember to change the permissions of the copied files(rclick>properties>Permissions) so that you are the owner

---

### Post by nothingspecial on 2010-09-30
Press Alt_F2 and type ```
gksudo nautilus
```

Then your password

Make sure you don`t delete or move anything if you don`t know what it is of for

---

### Post by Hippytaff on 2010-09-30
CD to where file is (PWD to find out where you are and ls to list files that are in the directory that you are in)
 
```
 
sudo mv filenam /usr/share/gnome-screensaver folder

```
 
more acuratley
 
if the filename is a pain in the butt to type, type the first few letters and press TAB

---

### Post by Yougo on 2010-09-30
^be careful with sudo nautilus though. it gives the user all permission to royally screw up the system. a click out of place, a folder dragged and released carelessly and no real way to trace where it went (other than a one shot undo and a clumsy search)

also, files created by a rooted nautilus are owned by root, and aren't accesible without root afterwards.

not saying you can't do it, but just a heads-up

----

that said, can't you add the screensaver via the screensaver menu? (not on my Ubuntu box right now)

---

### Post by Hippytaff on 2010-09-30
Is this right or am I giving out duff info?
 
```
 
sudo mv filename /usr/share/gnome-screensaver folder

```

---

### Post by CharlesA on 2010-09-30
> **Hippytaff said:**
> Is this right or am I giving out duff info?
 
```
 
sudo mv filename /usr/share/gnome-screensaver folder

```

Looks right. :)

Granted, you should probably take "folder" out, but otherwise it's ok.

---

### Post by Hippytaff on 2010-09-30
that's ok then. :-) thanks for the reassurance

---

### Post by Sgele™ on 2010-09-30
Thanks guys, i'll go play with it a little and see how this ended up! You really are awesome :)

---

### Post by Sgele™ on 2010-09-30
Indeed, without the 'folder' it works!
Thanks!

---

