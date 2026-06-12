---
title: "Can't find installed game"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Indigo340 on 2010-01-14
I downloaded Urban Terror from Softpedia and installed it but can't find a shortcut to start it.

I was expecting to find a shortcut on the Games menu but it is not there or on any other menus. 

Synaptic says that it is installed and I have tried re-installing it but still no shortcut.

I searched for the file and folder (where it should be installed) to see if I could manually open it but can't find it.

Any advice please.

Ubuntu 9.10

---

### Post by Darce on 2010-01-14
Mine is at 

/home/<username>/.urbanterror/ioUrbanTerror.i386

but then mine has a icon under Applicatios->Games as well !

---

### Post by 73ckn797 on 2010-01-14
If you can find out the main file name you can create a shortcut via System/Preferences/Main Menu.

Did you restart the system after installing? That can sometimes fix the problem, though not in all cases.

---

### Post by Indigo340 on 2010-01-14
As I can't find it, I can't make a shortcut for it.

I have re-started many times since installing.

---

### Post by 3rdalbum on 2010-01-14
The shortcut is only created if the person who made the package included one.

See my signature for details on how to create a launcher for any program in Synaptic.

Also you'll probably find that the command 'urbanterror' starts the game.

---

### Post by Indigo340 on 2010-01-14
Thanks 3rdalbum, the command 'urbanterror' does nothing, it just says "command not found" 

I have looked at your tutorial and although it is very informative, it was no help because I can't start the game from Terminal.

There must be a way to solve this, how could I find the folder or files ?

---

### Post by audiomick on 2010-01-14
try this
```
find -iname urban*
```

info on find
```
man find
```

I am not absolutely sure, but I think this will turn up files with "urban" in the name. Might help you find your game.:D

---

### Post by Indigo340 on 2010-01-15
Nope nothing works, I don't understand how Synaptic can say that a program is installed when there is no trace of it.
What am I doing wrong ?

---

### Post by houseworkshy on 2010-01-15
If you go to synaptic package manager find the package and then look at the properties tab it will bring up a window on which is a tab called installed files, click that for a list of them. You could also use the locate command in the terminal.  Enter "man locate" ( without the quotes ) in the terminal for more details on how the command is used.  When you have that information try running the program via Alt + F2 to test it.  If all works then follow the advice above to add a menu item.

---

### Post by 73ckn797 on 2010-01-15
Found this on the Urban Terror site:
[http://forums.urbanterror.net/topic/1717-urban-terror-on-linux-faq-read-this-first/](http://forums.urbanterror.net/topic/1717-urban-terror-on-linux-faq-read-this-first/)

Did you look at info there?

---

### Post by bolucpap on 2010-01-15
You can start synaptic, find the package, right click on it and select properties. The on the dialog box that comes up, select the Installed Files tab. This will give you a list of files the package installed, and one of them will be an executable file. You can run it from the terminal or create a menu item for it for ease of use.

---

### Post by Indigo340 on 2010-01-23
> **73ckn797 said:**
> Found this on the Urban Terror site:
[http://forums.urbanterror.net/topic/1717-urban-terror-on-linux-faq-read-this-first/](http://forums.urbanterror.net/topic/1717-urban-terror-on-linux-faq-read-this-first/)

Did you look at info there?

Thanks a lot, I obviously overlooked the fact that I must have Q3 installed to play this game. 
Thanks for your help and advice, I'll mark this thread 'solved' now.

---

