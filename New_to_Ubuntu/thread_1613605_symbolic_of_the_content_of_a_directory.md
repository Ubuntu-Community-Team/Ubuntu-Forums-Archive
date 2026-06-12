---
title: "symbolic of the content of a directory"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by louisJ on 2010-11-04
Hey

I just installed ubuntu! and I'd like to create a symbolic link to my documents from windows.
I would like for the directory "Documents" in ubuntu Home to display all the files and directories I have in /media/E/Administrateur/Mes\ documents/.
So in a terminal I type:
cd ~/
ln -s /media/E/Administrateur/Mes\ documents/ Documents

But it creates a link into "Documents": ~/Documents/Mes\ Documents/ 
instead of directly listing the content of  /media/E/Administrateur/Mes\ documents/   in "Documents".

Morevoer the idea to add a "*" like this:  ln -s /media/E/Administrateur/Mes\ documents/* Documents
doesn't work for me because I would like that when I create a file or directory in ~/Documents, it is also created in /media/E/Administrateur/Mes\ documents/.

How can I do that?

thanks

---

### Post by A_M_S on 2010-11-04
I'm not sure if this is what you want

cd ~/Documents
ln -s /media/E/Administrateur/Mes\ documents/ mydocs


This will create inside the directory Documents a symbolic link to

/media/E/Administrateur/Mes\ documents/ with the name of mydocs

When inside ~/Documents you can access to your windows docs with the command

cd mydocs

---

### Post by cariboo on 2010-11-04
I don't auto mount my NTFS partition, so this link would have to be recreated every time the NTFS partion was mounted. IF you want to auto mount your NTFS partition ,use /etc/fstab.

To create a symbolic link to your Documents directory on your windows partition, the command would look something like this:

```
ln -s /media/E4345EFC345ED0E2/Users/Cariboo/Documents Windows_stuff
```

The above command needs to be run in your home directory. What I've done is link my Documents directory to Windows_stuff in my home directory.

**Note:** Windows Vista and 7 have an applet called mlinks, that does essentially the same thing, but Windows can't access an ext4 partition without extra software, but I'm still not sure mlinks will work with directories/files on a Linux partition.

---

### Post by louisJ on 2010-11-05
Hey AMS and cariboo907,
thanks for answering. This is what I don't want, what I'd like is for "the content of mydocs" (and not the directory "mydcocs") to be displayed when I inside ~/Documents.
Any idea?

---

### Post by tgm4883 on 2010-11-05
> **louisJ said:**
> Hey AMS and cariboo907,
thanks for answering. This is what I don't want, what I'd like is for "the content of mydocs" (and not the directory "mydcocs") to be displayed when I inside ~/Documents.
Any idea?

```
cd ~/
rmdir Documents
ln -s /media/E/Administrateur/Mes\ documents/ Documents
```

:EDIT:

I should probably point out that you will want to move anything in your Documents folder into /media/E/Administrateur/Mes\ documents/ before you rmdir it

---

### Post by louisJ on 2010-11-06
Hi [[COLOR=#339900]**tgm4883**[/COLOR]]("http://ubuntuforums.org/member.php?u=191664")

Thanks this is perfectly what I was looking for. First removing Documents is what I was missing.

---

