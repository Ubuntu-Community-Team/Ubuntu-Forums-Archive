---
title: "i need help  cd /&lt;path-to-directory&gt;/"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by David-IT on 2009-04-19
i copyed it to my desktop my ussername is david the file i  copied it into is wow_install, so how do i type that in like cd /david/desktop/wow_install?? please help i am very lost any help will be greatlly appreciated!

---

### Post by nandemonai on 2009-04-19
> **David-IT said:**
> i copyed it to my desktop my ussername is david the file i  copied it into is wow_install, so how do i type that in like cd /david/desktop/wow_install?? please help i am very lost any help will be greatlly appreciated!

cd ~/Desktop/wow_install

Remember 2 things...

1. Linux is case sensative.
2. / = the start of the system, a bit like c:\ in Windows

So the full path to a dir in your home (ie Desktop) would be /home/username/Desktop.

~/ is a shortcut to your /home/username directory.

---

### Post by qamelian on 2009-04-19
You would use: 
```
cd ~/Desktop
```

or

```
cd $HOME/Desktop
```

or

```
cd /home/david/Desktop
```

---

### Post by spiderbatdad on 2009-04-19
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

ok when you open terminal, generally the environment is /home/user. typing pwd will show you that. so cd Desktop is all that is needed to change to Desktop. The above link should help a lot.

---

### Post by David-IT on 2009-04-19
omg wow tyttyyttytytyt omg i cannot say ty enough is there any way to add like rep or thnx? also ty for the guide i am reading atm!

---

### Post by neu2buntu on 2009-04-19
the terminal always starts in "home" directory when inside gdm ...for example do code ```
ls 
```(this will show files inside home) ```
ls -a
``` will show all files including HIDDEN files ie dot "." files.... if you want to move back to the last directory if you have "cd" inside a directory use code ```
cd ..
```   try searching "linux commands" or "terminal commands" maybe print them out for famialarity!!!! or buy some linux books.......:P

---

### Post by MrWES on 2009-04-19
> **David-IT said:**
> omg wow tyttyyttytytyt omg i cannot say ty enough is there any way to add like rep or thnx? also ty for the guide i am reading atm!

Just wait until you learn how to write aliases!

[http://linuxreviews.org/quicktips/alias/]("http://linuxreviews.org/quicktips/alias/")

Plenty of web sites with examples and instructions.

Bill

---

### Post by DGortze380 on 2009-04-19
two useful commands for beginners to a CLI

pwd  - print working directory, shows your current location in the directory tree

whoami  - show which user you are currently operating as

---

### Post by Gen2ly on 2009-04-19
Also bash has auto-complettion which means you can type:

```
cd ~/Des
```

Hit tab and line will be completed.

Good to see someone learning the terminal.

---

### Post by David-IT on 2009-04-19
ok i got another problem i pop a disk in for wrath of the lich king  the installer executable is hidden and you need to re-mount the disc with the 'unhide' option. To do this type in a terminal: so i use these command's:
> sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/once i run the second command it gives me this:
> mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 and i have tried this in root still nothin, also i am triyng to learn terminal but it is sooo mutch different then cmd imo

---

### Post by steve101101 on 2009-04-19
just open the disk normally on nautalis and on the keyboard press Ctrl+H

---

### Post by DGortze380 on 2009-04-19
> **David-IT said:**
> 
 and i have tried this in root still nothin, also i am triyng to learn terminal but it is sooo mutch different then cmd imo

You're right, it's much more powerful, you'll see.

you may try the -o loop flag

example: sudo mount /dev/cdrom /media/cdrom0/ -o loop


But ...

sometimes it's just easier to user the GUI, there is an option to show hidden files, simply select the option (or ctrl+h)... and eject and reinsert the disk if need.

---

### Post by David-IT on 2009-04-19
i tried all those comands and ctrl+h still does nothing even tried h in caps lol if anyone wants to remote connect to me i would greatlly appreacite it [email]dl152567@att.net[/email] is my yahoo and windows messenger  or please hlp me :D

---

