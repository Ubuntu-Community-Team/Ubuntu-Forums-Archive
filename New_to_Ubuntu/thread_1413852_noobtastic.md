---
title: "noobtastic"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by now_here on 2010-02-22
hi everybody!
i am new to ubuntu, and to the forum. 
just built my first box and thought it was time to try out ubuntu. :D
so i'm playing around in the terminal which is a whole new world for me and trying to get familiar with the basics of navigating the file tree, creating directories, moving and deleting files, and i'm bopping along using cd, ls, pwd, mkdir, rm and mv, feeling like i'm getting a little bit of a feel for it, and then i hit a wall. i'm in my home directory and cant seem to access any of the directories :confused:. heres a paste from the terminal:
> 
nowhere@nowhere-desktop:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates

nowhere@nowhere-desktop:~$ cd downloads
bash: cd: downloads: No such file or directory

nowhere@nowhere-desktop:~$ cd music
bash: cd: music: No such file or directory

nowhere@nowhere-desktop:~$ cd documents
bash: cd: documents: No such file or directory

nowhere@nowhere-desktop:~$ cd /home/nowhere/music
bash: cd: /home/nowhere/music: No such file or directory
nowhere@nowhere-desktop:~$ 

nowhere@nowhere-desktop:~$ ls -l
total 36
drwxr-xr-x 3 nowhere nowhere 4096 2010-02-21 14:58 Desktop
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-16 00:43 Documents
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-16 00:54 Downloads
-rw-r--r-- 1 nowhere nowhere  167 2010-02-16 00:11 examples.desktop
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-21 03:30 Music
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-16 00:43 Pictures
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-16 00:43 Public
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-16 00:43 Templates
drwxr-xr-x 2 nowhere nowhere 4096 2010-02-16 00:43 Videos
nowhere@nowhere-desktop:~$ 

i'm sure this is something simple and obvious, but this is all new to me, i felt proud just to be able to move a file using the terminal, thats where i'm at. so thanks in advance for any help!

---

### Post by crlang13 on 2010-02-22
Keep in mind that everything is case sensitive... Documents is different from documents etc.

---

### Post by tom.swartz07 on 2010-02-23
> **crlang13 said:**
> Keep in mind that everything is case sensitive... Documents is different from documents etc.

+1

Thats all that it is; you could try ```
cd Music
``` rather than ```
cd music
```

---

### Post by now_here on 2010-02-24
hahaha i knew it was gonna be something like that. thanks for the help guys!

---

### Post by Ozymandias_117 on 2010-02-24
[http://linuxcommand.org/]("http://linuxcommand.org/") << Really good place to help you learn BASH (the terminal)

---

### Post by now_here on 2010-02-28
> **Ozymandias_117 said:**
> [http://linuxcommand.org/](http://linuxcommand.org/) << Really good place to help you learn BASH (the terminal)
thanks! awesome site

---

