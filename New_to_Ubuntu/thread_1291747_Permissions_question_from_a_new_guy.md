---
title: "Permissions question from a new guy"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by tj_thompson on 2009-10-15
Hey guys,  I'm quite new and just put together a ubuntu box.  Everything's been going well (built mediatomb from the ground up, working out some samba wierdness) but I've bumped into a permissions issue that's confusing me. 

I have this folder: 

tjthomps@ubuntu:/backup/SFF$ ls -alrt / 
drwxrwxr-x   3 root backup  4096 2009-10-14 22:23 backup 

The folder is owned by root, but is part of the backup group.  The group permissions appear to grant write/modify access to the folder. 

tjthomps@ubuntu:/backup/SFF$ groups tjthomps 
tjthomps adm dialout cdrom backup plugdev lpadmin admin sambashare 

The groups command says I'm a member of the backup group.  However, I get this when I try to make a new directory:  

tjthomps@ubuntu:/backup/SFF$ mkdir /backup/new 
mkdir: cannot create directory `/backup/new': Permission denied 

This seems like it should be simple, but I'm not seeing what's wrong here.  why can I not create a new folder in this directory?  Can someone help a new guy out and point out the obvious for me?  I'm generally very good at finding answers myself, but I can't find what the problem here is :)  Thanks guys.  

TJ

---

### Post by tj_thompson on 2009-10-15
Ack.  I'll try to figure out how to put in linebreaks in the mean time...that's terrible.

EDIT: got it!  Now it's readable :)

---

### Post by wojox on 2009-10-15
It doesn't look like your in your home directory, so try:

```
sudo mkdir /backup/new
```

---

### Post by jbrown96 on 2009-10-15
That's really weird. I tried something similar.
```
sudo mkdir Desktop/test
``` ```
sudo chown -R root:cdrom Desktop/test
``` ```
sudo chmod -R g+w Desktop/test
``` I can then create folders within that. Here are some things to try
1) have you logged out since you were added to the backup group. New group permissions do not take affect until you login again.
2) Maybe the permissions only apply to the folder and not its contents?? try ```
sudo chown -R root:backup FOLDER
```
3) Along the same line as #2, maybe the write permissions aren't applied to the contents ```
sudo chmod -R g+w FOLDER
```


Just a quick tip. When you are posting it really helps if you use the quote and code tags. When you are posting, at the top of the text entry box, there is text bubble icon for quote and a # sign for code. It really makes reading posts a lot easier.

---

### Post by tj_thompson on 2009-10-15
Ah, you nailed it jbrown96.  I logged out and back in and I'm good!  I was rather confused at what was happening there :)  Thanks for the fast help.

From here on out, I'll make sure to use the code tags as well.  Matter of fact, here's what it looks like after simply logging out and back in:
```

tjthomps@ubuntu:~$ mkdir /backup/new
tjthomps@ubuntu:~$

```

Thanks again! :razz:

---

