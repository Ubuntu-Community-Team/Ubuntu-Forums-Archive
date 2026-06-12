---
title: "restore snapshot using backintime"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by pgar23 on 2009-10-26
Hi,
I am trying to restore a snapshot with the program Back-In-Time. I bodged up my GUI somehow and I don;t want to mess around with anything, plus I need to learn how to restore a snapshot.

BIG POINTER: I want to do this with the COMMAND LINE. not via GUI.

Anyone know how?
Thanks in advance.

---

### Post by earthpigg on 2009-10-26
hi,

i've never worked with that program.

however, there is almost always one easy method to restore a program's settings 'back in time' to when you first installed it:

delete it's personal settings dotfiles in your /home directory, forcing the program to revert to default settings.

you didn't mention if you where using GNOME or KDE or what, so i can't tell which specific dotfile or set of dotfiles this is.

in your home directory, type 'ls -a' and pay attention to the folders and files that start with a dot (aka, period: .). those are called dotfiles.

for gnome, look at and inside .config and .gconf. find the one that looks like it may be part of the program you messed up (remember, everything in Linux is just another program... including gnome-panel and the rest of your graphical interface). YOU may think it's all just "Ubuntu", but your computer would disagree with you. type "ps -a" in a terminal to see just how many programs you have running.

once you think you have found the dotfile for the right program, test your theory by renaming that file, restarting the program, and see how it goes:

```
mv ~/.dotfolder/somefile mv ~/.dotfolder/somefilebackup
```
then restart that program. if your educated guess about the dotfile was off, rename that dotfile how it was:
```
mv ~/.dotfolder/somefilebackup ~/.dotfolder/somefile
```


dotfiles can be dropped in, backed up by drag and drop, removed, manipulated in all sorts of ways. dig around in your 'back-in-time' backup and see if it kept your dotfiles, and after you locate the right one go ahead and move it over to your /home where it goes.

---

### Post by Matt__ on 2009-10-26
Back in time is an image backup prog (ie; hes not trying to repair BIT but use it to restore drive image).

I think you will find he has corrupted his Ubuntu install and is trying to restore it from an image. My guess is a failed graphics driver install as he no longer has access to GUI.

Cant help with back in time as Ive only just downloaded it myself.

Have you tried to restore Ubuntu from the tools available at boot? like the autorepair of xorg/graphics?

---

### Post by pgar23 on 2009-10-26
> **Matt__ said:**
> Back in time is an image backup prog (ie; hes not trying to repair BIT but use it to restore drive image).

I think you will find he has corrupted his Ubuntu install and is trying to restore it from an image. My guess is a failed graphics driver install as he no longer has access to GUI.

Cant help with back in time as Ive only just downloaded it myself.

Have you tried to restore Ubuntu from the tools available at boot? like the autorepair of xorg/graphics?

Thanks for your reply Matt,
  You are write, I am using the backup Util named "Back-In-Time" not BIT, and yes I have tried the autorepair xorg under the recovery mode, but it did not solve the problem.

Does anyone know how to restor a snapshot via CLI??

---

### Post by pgar23 on 2009-10-27
Bump. Please does anyone know how restore snapshot via CLI>>??

---

### Post by earthpigg on 2009-10-28
have you looked around for "back in time" documentation, or a related discussion forum?

forum users can only speak based on their own experiences.... so if it's a niche or not-so-popular app among the ubuntuforums.org community then you may have problems getting help.

---

