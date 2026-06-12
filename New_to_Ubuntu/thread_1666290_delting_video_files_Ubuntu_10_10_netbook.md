---
title: "delting video files Ubuntu 10 10 netbook"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by crippin2 on 2011-01-13
Hi, this question may have an obvious solution but being new to linux i am puzzled. How do I delete video files from my video folder.  I am using Ubuntu 10 10 netbook version, 'right clicking' on the file does nothing, in the link index screen 'right clicking' gives no delete or move to rubbish bin nor can I drag the file to the rubbish bin.  Maybe I have to use the terminal, if so could some-one please tell me the code. thanks

---

### Post by TeoBigusGeekus on 2011-01-13
```
rm ~/Videos/nameoffile.extension
```
Watch out with rm (mistyping could delete something different from what you initially intended - by the way: rm deletes files/folders forever, ie. don't go looking for them in Trash if you regret it afterwards.)

---

### Post by crippin2 on 2011-01-13
Thanks TeoBigusGeekus tried that but get error folder/file not found.  Will try again tomorrow when I have more time

---

### Post by wannabegeek on 2011-01-13
I suggest that you install  'trash'   utility  instead of using rm

to install trash in terminal:
```
sudo apt-get install trash
```

then navigate to video directory in terminal and use:
```
trash /path/to/file
```

to recover from the trash, is different than the GUI....but it is easy enough...I forget the exact
commands but they are in the man pages. 
```
man trash
```

I have deleted my video directory that gets setup with install so I don't remember exactly where it is supposed to be....I am guessing that in your case now, it is not in  /home/Video

Are you able to see if it is ?

---

### Post by no2498 on 2011-01-13
if your in the down load folder click edit, select all, edit, delete 
if under places, recent documents, clear recent documents
that gets rid of the list in the players too

---

### Post by crippin2 on 2011-01-13
Thanks all you guys, just downloaded Thunar File Manager did the trick in no time.  Well worth downloading for easy file management..

---

### Post by TeoBigusGeekus on 2011-01-13
+1 for thunar.
You won't regret it.

---

