---
title: "filename ending with ~ (Tilde)"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by munishvit on 2009-07-10
We often see hidden files with filenames ending with ~, in linux. What is the function of these file? Is there any harm if one deletes these files???

---

### Post by Mornedhel on 2009-07-10
They're backups, and you can safely delete them if you want to.

---

### Post by NilsE on 2009-07-10
> **munishvit said:**
> We often see hidden files with filenames ending with ~, in linux. What is the function of these file? Is there any harm if one deletes these files???
As Mornedhel said they are backups and can be deleted at your will.  However, if the are backups of config files like xorg.conf they are worth keeping since they can be re-used if there is a problem with recent changes.

---

### Post by munishvit on 2009-07-10
Friends, thanks for the reply...
Whenever I see those files (in my home directory) I use to delete them (had a habit). But, once I deleted file named C.odt~ which was associated with C.odt (which I use to update when I get something new on C). Next time when I tried to open C.odt, there were just some unreadable characters. Luckly some days back I made the backup of the same, so it didn't creat much problem. :)

So I want to make sure, is it always safe to delete *~ files? 

**NilsE** says, "they can be re-used if there is a problem with recent changes". But, how u do that??:confused:

---

### Post by NilsE on 2009-07-10
> **munishvit said:**
> 
**NilsE** says, "they can be re-used if there is a problem with recent changes". But, how u do that??:confused:

Rename the original to something like ending with .old and rename the one with the ~ by just removing the ~

---

### Post by earthpigg on 2009-07-10
> **munishvit said:**
> F
So I want to make sure, is it always safe to delete *~ files? 

**NilsE** says, "they can be re-used if there is a problem with recent changes". But, how u do that??:confused:

if _everything_ pertaining to your computer _always_ goes perfect, you will never have a use for any file ending in ~, and you can safely delete it.

if your computer is not Jesus Christ reborn, however, you may want to keep them around :D


as for using them:

lets say you edit your sources.list to include google's linux repository, so you can update google gadgets directly from google. it is located at /etc/apt/sources.list.

aaaaaaaaand lets say you accidentally make a horrible typo, and wipe your sources.list.

to fix that, we would do this:
```

sudo cp -i /etc/apt/sources.list~ /etc/apt/sources.list
```

cp is the command to copy. typing 'man cp' will show us the manual for this command.

-i is the option to ask 'are you sure you want to do this?' so you can re-read what you are about to do and make sure you didnt make *another* typo.

/etc/apt/sources.list~ is *what* we are copying.

the second one, /etc/apt/sources.list is *where* we are copying it to -- in this case, we are replacing the sources.list that we just screwed up by mistake with the backup sources.list (that ends in ~).


in a perfect world, ubuntu would backup any important config file before saving any changes to it. nothing is perfect, however. if i had a working sources.list right now and wanted to change it, i would probably back it up manually first just in case:

```
sudo cp -i /etc/apt/sources.list /etc/apt/sources.list~
```

again, i am including the -i to give myself a chance to double check what i just told my computer to do. always a good idea to double and triple check anything you do involving the command 'sudo'. think of typing 'sudo' as loading a gun: 

sure, guns are fun and do useful things... but if you aren't careful, a gun can also do all sorts of not-so-fun stuff.

(granted, we dont get files ending in ~ in real life...)

---

### Post by munishvit on 2009-07-11
Thanks..I got the point.

---

