---
title: "disk full but cannot see why??"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by candtalan on 2009-05-16
I have a dual boot win-ubuntu 8.04 machine which has a 18.3GB ubuntu partition.
nautilus says there is only 590MB free

This is fairly minimal system and I am struggling to know why it shows so full.

Applications>accessories>disk usage analyser shows / as containing 7GB only, but:
system>administration>system monitor
shows this also total size 18.2GB, 1.5GB free but 590MB available, presumably available for me as user.

I have been using sbackup and I suspect that somehow, when its old backups have been deleted, they maybe have not been cleared out of the wastebasket (root permissions?) Anyway, I can not see any wastebasket content.

However, if I use 
sudo nautilus 
and then view hidden files I see nearly 10GB  of files inside
/root/.local/share/Trash/files

and my guess is that these are the problem.

Any help would be much appreciated.

---

### Post by NHArticleTen on 2009-05-16
sounds like you're on the right track

---

### Post by candtalan on 2009-05-16
how do I get rid of them though?

---

### Post by candtalan on 2009-05-16
found it I think

 sudo rm -r  /root/.local/share/Trash/files/2009-04-19_10.2.2.2.2.2.53.34.479009.170L.ful

---

### Post by Paqman on 2009-05-16
Yeah, you've got to be careful deleting stuff as root. A good way to find things like is by launching the disk usage analyser as root by hitting ALT-F2 and:
```

gksu baobab

```
It'll give you a nice graphical way to look for any huge fat files that are sitting on your system. Sbackup can be a terror for doing this if you mess the settings up a little.

---

### Post by candtalan on 2009-05-16
> **candtalan said:**
> found it I think

 sudo rm -r  /root/.local/share/Trash/files/2009-04-19_10.2.2.2.2.2.53.34.479009.170L.ful

This worked ok. However, I had to get rid of at least a  dozen unwanted such directories in root's Trash, one by one ...... because I had allowed sbackup to fill the (rather small) ubuntu partition :-(  

I could not see a way to use this type of command to remove more than one directory.

Does rm -r support multiple directories please?

---

### Post by sjovat on 2009-05-16
is this what you are looking for?
*rm -r <dir1> <dir2>*

---

### Post by sjovat on 2009-05-16
or if you have several files with simular names you can yea a '*' where they differ.

for example : rm -r *.ful
then you remove all files in the directory tha end with '.ful'

(I'm not used to tlking on  forms... and not used to tying english... 
  so please tell me if it's not undersandalbe. :P)

---

### Post by Didius Falco on 2009-05-16
Be very careful with those **rm** commands, especially the **rm -r** ones. Type it out wrong and you could hose your whole system...

Regards,

Didius

---

### Post by candtalan on 2009-05-17
> **sjovat said:**
> is this what you are looking for?
*rm -r <dir1> <dir2>*

Maybe. do the < and > characters have to be used?

---

### Post by bumanie on 2009-05-17
You don't need to use < >. But as already warned, be very careful what you delete. Delete the wrong thing(s) and you may have to reinstall.

---

### Post by Bush_Roo on 2009-05-17
I recommend changing from the present working directory to the directory which contains the files.

```
rm -r
```

This is a very dangerous command, and I have done some serious damage to my own home folder with it... (insert some curses over lost pictures)

```
cd /root/.local/ (etc etc etc)
```

then

```
rm *
```

Better to be safe than sorry.

Avoid using -r if you aren't sure what you are doing, but feel free to do something like

```
rm -i * 
```

(It will just prompt you with "rm: remove regular file `filermisgoingtodelete'?" on every file ;) )

If it won't delete, use sudo, but only use it as a last resort.)

---

### Post by sjovat on 2009-05-17
no.. they are no supposed to be there... :P

the <> I mean.

---

### Post by CatKiller on 2009-05-17
> **candtalan said:**
> This worked ok. However, I had to get rid of at least a  dozen unwanted such directories in root's Trash, one by one ...... because I had allowed sbackup to fill the (rather small) ubuntu partition :-(  

I could not see a way to use this type of command to remove more than one directory.

Does rm -r support multiple directories please?

Personally, I would just run ```
gksudo nautilus
```to get a file manager window with root privileges and delete the files from there. I guess I'm just a point-and-click kinda guy when it comes to file management.

---

### Post by mapes12 on 2009-05-17
I had a similar problem.This howto fixed it for me: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by marym on 2010-03-28
I would just like to say thank you everyone.  I tried to install a backup system but ended up filling a .var root directory.

Through this forum I found out a safe way to identify the problem and delete the unwanted files.

Mary

---

