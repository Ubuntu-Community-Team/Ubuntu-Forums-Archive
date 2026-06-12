---
title: "Help! I messed something up with gdm!"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by ubun2geek on 2011-04-29
hi everyone!
I have ubuntu 11.04, but i also have kubuntu-desktop installed on it. I modified the file at /etc/X11/default-display-manager to say GDM when previously I had KDM. Now I have no display manager and I cannot use my computer.

---

### Post by ~Plue on 2011-04-29
Did you give the full path correctly? for gdm its /usr/**s**bin/gdm, and for kdm its /usr/bin/kdm.
you could switch to a tty (ctrl+alt+F1) and run *sudo /etc/init.d/gdm* *start* to get to a gui, then revert/correct the changes made to /etc/X11/default-display-manager.

---

### Post by ubun2geek on 2011-04-29
I will try that, thank you.

---

### Post by Calash on 2011-04-29
If you cannot get the GUI up you can use Nano from the terminal

```

sudo nano /etc/X11/default-display-manager

```

And make your changes there.

---

### Post by ubun2geek on 2011-04-29
Hey I think that is what I need to do. What are the controls for editing and saving?

---

### Post by ~Plue on 2011-04-29
arrow keys to move the cursor
ctrl+O , press return to save the changes
ctrl+X to exit
or ctrl+X , Y , return to save and exit

---

### Post by ubun2geek on 2011-04-29
WOnderful job! Thank you SOOOOO much!
Can I ask one last question?
I have 11.04 but the Unity desktop does not show up.

---

### Post by ~Plue on 2011-04-29
sorry, cant help you there since i don't have much experience with it....

---

### Post by lupusnoctu on 2011-04-29
I can't answer regarding the unity desktop, but I do want to recommend that if you ever want or need to change your default display manager again, you use the reconfiguration scripts rather than editing that file yourself. The scripts actually *know* where the binaries for the DMs are, and know correct syntax for the configuration files, and will ensure that you don't forget to edit any files that need editing. The reconfigure scripts work for pretty much all packages, and is simple as running the following in terminal:

```
$ sudo dpkg-reconfigure "package"
```

in the case of switching from KDM to GDM, 

```
$ sudo dpkg-reconfigure kdm
```

This will open an ncurses UI allowing you to choose your new default DM from a list of options. My recommendation is that when you want to change DMs, use the reconfigure script for the DM that you're changing FROM. It does not matter, really and you certainly could do dpkg-reconfigure lxdm (if you have LXDE install too) to change to gdm from kdm and it would work, but it makes more sense to use the package you're changing from.

Hope that helps. :)

---

### Post by verymadpip on 2011-04-29
I found that if a machine didn't have the 3D capability to run Unity it would default to the 'Classic' desktop.
Could that be the case?
I thought I saw mention of Unity 2D from a ppa which may work on lower spec machines.
That's not meant to be an insult about the quality of your machine by the way :)

---

### Post by ubun2geek on 2011-04-30
thats all right :) I'll look into that
Thank you. And it did say something about my machine not meeting the hardware requirements.

---

