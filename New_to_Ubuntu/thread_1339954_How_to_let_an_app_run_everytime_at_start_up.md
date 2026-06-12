---
title: "How to let an app run everytime at start up?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by BioVirtual on 2009-11-28
I want some of my apps (like Dictionary,...) to run at start up automatically.

Thanks.

---

### Post by Virtual Liberty on 2009-11-28
System / Preferences / Startup Applications - let us know if you can't figure out how to add one in there.

---

### Post by BioVirtual on 2009-11-28
Well, I think I have to add the executable file in command field right? where can I find that file? Basically where does Ubuntu install apps?  Where is Ubuntu "Program Files" ?! :)

---

### Post by Virtual Liberty on 2009-11-28
You should be able to find them in /usr/bin ( for the future reference, [Linux directory structure]("http://www.tuxfiles.org/linuxhelp/linuxdir.html") ).

---

### Post by BioVirtual on 2009-11-28
Thanks. 
Few file structure questions:
 - Why user "root" has a folder directly in file system other users don't
 - What is the difference between the bin in file system and the bin in usr folder? is it shared between all users?
 - Where is the location of a user home folder and its subfolder (Desktop, Download,...)?

and lots of other Qs that I think I'll find them by getting more experience working with Ubuntu.

Thanks...

---

### Post by 3rdalbum on 2009-11-28
> **BioVirtual said:**
> Thanks. 
Few file structure questions:
 - Why user "root" has a folder directly in file system other users don't

Because root is special. I think it also has something to do with /home often being on a different partition - if /home can't be mounted, at least root still has his/her home directory so they can fix the system.

>  - What is the difference between the bin in file system and the bin in usr folder? is it shared between all users?

/bin holds more basic utilities; /usr/bin holds application programs. I'm not sure what the exact distinction is, but anything that's not essential for bringing the computer up should be in /usr/bin/.

>  - Where is the location of a user home folder and its subfolder (Desktop, Download,...)?

My username is 'chris' - so my home directory is at /home/chris.

> and lots of other Qs that I think I'll find them by getting more experience working with Ubuntu.

Thanks...

Three other tips regarding the filesystem:

1. Any external drives (CD/DVDs, external hard disks, flash drives etc) are usually mounted within /media

2. Any network shares that you mount from within Gnome (for instance, if you go to Places > Network and double-click on a local share) will be accessible through a hidden folder called ".gvfs" inside your home directory. If you use network shares, then make a bookmark to ~/.gvfs for it to appear in the Open/Save dialogs in your programs.

3. Your user account's settings (Gnome/KDE settings, application program settings etc) are also stored in hidden folders inside your home directory, so if you back up your system make sure you remember those hidden folders.

4. All programs inside /bin, /usr/bin and /usr/local/bin (don't ask) can be launched just by typing their name into the terminal; no need to put the full path of the file.

So, these two commands are the same:

```
/usr/bin/gnome-dictionary
```

```
gnome-dictionary
```

---

### Post by Rinzwind on 2009-11-28
Ok I will add in too:

You can find the program that starts something in a couple of ways.

1. in synaptic AFTER installing software you can choose "properties", "installed files". The one you want is most likely in one of those dirs posted by the person above me: /bin /usr/bin /usr/local/bin

Example with "giver" (a utility that lets you share files over your OWN network):
> /.
/usr
/usr/bin
/usr/bin/giver
/usr/lib
/usr/lib/giver
<..>


so /usr/bin/giver is most likely the executable :) 

2. From the menu:
System, preference, main menu.

Find the item you want to know how to start it and click properties. "command" has the value that starts a program.

3. If you want to find where something can be found. You can use 
locate giver

> locate giver|more
/home/rinzwind/.config/giver
/home/rinzwind/.config/giver/preferences
/usr/bin/giver
<..>
/usr/share/man/man1/giver.1.gz
/usr/share/menu/giver
<..>
Here you can also see that there is a manual for giver and that there is a .config in my home dir!

4. man giver
will show that manual

:)

---

### Post by BioVirtual on 2009-11-28
Thanks...
to make it  a good reference, I'll add any other question regarding system files to this post.

---

### Post by pebo on 2009-11-28
[This]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") link explains a bit about the linux file structure

---

