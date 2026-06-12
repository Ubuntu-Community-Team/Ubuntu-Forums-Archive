---
title: "Gnome commander not working"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by rhenium3 on 2009-07-26
For some reason Gnome commander is not working. It says starting program and then nothing. I reinstalled it and that did not help. I have the latest version of Ubuntu (not sure what it is called or where to look it up)

Thanks for replies

---

### Post by Liolikas on 2009-07-26
Start it from terminal by typing name, and post debug info here.
Latest Ubuntu is 9.04. 
You can check what you have with uname -a command.

---

### Post by rhenium3 on 2009-07-26
Or lsb_release -a, right?

Ok, what is the command to start the program?  Sorry, I'm a begginer here...

---

### Post by Liolikas on 2009-07-26
gcmd maybe?
Also you can try mc (midnight commander).

---

### Post by rhenium3 on 2009-07-26
is there a command for starting programs or you just write the program shortcut?

---

### Post by Liolikas on 2009-07-26
If you type program name program will start:
firefox for example. Problem that some programs have crazy names. You can type first few letters and then press TAB 2 times for suggestions.

---

### Post by oldos2er on 2009-07-26
```
gnome-commander
```starts Gnome Commander. If you're unsure of a program's name (i.e., the command which starts the program), type (for example)
```
apropos gnome commander
```and the shell will give you some suggestions.

---

### Post by rhenium3 on 2009-07-27
So this is what I get:

rhenium3@rhenium3-laptop:~$ gnome-commander

Segmentation fault
rhenium3@rhenium3-laptop:~$

---

### Post by Malta paul on 2009-07-27
If its any help 'gnome-commander' has always worked great for me in Ubuntu.

I would remove the version you have installed it may be corrupted.
The latest version is 1.2.8-1 and you can download it as a .deb file from:
[http://www.getdeb.net/search.php?keywords=gnome-commander](http://www.getdeb.net/search.php?keywords=gnome-commander)
Just make sure you download the 32bit or 64bit version depending on your system.
When the .deb file has downloaded (its 3.2mb) click on the folder and it will install for you. When installed you will find it at, Applications>Accessories>Gnome Commander. And thats it :D

You can also get more information from the gnome-commander site:
[http://www.nongnu.org/gcmd/](http://www.nongnu.org/gcmd/)  
 
Have Fun:cool:

---

### Post by yaye on 2009-08-07
I'm having the same problem with gnome-commander crashing with a segmentation fault in Jaunty.  It does work if you type sudo gnome-commander and give the root password.  In previous versions, it worked without requiring the root password.

---

### Post by rhenium3 on 2009-08-18
nothing works :( is there a replacement? I miss my gnome commander! :(

---

### Post by yaye on 2009-08-19
Try Tux Commander (tuxcmd).  You should be able to get it via Synaptic.

---

### Post by rhenium3 on 2009-08-22
Ok, I installed it but can't find it in my Applications list. Where do I find programs afer they are installed?  Would something for KDE work for me?

---

### Post by yaye on 2009-08-23
If it is not in any of the menus, you can go to System -> Preferences -> Main Menu and create a menu item for it.  The command to start the program is tuxcmd .

---

