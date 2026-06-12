---
title: "deleting files in the trash bin"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by brokenhachi on 2009-05-19
hi everyone,

somehow, some locked files ended up in the trash bin, and now they are stuck there. i cant delete them, and i cant move them back to their original spot.. when i try sudo nautilus and then try to access the trash bin it says i dont have access to it.

how can i delete the files from the bin?


thanks in advance for the help;)

---

### Post by taurus on 2009-05-19
What's the output of this command from a terminal?

```
ls -la ~/.local/share/Trash/files
```

---

### Post by asmoore82 on 2009-05-19
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la ~/.local/share/Trash/files
```

[SIZE="3"]**+1**[/SIZE]

and/or
```
ls -laR ~/.local/share/Trash
```

---

### Post by brokenhachi on 2009-05-20
total 12
drwx------ 3 dave dave 4096 2009-05-19 22:56 .
drwx------ 4 dave dave 4096 2008-10-13 15:41 ..
drwxr-xr-x 3 dave dave 4096 2008-04-13 16:31 Old World of Darkness

and

/home/dave/.local/share/Trash:
total 24
drwx------ 4 dave dave  4096 2008-10-13 15:41 .
drwxr-xr-x 6 dave dave  4096 2009-03-16 22:13 ..
drwx------ 3 dave dave  4096 2009-05-19 22:56 files
drwx------ 2 dave dave 12288 2009-05-19 22:56 info

/home/dave/.local/share/Trash/files:
total 12
drwx------ 3 dave dave 4096 2009-05-19 22:56 .
drwx------ 4 dave dave 4096 2008-10-13 15:41 ..
drwxr-xr-x 3 dave dave 4096 2008-04-13 16:31 Old World of Darkness

/home/dave/.local/share/Trash/files/Old World of Darkness:
total 12
drwxr-xr-x 3 dave dave 4096 2008-04-13 16:31 .
drwx------ 3 dave dave 4096 2009-05-19 22:56 ..
drwxr-xr-x 3 dave dave 4096 2009-04-18 10:27 Werewolf

/home/dave/.local/share/Trash/files/Old World of Darkness/Werewolf:
total 12
drwxr-xr-x 3 dave dave 4096 2009-04-18 10:27 .
drwxr-xr-x 3 dave dave 4096 2008-04-13 16:31 ..
drwxr-xr-x 3 dave dave 4096 2009-04-18 10:25 Werewolf - The Dark Ages

/home/dave/.local/share/Trash/files/Old World of Darkness/Werewolf/Werewolf - The Dark Ages:
total 12
drwxr-xr-x 3 dave dave 4096 2009-04-18 10:25 .
drwxr-xr-x 3 dave dave 4096 2009-04-18 10:27 ..
drwx---r-x 3 root dave 4096 2008-02-02 21:39 kde
ls: cannot open directory /home/dave/.local/share/Trash/files/Old World of Darkness/Werewolf/Werewolf - The Dark Ages/kde: Permission denied

/home/dave/.local/share/Trash/info:
total 20
drwx------ 2 dave dave 12288 2009-05-19 22:56 .
drwx------ 4 dave dave  4096 2008-10-13 15:41 ..
-rw-r--r-- 1 dave dave     0 2009-04-18 10:24 kde.trashinfo
-rw-r--r-- 1 dave dave     0 2008-12-28 23:29 .mediatomb.trashinfo
-rw-r--r-- 1 dave dave   112 2009-04-18 10:26 Old World of Darkness.trashinfo

---

### Post by amingv on 2009-05-20
Try:

```
sudo chown -R dave:dave ~/.local/share/Trash/
```

and then try deleting them.

If that doesn't work (it should) do:

```
sudo rm -r ~/.local/share/Trash/files/*
```

---

### Post by brokenhachi on 2009-05-20
cool that first one worked. thanks!


so what exactly does that command do? -r is removing something i guess?

---

### Post by halitech on 2009-05-20
rm = remove
-r = recursive
~/.local = location

warning - be very careful with this command, especially when running it as sudo as it will remove whatever you point it at

---

### Post by mapes12 on 2009-05-20
Before you go punching in those rm commands read this:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Solution for a nice clean system without breaking anything.

---

### Post by amingv on 2009-05-20
> **brokenhachi said:**
> cool that first one worked. thanks!


so what exactly does that command do? -r is removing something i guess?

If the first one is the one that worked for you, here's what it does:

**sudo:** execute command with root privileges
**chown:** CHange OWNer
**-R:** recursively
**dave:dave:** to_this_user:and_this_group
**~/local...:** this file

> **mapes12 said:**
> Before you go punching in those rm commands read this:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Solution for a nice clean system without breaking anything.

I would **never** give a user a command to break his/her system. In fact, that's why I suggested chown first.

---

### Post by brokenhachi on 2009-05-20
ok so rm is remove and -r is everything gotcha.. something new everyday:D


how can you tell the location though..it always takes me forever to find where files are located.:confused: i guess that just comes with exp?

---

### Post by alphacrucis2 on 2009-05-21
> **brokenhachi said:**
> ok so rm is remove and -r is everything gotcha.. something new everyday:D


how can you tell the location though..it always takes me forever to find where files are located.:confused: i guess that just comes with exp?

If you select Places - Home Folder from the menu it fires up nautilus showing the contents of /home/<your user name>. If you select View - Show Hidden Files a bunch of additional stuff will appear in the window. .local is one of the folders that will appear.

---

