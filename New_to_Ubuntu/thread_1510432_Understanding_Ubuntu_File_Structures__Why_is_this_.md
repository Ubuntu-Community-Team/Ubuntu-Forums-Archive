---
title: "Understanding Ubuntu File Structures:  Why is this file not showing up?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by u2rcrazy on 2010-06-15
[SIZE=4]Understanding Ubuntu File Structures:  Why is this file not showing up?[/SIZE]


Please see this attached screen shot below:
[ATTACH]160541[/ATTACH]

On the right, I have the "*select local directory*" window open within Mozilla Thunderbird mail program.  On the left, I have my "*File Browser*" open.  I have noticed that the  "*select local directory*" has a folder called **.thunderbird**, as well as many other **.(folder_name)**'s that appear to be applications and plug-ins.  How come I'm not able to see these **.(folder_name)** folders in other places in my computer such as  "*File Browser*"?  

I'm asking this, because I'm pretty familiar with the Windows file structure, but not with Ubuntu's.  My second question is, where is a good place to read up on or watch a video about _[COLOR=Indigo]how to[/COLOR] [COLOR=Purple]learn Ubuntu's file structure when coming from a Windows environment[/COLOR]_?  This would be a big help and I greatly appreciate your time.

Sincerely,
Bob:guitar:

---

### Post by Bachstelze on 2010-06-15
Files (and directories) that start with a period are *hidden files*. They're pretty much like hidden files in Windows, you usually have to do some special action to see them.

---

### Post by zer010 on 2010-06-15
**.file_name **is a hidden file or folder(directory). you can choose to show or hide these by going to the "View" menu at the top of the directory window.
You can make any file or directory hidden by adding the dot to the name as seen with the others.

---

### Post by Morbius1 on 2010-06-15
Open Nautilus ("File Browser") > Edit > Preferences > Show hidden and Backup files.

---

### Post by Penguin Guy on 2010-06-15
[COLOR="Green"]Ctrl + H[/COLOR] should toggle hidden files.

---

### Post by bodhi.zazen on 2010-06-15
From the command line, use 

```
ls -A
```

---

### Post by wyliecoyoteuk on 2010-06-15
Hidden files and folders usually contain configuration and settings files (as in Windows), or data files (such as email folders)

---

### Post by linux-hack on 2010-06-15
this can help you a little bit to get started : [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

and for more google is your friend :D

---

### Post by u2rcrazy on 2010-06-17
Thanks guys!!!  :p  All your answers were great=D>

Bob:guitar:

---

