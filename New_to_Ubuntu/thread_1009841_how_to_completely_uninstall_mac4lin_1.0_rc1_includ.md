---
title: "how to completely uninstall mac4lin 1.0 rc1 including the login screen"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by djmike on 2008-12-13
hey everyone im a begginer to ubuntu and i installed the mac4lin package and then i quickly found it annoying so now i want to go back to the good ol default ubuntu theme, but when i click on the uninstaller it doesn't seem to do anything, any help guys?

---

### Post by nakama85 on 2008-12-13
> **djmike said:**
> hey everyone im a begginer to ubuntu and i installed the mac4lin package and then i quickly found it annoying so now i want to go back to the good ol default ubuntu theme, but when i click on the uninstaller it doesn't seem to do anything, any help guys?

try going to terminal and entering the following

```
sudo apt-get remove mac4lin
```

---

### Post by nakama85 on 2008-12-13
I found this code in another thread 

```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

for further info see this thread
[http://ubuntuforums.org/showthread.php?p=6349465](http://ubuntuforums.org/showthread.php?p=6349465)

---

### Post by djmike on 2008-12-13
well the first one u posted didnt help at all and the second one only changed the icons back the right side of the window, but its fine cuz im gonna have to reboot my pc anyways cuz i got a virus in windows and i installed ubuntu using wubi, so thanks anyways

---

### Post by Orion8 on 2008-12-13
I was having the same problem. I am a Mac user switching over to Ubuntu and I thought it would be cool to try. I quickly found Mac4Lin to be confusing and then annoying (since it really isn't OS X and it confused my ability to tell what I was doing).  

Anyway.  I got that script to work.  You just have to make that uninstall script file executable.   The way I did it was this:  use the file browser (start by opening Places -> Home Folder) to navigate to the uninstall script.  Select it, hit <Ctrl><i> to bring up the file's properies.  Click on the "Permissions" tab and then check the box by "Execute" that says "Allow executing file as program".  Then you can double click the file and say "run in terminal" and you are back to the default Ubuntu (Hardy) setup.

I hope this helps somebody!

---

### Post by mbruges on 2009-05-25
Thanks! I've been struggling too, couldn't work out why the damned script wouldn't execute... Seems like such an obvious solution ;)

---

### Post by matheusrosa on 2009-12-07
Hey guys, i can't uninstall it :/ nothing works here... What can I do?

---

### Post by rwaki on 2010-04-01
> **matheusrosa said:**
> Hey guys, i can't uninstall it :/ nothing works here... What can I do?
Alternatively, you can download the Mac4Lin again and once you extract it you will find the Uninstall file. It worked for me

---

### Post by @rizz on 2010-04-01
Hi guys, if nothing else works give this a try.....


```
$ sudo apt-get autoremove [filename]
```and then give your user account password.



hope this helps.......works for me every time:D!

---

