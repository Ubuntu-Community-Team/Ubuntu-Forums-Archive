---
title: "Desktop launcher"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by ubu newb on 2011-01-02
I have a weather program, metwise, that I want to launch from the desktop.  It's an .sh file extension.  For now I need to go to my home/metwise and  find metwise.sh.  Once I double click I choose open in terminal and  opens normally.  However, I can't get it to work.  I right click and go through the steps but the program doesn't launch.    I choose gnome_panel_launcher.    This is a program I had to download.

What am I missing?

---

### Post by cheapie on 2011-01-02
You should be able to create a launcher on your desktop pointing to "/home/metwise/metwise.sh". Make sure it says "Application in Terminal" not "Application".

---

### Post by ubu newb on 2011-01-02
> **cheapie said:**
> You should be able to create a launcher on your desktop pointing to "/home/metwise/metwise.sh". Make sure it says "Application in Terminal" not "Application".


When I do the terminal pops up for a second then disappears.

---

### Post by ubu newb on 2011-01-04
Any suggestions?  Any reason why the terminal pops up and quickly disappears?

---

### Post by vagrale13 on 2011-01-04
Try with command
```
gnome-terminal -e "/full_path/to_archive/metwise.sh"
```

e.g. if the archive *metwise.sh *is in */home/metwise/metwise.sh*then command must be ```
gnome-terminal -e "/home/metwise/metwise.sh"
```

---

### Post by ubu newb on 2011-01-04
That does nothing.  Again a box appears then disappears.  I did copy the executable file to my desktop and the option to run in terminal/display/cancel/run comes up but again, nothing happens.  This is so frustrating that I can't get a program I regularly use to work off the desktop. :mad:

---

### Post by vagrale13 on 2011-01-05
> **ubu newb said:**
> That does nothing.  Again a box appears then disappears.  I did copy the executable file to my desktop and the option to run in terminal/display/cancel/run comes up but again, nothing happens.  This is so frustrating that I can't get a program I regularly use to work off the desktop. :mad:
The problem must be in *metwise.sh *not in the settings!
Put the script to your home folder and try to run the script with command
```
sh ./metwise.sh 
```and post the output of command, or tell us if it works well!

---

### Post by ubu newb on 2011-01-05
Yes, it worked and so did the gnome -e work as well.  I wasn't in the right directory when I tried it.  :x

I the question is, how do you apply either one to work with desktop startup?  

Thanks

---

### Post by mikewhatever on 2011-01-05
Just add it to the startup commands under System->Preferences.:KS

---

### Post by ubu newb on 2011-01-05
Not sure I follow?   I added a startup for metwise with the command: gnome-terminal -e /home/rick/MetWise_Net/metwisenet.sh but that yields the same results.

---

### Post by vagrale13 on 2011-01-06
If you want to add it on startup programms, 
you must create another script with the following
```
#!/bin/bash
sleep 15 &&
gnome-terminal -e "/home/rick/MetWise_Net/metwisenet.sh"
```save it somewhere and execute it, and add this script on startup programms!
e.g. if you save this script with name **metwisenet** to your home folder
command must be */home/rick/metwisenet*

*Change number **15** with the seconds you want start **metwisenet.sh** after loggin!

---

### Post by ubu newb on 2011-01-07
It does the same thing, pops quick terminal pop up then disappears.  This whole thing is  baffling.   I never thought I would have this many problems adding a program to start up on my desktop.

---

