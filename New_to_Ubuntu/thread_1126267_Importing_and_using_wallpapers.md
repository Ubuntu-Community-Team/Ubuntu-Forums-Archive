---
title: "Importing and using wallpapers"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-15
Hi, have installed ubuntu 8.10 and have been searching for a suitable wallpaper. During search I saved a number of images to the desktop. I subsequently wanted to move them from the desktop and put them into the shared backgrounds folder which already holds such images. I tried drag and drop but it wouldn't let me. What am i doing wrong?

---

### Post by Jakey_TheSnake on 2009-04-15
It should let you. Is the shared backgrounds folder inside your home directory? Do the pictures have the same filenames as others? 

So I can help, what's the filepath of your shared backgrounds, what format are they?

---

### Post by clive littlewood on 2009-04-15
Hi

Just go to system > preferences > appearence > background then click add and navigate to the file you store your wallpaper (not desktop) then just click on the paper you want.     :p

Clive

---

### Post by Jakey_TheSnake on 2009-04-15
^ He's having problems moving the files into a new directory, not importing them I believe. 

Does it say permission denied when dragging and dropping?

---

### Post by clive littlewood on 2009-04-15
Hi

OOOOOOps didn't read the thread properly.

Clive

---

### Post by dan1973 on 2009-04-15
Yes, permission is denied, files are of differing types, will list when back on 'ubuntu PC' - after dinner!

---

### Post by lhb1142 on 2009-04-15
> **dan1973 said:**
> Hi, have installed ubuntu 8.10 and have been searching for a suitable wallpaper. During search I saved a number of images to the desktop. I subsequently wanted to move them from the desktop and put them into the shared backgrounds folder which already holds such images. I tried drag and drop but it wouldn't let me. What am i doing wrong?

:KS  Check the "Permissions" in each picture's "Properties" and make sure that you have selected the option to access and write to the file.

You do this by right clicking the picture and clicking on "Properties" which is at the end of the dialog box brought up by right clicking. Go into that box and you will see a tab marked "Permissions."

You may see that the permission is "access file." Merely change that to allow "accessing and writing" (or a similar command).

Then you can do whatever you wish with the file.

I hope this helps you. ):P

---

### Post by Jakey_TheSnake on 2009-04-15
Press Alt+F2, type in "gksudo nautilus", navigate to where they are, then drag and drop ;)

---

### Post by dan1973 on 2009-04-15
thank you, problem resolved, was one of permission.

---

