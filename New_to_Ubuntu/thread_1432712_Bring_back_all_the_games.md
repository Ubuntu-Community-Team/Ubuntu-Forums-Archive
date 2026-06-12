---
title: "Bring back all the games"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-18
I have deleted some games from the main menu by running,

```
sudo alacarte
```

How to bring it back?

---

### Post by mbzn on 2010-03-18
System>Preferences>Main Menu. this gives you a list with all the installed apps and you can show/hide them...

---

### Post by k23 on 2010-03-18
> **mbzn said:**
> System>Preferences>Main Menu. this gives you a list with all the installed apps and you can show/hide them...

If I deleted them, then there is no way to recover them on this screen.

---

### Post by lavinog on 2010-03-18
you really shouldn't be running alacarte as root (sudo)

Try reinstalling them with synaptic

---

### Post by lavinog on 2010-03-18
> **k23 said:**
> If I deleted them, then there is no way to recover them on this screen.

It depends on if the OP actually deleted them, or if they just unchecked them.

---

### Post by k23 on 2010-03-18
> **lavinog said:**
> It depends on if the OP actually deleted them, or if they just unchecked them.

Ok, if I deleted them? :) Thanks for the reply.

---

### Post by karthick87 on 2010-03-20
If i run without sudo i get the following error..

```
karthick@Learners-desktop:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/karthick/.config/menus/applications.menu'

```

---

### Post by lavinog on 2010-03-20
> **getyourkarthick said:**
> If i run without sudo i get the following error..

```
karthick@Learners-desktop:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/karthick/.config/menus/applications.menu'

```
Looks like you broke your system by running it with sudo.
This is why it is recommended to not run gui apps with sudo...you should be using gksu or gksudo for gui applications

try this:
```

ls -l /home/karthick/.config/menus/applications.menu

```
it likely says root is the owner...in which case you will need to chown the all of the files.
```

sudo chown karthick:karthick /home/karthick/.config/menus/*

```

---

### Post by karthick87 on 2010-03-23
> **lavinog said:**
> Looks like you broke your system by running it with sudo.
This is why it is recommended to not run gui apps with sudo...you should be using gksu or gksudo for gui applications

try this:
```

ls -l /home/karthick/.config/menus/applications.menu

```it likely says root is the owner...in which case you will need to chown the all of the files.
```

sudo chown karthick:karthick /home/karthick/.config/menus/*

```


I have tried but no use,these are the outputs..

```
karthick@Learners-desktop:~$ ls -l /home/karthick/.config/menus/applications.menu
ls: cannot access /home/karthick/.config/menus/applications.menu: Permission denied
karthick@Learners-desktop:~$ sudo chown karthick:karthick /home/karthick/.config/menus/*
chown: cannot access `/home/karthick/.config/menus/*': No such file or directory

```

---

### Post by lavinog on 2010-03-23
It looks like you dont have ownership of the whole folder

does this show anything:
```

find /home/karthick/.config -user root

```

you could also try:
```

sudo chown -R karthick:karthick /home/karthick/.config

```
the -R means to change the ownership of all files and folders in that folder.

also you should test if there are any other files in your home folder owned by root:

```

find -xdev /home/karthick -user root

```
-xdev means don't look at files on other filesystems (many mounted systems mount in /home/karthick/.gvfs)

---

### Post by karthick87 on 2010-03-24
```
karthick@Learners-desktop:~$ find /home/karthick/.config -user root
/home/karthick/.config/menus
find: `/home/karthick/.config/menus': Permission denied
/home/karthick/.config/Google
/home/karthick/.config/Google/GoogleEarthPlus.conf

```


```


karthick@Learners-desktop:~$ find -xdev /home/karthick -user root
find: paths must precede expression: /home/karthick
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
```

---

### Post by 3rdalbum on 2010-03-24
If a command or program only operates within your home directory and doesn't need to modify anything outside there, then don't run it as root.

If you do run a GUI program as root, use 'gksudo' rather than just plain 'sudo'.

And you might need to reinstall the programs whose menu items you removed.

---

### Post by k23 on 2010-03-24
Ok. In case you accidentaly deleted your menu items.

1. find /home/user/.config/menus/applications.menu file
2. open it and find all tags saying <deleted/> and delete them
3. your menu items will reappear

thx Lavinog for the file location :)

---

### Post by lavinog on 2010-03-24
> **getyourkarthick said:**
> 
```


karthick@Learners-desktop:~$ find -xdev /home/karthick -user root
find: paths must precede expression: /home/karthick
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
```

sorry, I think you need to use sudo since the folder is not readable by the user, and the error is because I put the -xdev in the wrong location:
```

sudo find /home/karthick -xdev -user root

```

---

