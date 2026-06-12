---
title: "Backingup"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by hedge2211 on 2009-02-22
I am new to ubuntu and was wondering what program i should use to backup and what i should backup?

---

### Post by blueridgedog on 2009-02-22
In Linux people generally backup /home as this is where the user generated content is stored.  If you put yours elsewhere, then you can adjust accordingly.

How you backup your data depends on the media you intend to backup to.  If you tell me what you have to backup to, I can make a suggestion or two on backup methods.  The built in program is great...system -> administration -> Simple Backup

---

### Post by DGortze380 on 2009-02-22
rsync is a good way to backup to an external drive.

Open a terminal,

Enter to add all new files and update current backups-
sudo rsync -ax /Path/To/Source /Path/To/Destination

Enter to add all new files, update current backups, and delete deleted files-
sudo rsync -ax --delete /Path/To/Source /Path/To/Destination

Example, I use this command to sync my backup with my current files-
sudo rsync -ax -delete /home /media/My_External

---

### Post by capnthommo on 2009-02-22
hi hedge2211
i don't know if this will be much help to you but i asked a similar question some weeks ago.  try this thread

> [http://ubuntuforums.org/showthread.php?t=1000092](http://ubuntuforums.org/showthread.php?t=1000092)

i still haven't totally solved it but there is a help page and a few opinions on what to use.
the main thing, i think, is to get it stored on an alternative drive such as an external HDD.
i think i tend towards rsync myself, but i am still undecided.  just get it backed up somewhere - what i do at present is just make a direct copy of my data files (photos, music, text etc) on a DVD-rw which i periodically re burn using the K3b disk burner which i personally find quite straightforward, and use foxmarks to keep my browser bookmarks backed up.

and what about backing up the system, you ask?  well as long as i have my data saved to dvd i can do a complete re-install and partition, and then go through the tiresome process of re-adjusting things to my liking.  tedious, but at least i can save my data to load again when i have rebuilt the system.

it's not the most elegant method, but it seems to work, but when i get an ext HDD drive this week i can set about making complete backups of system and data to that.  as i said, i think i shall use rsync to do it.
do give my thread a look, as it might give you a starting point.
good luck
nigel
ps.  don't underestimate the importance of backing up, particularly before making major changes.
:guitar:

---

### Post by MrKlean on 2009-02-22
I set my puter up the way I wanted... then made a live cd with remastersys !!  I love that proggie LOL!

---

