---
title: "back up my /home folder"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by pgar23 on 2009-11-04
Ok, so i have been researching many different methods of backing up and restoring folders and files. And I have come to the understanding, correct me if I'm wrong, that you only need to back up your /home directory and sub-folders because this directory contains all of the essential configuration files.

What is the simplest method/program/code to back up and restore the /home?

All I WANT TO DO IS BACK UP MY PROGRAMS, FILES, MUSIC, MOVIES, ETC. and THEN RESTORE THEM, HOW DO I DO THIS???

---

### Post by pgar23 on 2009-11-04
I tried this program named "Back-in-time" and it creates snapshots of the directory and it does a wonderful job of doing that, but when you have to restore them...it becomes an impossible task to do via command line interface. Sure, there is a GUI for that, but the GUI is not always available, especially when you have deleted or botched up the wrong file.

---

### Post by Raistlin355 on 2009-11-04
I have never had a problem backing up my /home directory using:
```
rsync -rtvPWR /home /myserver
```
/home being the directory being copied and /myserver being the destination.  This will however not copy your programs, unless by programs you mean code that you have created yourself and stored in your /home directory in that case it will, you will have to reinstall them.

---

### Post by pgar23 on 2009-11-04
Thanks. what is the -rtvPWR option for??

---

### Post by Raistlin355 on 2009-11-04
Wow lets see if I remember without having to use man pages.  In order 
-recursive -times -verbose -Partial -Wholefile -Relativepaths.

YAY!! I remembered!!  ok so -r to recurse into subdirs, -t to preserve modification times, -v to tell you whats happening, -P to keep partially trasferred files, -W to transfer while files, -R to make the directory on at the destination.  You really don't have to use any of them, its just they way I taught myself to use rsync years ago.

---

### Post by pgar23 on 2009-11-04
Wow, thanks alot. I really appreciate that info.

---

### Post by Raistlin355 on 2009-11-04
No problem, anytime.  I hope it helps ya!!

---

### Post by ndefontenay on 2009-11-04
Music and movies etc... might be too much for ubuntu one but since we're talking backup, you can also go to Applications>Internet>Ubuntu One, get an account on the webpage and register your computer (it's all straight forward) then copy whatever folder you want to sync there by copying them to Ubuntu One folder in places.

For the home folder I didn't use rsync previously but I totally will because it will make copying faster.

Short answer: Yes. Copying /home will get all your personal data.

---

