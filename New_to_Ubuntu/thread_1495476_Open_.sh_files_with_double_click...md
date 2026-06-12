---
title: "Open .sh files with double click.."
date: 2010-05-28
forum: New to Ubuntu
---

### Post by rockoprem on 2010-05-28
So, as the title says, I want to run a shell script (Matlab program) by double clicking on it. Presently, I can open it by either typing ./matlab in the terminal or by creating a launcher and choosing the 'run in terminal' option. Is there anyway to just run it with a simple double click? :-?

---

### Post by -humanaut- on 2010-05-28
Try right-clicking on it make the default program it runs in gnome-terminal and make it executable.

---

### Post by rockoprem on 2010-05-28
yup... using chmod +x, I made it executable.. and I can't choose a default program to run Matlab.. because, I am trying to run Matlan itself!

---

### Post by AJH101 on 2010-05-28
I may have got the wrong end of the stick but couldn't you right click and (under Permissions I think) tick the 'executable' box?

---

### Post by KdotJ on 2010-05-28
When you double click on the file, doesn't it give you choice to display, run, or run in terminal?

---

### Post by ankspo71 on 2010-05-28
Hi,
It's probably best to place it in your home folder then create a menu shortcut the it, and the probable shortcut command might be:
```
sh /home/<user>/matlab.sh
```
Hope that helps.

---

### Post by rockoprem on 2010-05-28
Hi, there is no problem in making the file an executable. Also, when i double click on it, it gives me the usual 4 options. None of them work. Infact, when I click on 'Run', the splash screen of Matlab is splashed for a few seconds and then it disappears! Matlab runs perfectly fine when I run it via the terminal, or create a launcher and run it in a terminal.. and I also tried placing it in the home folder, didn't quite seem to work! :(

---

### Post by Vishal Agarwal on 2010-05-28
try put the shell script link in /bin folder.

ln -s  /your shell script path/ /bin/link name

[change the required accordingly.]

---

### Post by rockoprem on 2010-05-28
yup.. it is already in the bin folder... i also tried it with the 777 permission +x mode.. I also found some other links with similar kind of problems, I guess one has to fiddle around with the script itself..
 [http://www.linuxquestions.org/questions/programming-9/executing-shell-script-in-terminal-directly-with-a-double-click-370091/](http://www.linuxquestions.org/questions/programming-9/executing-shell-script-in-terminal-directly-with-a-double-click-370091/)  
[http://macosx.com/forums/howto-faqs/41816-howto-open-terminal-shell-scripts-double-click.html](http://macosx.com/forums/howto-faqs/41816-howto-open-terminal-shell-scripts-double-click.html)

---

### Post by intrader on 2010-11-24
> **KdotJ said:**
> When you double click on the file, doesn't it give you choice to display, run, or run in terminal?
Before Nov 10th it used to open .sh files in FAT volumes by simply doubleclick. 
Now I don't know how to set the executable bit. The context-menu->Permission->Executable-checkbox toggles but reverts back to not executable. 
The default application to open the file is set to Open Office not what I want.
The contents of the  Pharo.sh file I am having problems with is: [http://pastebin.ubuntu.com/536076/](http://pastebin.ubuntu.com/536076/)

---

