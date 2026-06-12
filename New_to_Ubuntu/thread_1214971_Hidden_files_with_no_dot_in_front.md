---
title: "Hidden files with no dot in front"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Mariane on 2009-07-16
I am looking at a windows xp disk which I would like to backup before partitioning to install ubuntu. 

Some files and some directories do not appear  in the File Browser even with the option "show hidden files". The ls command displays these files in green and the folders either in blue or in black with a green background. 

What do these colour-codes mean and how can I make all files and folder become visible in the File Browser? 

ls -lh tells me the files are completely unprotected, eg:

-rwxrwxrwx 2 root root 7 2008-08-18 17:10 CacheSize.txt 

Is this normal? 

Mariane

---

### Post by Cypher on 2009-07-16
Do
```

ls -la

```
to show all files in the directory, regardless of being hidden or not. The color codes usually go something like:
Green - Executable
Blue - Directory
Cyan - Symlink
White with red background - SUID'ed file
Red with back background - Broken symlink
Black - Regular files

I believe that covers all the colors..at least on my Jaunty Ubuntu..:)

---

### Post by Mariane on 2009-07-16
Thank you. So they are mostly executables. 
How can I un-hide them? 

Mariane

---

### Post by Elep.Repu on 2009-07-16
Linux views windows disks as they are, without system files being hidden.
nothing should be hidden at all.

```
rsync /windisk /backup 
```should do what you want. (to backup)

---

### Post by Cypher on 2009-07-16
Choosing the "Show hidden files" should be enough to make them visible, especially if they can be seen from the LS command. I don't believe there's anything else you need to do..

---

### Post by Mariane on 2009-07-16
> **Cypher said:**
> 
Choosing the "Show hidden files" should be enough to make them visible, especially if they can be seen from the LS command. I don't believe there's anything else you need to do..


Well, they should be visible, but they are not... I'm running Ubuntu from the cd, so maybe it doesn't have the same power as when it's installed? Or is this silly?

Mariane

---

### Post by earthpigg on 2009-07-16
it may be silly, it may not be.

can you give us an example of a file you are absolutely positive exists, *and that you can see in windows*, but that you are not seeing in ubuntu?

---

### Post by Mariane on 2009-07-16
I never even tried looking at them with windows... 

What I am saying is that they are displayed by the terminal with the 
```
ls
``` command, but they are not displayed by Gnome File Browser... 

And they have these weird permissions. 

An example would be 
```

/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002109110000000000000000F01FEC/12.0.4518/XFILE.PSP

```

(I chose XFILE not because it is giving me more trouble than the rest but because the nme made me smile).

---

### Post by earthpigg on 2009-07-16
wow, that is odd!

have you tried a different graphical file manager, so we can see if there is any pattern to what does and does not show these files?

pcmanfm is pretty lightweight, quick download.

```
sudo apt-get install pcmanfm
```

shows up in applications -> system tools

---

### Post by mcduck on 2009-07-16
> **Mariane said:**
> I never even tried looking at them with windows... 

What I am saying is that they are displayed by the terminal with the 
```
ls
``` command, but they are not displayed by Gnome File Browser... 

And they have these weird permissions. 

An example would be 
```

/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002109110000000000000000F01FEC/12.0.4518/XFILE.PSP

```

(I chose XFILE not because it is giving me more trouble than the rest but because the nme made me smile).

Your file seems to be on a mounted Windows filesystem.  That would explain the permissions, as Windows filesystems don't support ownerships and permissions as they are handled in Linux/Unix systems, so permissions are set for the whole drive when it's mounted.

And that also explains why it's hidden, as Windows hides it's files at filesystem level while Linux doesn't even have the same kind of hidden files and simply uses the dot in the filename to keep certain files from cluttering your file managers and terminal outputs. So the way of hiding files is completely different as well.

So yes, your situation seems completely normal, no need to worry about it. And I really doubt that you'd need to backup data from  any Windows system directory (like where the file you posted is). Backing up your personal data is what matters, as that's what's hard to get back if lost while Windows will definitely recreate it's own stuff if something breaks and you need to reinstall it. :)

---

