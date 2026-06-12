---
title: "Can't find package that Synaptic just installed"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by japhyr on 2009-04-02
Hello everyone,

I know I've seen this problem before, but I can't find a relevant thread.

I just installed ksociograma through Synaptic, but I can't find it on my computer.  It's not in any of the menus, and "locate ksociograma" shows nothing.

When this happens, does it mean nothing was downloaded?
What should I do?
Obviously the whole package was not installed properly.  Is there any simple way to see if some things were just downloaded?

Thank you.

-Eric

---

### Post by Sealbhach on 2009-04-02
Open up Synpatic and then look in File/History.

It will show you what you recently installed and removed.

You could also do 

```
sudo dpkg -l 

```
in the command line, to see what packages you have

and to search for your specific package:
  
```
sudo dpkg -l | grep ksociograma
```

.

---

### Post by llamabr on 2009-04-02
Right.  And locate is not only the wrong tool (it will find false positives), but it won't work until the database is rebuilt.  You can do so yourself with updated

Anyway, the correct tool to use is which.  So:
```

which ksociograma
```

will find it, if it's in your path, and it's installed.

---

### Post by gandaran on 2009-04-02
> **japhyr said:**
> Hello everyone,

I know I've seen this problem before, but I can't find a relevant thread.

I just installed ksociograma through Synaptic, but I can't find it on my computer.  It's not in any of the menus, and "locate ksociograma" shows nothing.

When this happens, does it mean nothing was downloaded?
What should I do?
Obviously the whole package was not installed properly.  Is there any simple way to see if some things were just downloaded?

Thank you.

-Eric
did you reboot, some applications need a computer reboot to show up in the menu, if it still doesn't show in the applications menu you can always add one in system » preferences » main menu.
or start the application in terminal by typing *ksociograma*

---

### Post by japhyr on 2009-04-02
Thanks everyone, I'll try this when I get home this evening and let you know if it worked.  I was curious about whether "locate" was the best tool to use, and how exactly it works.  I appreciate the clarification on that.

Eric

---

### Post by japhyr on 2009-04-02
Thanks everyone, it was installed and I was able to start the program.  I am happy to know about "which", and happy to be reminded that I can try to start a program just by typing its name in a terminal.

Eric

---

### Post by IronOutsider on 2009-04-02
You can also make a custom launcher which, I think, makes it a little easier to start the program. Just right click on your panel and click on Add to Panel. Then select Custom Application Laucher.

In the Create Launcher options, under command, just type the name of the command you put in Terminal and a name in the name field. Then you should be able to run the program with one click. I think its pretty handy!

---

### Post by Sef on 2009-04-02
Check System > Preferences > Main Menu.   Sometimes the icon is not activated.  Find it and click on the box next to it, so there is a check in it.

---

