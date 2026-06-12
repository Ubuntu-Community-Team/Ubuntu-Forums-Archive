---
title: "How to change the permission of an application ?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-11-18
I have to use the kppp application for my broadband dongle to work.  Though kppp shows up in Applications->Internet, I am unable to run it from there because I get a 'permission denied' error.  So I always have to launch it from terminal however, I would rather like to just click on the icon to connect without having to open it up through the terminal all of the time.  Is there away to change the permissions of an app so that I can run this app as a normal user ?
Thanks.

-Yos

---

### Post by Excedio on 2009-11-18
When you are running it in the terminal, how are you doing this? What command are you typing?

---

### Post by YosefKaro on 2009-11-18
The command that I use from terminal is 'gksudo kppp' and that works.

-Yos

---

### Post by Excedio on 2009-11-18
Ok great. Right click on your top panel and click Edit Menus. Then find the program (KPPP) and double click on it. Where it says COMMAND: type in
```
gksudo kppp
```
Close the Menu Editor and try running the program from your Applications menu.

---

### Post by YosefKaro on 2009-11-18
Thank you for the advice...it sounds good and sound.  However, when I right click on my top panel, I don't get the option 'Edit Menus'.  I couldn't even find it as a sub menu.  Any more ideas ?

-Yos

---

### Post by philinux on 2009-11-18
System>prefs>edit menus.

---

### Post by sisco311 on 2009-11-18
Press Alt+F2 and run:
```
alacarte
```

---

### Post by Excedio on 2009-11-18
Ok, instead of clicking anywhere on the top panel, right click on the word "Applications." Let me know if you still don't see it.
 
By the way...What version of Ubuntu are you using?

---

### Post by YosefKaro on 2009-11-18
Thanks a lot for all of your help :D I found it through System -> Preferences -> Main Menu...I double clicked on the application and changed the command from kppp to gksudo kppp and it works.  Now I just saw that right clicking on Applications brings up the edit menu as well :D

-Yos

---

### Post by Excedio on 2009-11-18
Good deal. :-)

---

