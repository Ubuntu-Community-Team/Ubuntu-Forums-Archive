---
title: "Suggestion: Right Click and Format USB Flash Drive"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2009-01-18
Not sure if this is the correct venue for suggestion, but. I am fairly a beginner, have had to use the terminal a few times here and there, uncomfortably  compiled a few things when I couldn't find a deb.

Anyways, the other day, my 8GB Flash Drive was totally empty and yet said that I had only 1.4MB, I soon realized just how hard it was to format a USB Drive for Ubuntu.

I Googled as much as I could, found quite a few VERY complicated suggestions that were WAY above my head to the point that I couldn't even attempt them as solutions, tried reading, IRC (XChat), after several hours, I realized...My old Windows Desktop is in the other room, all I'd have to do is plug in my USB Drive, Right click, select Format, select FAT32, and click OK, and.... Problem Fixed, in about 12 seconds.


USB Flash Drives are so common, that there seems no reason why even someone  like myself, who has gone through the ubuntu terminal for everything else, should have to give up and resort to Windows for such a simple task.

Does anyone know if making it easier to format a USB drive is anywhere on the priority list? If not, I will grudgingly keep my Windows Machine close by and working, even if it is only for this task. As it is EXTREMELY important. Id hate to have to keep around Windows just so that I can format USB Drives.

---

### Post by nhasian on 2009-01-18
I see what you mean.  although you cannot just right cilck on the drive and select format, it is pretty easy to format using gparted in System->Administration->Partition Editor.

I know its on the liveCD but if its not installed by default you can add it with:

```
sudo apt-get install gparted
```

---

### Post by bailbath on 2009-01-18
Go to system - admin menu and see if you have Partition Editor in the list.
If you don't you can install it from add/remove program at the bottom of application menu. Just use the search facility in the program and it will find Gnome partition Editor click the box to install.It will ask for your password.
Now it will be in the system - admin menu as Partition Editor.
Click it to launch it. Again it will ask for your password.
If you already got the usb stick in your computer it will available on gparted device tab at the end which has a choice of devices for example /dev/sda or /dev/hda on my system my usb stick turns up as /dev/sdc. If you have not got the stick in put it in and then refresh gparted on one of its menu's
If you have used a partition program before gparted works very much the same.
Here are some screenshots
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Ian

---

### Post by mister_pink on 2009-01-18
Also, formatting the stick shouldn't be a common occurance. It's likely that there were hidden files on there (show them in the file viewer with Ctrl+H). Most probably there was a .trash folder or similar containing deleted files.

---

