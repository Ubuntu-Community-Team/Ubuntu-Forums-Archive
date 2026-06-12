---
title: "Recover lost data"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by cartisdm on 2009-01-19
After formatting my harddrive which previously had Windows on it and installing Ubuntu on it I remembered that I had a old My Documents folder on that computer that contained a bunch of my old pictures, some music, and word docs.  Most of it isn't important but I'd be really bummed if I couldn't recover my pictures since those are pretty sentimental.

I've used Stellar Phoenix data recover in the past but that's a windows application.  Is there anything I can do to recover my harddrive?  It's only been formated once since the delete and I know data recovery isn't 100% but anything I could save would be great:confused::confused:

---

### Post by taurus on 2009-01-19
Stop using that computer.  Then, hopefully testdisk would be able to recover your data on it, [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by cartisdm on 2009-01-19
I'm going to go download that on my desktop now.  Is it similar to Stellar Phoenix in any way?  Is it like a GUI software program that I can just let run a few hours then check back to see what files it's recovered?


EDIT:  I saw there is also a companion program to that called PhotoRec which is specially for picture recovery.  I think I'll try that

---

### Post by renzokuken on 2009-01-19
there is a program called **Foremost** that can recover JPGs. i used it when i accidentally reformatted the wrong partition last year and got back 90% of my photos. wasnt so good with word files though.

have a look here
[http://tombuntu.com/index.php/2008/04/09/recover-deleted-files-with-foremost/](http://tombuntu.com/index.php/2008/04/09/recover-deleted-files-with-foremost/)
and the section on Foremost here
[https://help.ubuntu.com/community/DataRecovery#Foremost](https://help.ubuntu.com/community/DataRecovery#Foremost)

---

### Post by linux_tech on 2009-01-19
Give testdisk and photorec a shot: 
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

A good reference for data recovery:: 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

You may also want to check out ntfsundelete

---

### Post by cartisdm on 2009-01-19
I'm using PhotoRec and I've selected the partition that I want to recover files from.  Then it asks me to chose a location to save the recovered files in (don't select to use the same partition I'm searching).

I have an external USB harddrive plugged in, it's mounted, I go navigate to the location (it has full permissions) but then it says "Do you want to save files in /media/Big Max I get an error saying it can't create directory in this location.  If the directory has permissions why can't it save?


EDIT:  I noticed that /media didn't have full permissions so I changed that to Read/Write but now I see this error

```
desktop@desktop-tv:/media$ sudo chmod 777 /media/Big\ Max/
chmod: changing permissions of `/media/Big Max/': Read-only file system

```

---

### Post by linux_tech on 2009-01-20
make sure your path is correct. you can also try saving to a different location such as your home directory

---

