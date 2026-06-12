---
title: "Deleting folders from /home/user/"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by BhumibolTheGreat on 2009-03-30
Hi Guys, 

I have an obsession for deleting old and unused directories and files.
After upgrading to Ubuntu 9.04 I have left with several unused folders in /home/user . 
Some of them belong to applications that were not transported from last version like Google Search, Dropbox and others. 

So my question is:
How can I know which folder is obsolete and can be deleted with no worries?
I mean, in Windows you can't just remove folders from "Program Files", you have to uninstall them using "Add/Remove Wizard". 
I guess this is the same situation in Ubuntu, so I have tried to look for these old ghost applications in "Add/Remove Wizard", but they are missing from there.
If I delete the folders, could it be that other configuration files are using them? Or is it safe as they are stand alone folders?

Hope you understand my question and where my confusion is coming from. 


Regards,
Bhumibol

---

### Post by kanikilu on 2009-03-30
There isn't a way to automatically distinguish between "used" and "unused" folders...

Most "dot" files/folders in your home directory are for configuration, so are probably safe to remove if you are not using the associated program anymore.

---

### Post by CatKiller on 2009-03-30
They aren't the equivalent of things in "Program Files," they are the equivalent of things in "My Documents." Uninstalling the program that created them (by design) doesn't remove them, since they are personal to each user.

They generally take up essentially no space at all, and you can't see them in normal usage unless you make the effort, but if it makes you happy to delete them then you won't really be doing any harm. If you subsequently decide that you do want to run the programs that used those configuration files, new configuration files will be created from the defaults for that program. That's how they were generated in the first place.

Your emails, bookmarks, installed games in Wine, and so on are also kept in hidden directories in your Home folder, so you might want to think about it before you delete those.

---

### Post by bodhi.zazen on 2009-03-30
You may enjoy these links :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

New in 9.04 is a utility to help with this :

System -> Administration _> computer janitor

*be warned, 9.04 is still in [s]alpha[/s] beta ;)

---

