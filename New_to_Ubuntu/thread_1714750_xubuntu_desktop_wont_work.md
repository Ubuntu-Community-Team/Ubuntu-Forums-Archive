---
title: "xubuntu desktop wont work"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by tobydog on 2011-03-25
hi i seem to have lost the xubuntu desktop , when i start up in the xubuntu option it starts as normal , once i enter my password it goes back to the log in screen , refuses to go any further, it works ok with gnome , i prefer xubuntu desktop , how can i get this to work again please.

---

### Post by Arijit_Kundu on 2011-03-25
one brutal way will be to remove ~/.config/xfce4 folder...

---

### Post by gnicko on 2011-03-25
When your system starts up, can you get to the recovery mode in Grub? Also, is there another user on the system that you can log in to or that is able to log in? 

I've had the same thing happen happen in the past--not sure why really--but was able to fix it up with the recovery console option. It's been a while, so i can't remember exactly what steps to take, but it seems to me that I just started in recovery mode and "followed along" until the system restarted and everything was OK...course it depends on why everything went wrong to begin with....

---

### Post by oboedad55 on 2011-03-25
Have you tried reinstalling the xfce stuff from Gnome or the command line? That would be my first shot.

---

### Post by tobydog on 2011-03-26
yes reinstalling it looks like the best option , presumably i need to make sure its uninstalled , how do i do this , what command do i need to put in terminal to remove it , and then what to reinstall please.

---

### Post by Arijit_Kundu on 2011-03-26
try first by removing ~/.config/xfce4 folder. This may fix the issue.

---

### Post by tobydog on 2011-03-28
i am new to xubuntu and don't really have much of a clue what i am dong yet , what would i need to put into terminal to delete this file please

---

### Post by Dutch70 on 2011-03-28
> **tobydog said:**
> i am new to xubuntu and don't really have much of a clue what i am dong yet , what would i need to put into terminal to delete this file please

Just go to your home folder. Click "view" & select "show hidden files".
Then go to your .config folder, and you should find the xfce4 folder in there.

---

