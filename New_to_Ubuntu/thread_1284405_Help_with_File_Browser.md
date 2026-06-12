---
title: "Help with File Browser"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Penguinlord on 2009-10-06
Hello,
I am a new user to Ubuntu. I have used xubuntu in brief, however I did not have this problem. I booted my computer from my flash drive boot disk. After installing the OS I can open any applications I please. However I can not open the file browser, whenever I try (via places on the panel) it says "starting 'location name'" and in the bottom panel. But then that simply goes away and I am left with nothing. Also the desktop does not show any files. I do know that there is a file there because it showed in the Terminal (i only know a little).
So help me, what do I need to do to fix this problem? 

Go ahead and ask me questions if you need more info.

---

### Post by arrange on 2009-10-06
First I would try and create a new user and check if the problem persists there. 

You can also open the Terminal and type```
nautilus
```(the file browser) and see if it launches and what it writes to the terminal output.

---

### Post by Sarmacid on 2009-10-06
Type in a terminal ```
nautilus
``` and post the output here.

---

### Post by Penguinlord on 2009-10-06
[FONT=monospace]It said

[/FONT]```
Segmentation fault
```

---

### Post by itsbrad212 on 2009-10-06
try:

```
sudo nautilus
```

---

### Post by Penguinlord on 2009-10-06
I get the same message:

```
harrison@harrison-desktop:~$ sudo nautilus
[sudo] password for harrison: 
Segmentation fault
harrison@harrison-desktop:~$ 
```

---

### Post by Paqman on 2009-10-06
> **itsbrad212 said:**
> try:

```
sudo nautilus
```

You should use gksu for graphical apps, sudo is only for command-line stuff.

Sounds like your Nautilus is indeed pretty broken Penguinlord. Since you've only just installed I suspect you've got a corrupted file somewhere. Try reinstalling the package nautilus from System > Admin > Synaptic Package Manager.

---

### Post by Penguinlord on 2009-10-06
I have fixed it, 
I didn't think it would work, but all I had to do was update everything and restart the computer.
Thank you all though.:)

---

