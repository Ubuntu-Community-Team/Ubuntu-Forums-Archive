---
title: "Advie on ubuntu software for backing up NAS"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by silvercue on 2011-08-21
Hi,
 
I am new to Ubuntru and Linux and have set up a Ubuntu OS on a HDD I rescued from a broken NAS. (Other disk boots to Vista64) I have now got a new NAS and want to boot into Ubuntu and use the HDD as a back up for some of the files on my NAS - like photos.
 
I am really looking for software that will allow intelligent backups - so only transferring deltas accross the home LAN. Any ideas?
 
I did a search and came up with Dropbox, but after installing it is totally not what I need at all.
 
Also, I am confused as to how to add a folder on my drive for backups - adding folder option is greyed out when I go to file system. I am set as administrator.
 
Sorry if it is basic to you, but all new to me.
 
thanks

---

### Post by alphacrucis2 on 2011-08-21
rsync is probably what you want. 

[http://rsync.samba.org/]("http://rsync.samba.org/")

It's in the standard repos.

---

### Post by silvercue on 2011-08-22
got grsync - but it can't see my NAS....did a search and it seems very complicated to do this..
 
IS there not an easier way?  Everything seems so difficult in Linux :(

---

### Post by silvercue on 2011-08-23
rsync doesn't seem to do what I want as it can only see drives local to the computer through the GUI.  The NAS is on the local network so thought it would be ok.

Anyone know any third party software specifically designed for intelligent back ups that runs through GUI and works with Ubuntu and can see network attached storage?

At the moment I am having to copy whole folders.

---

