---
title: "Scripting questions"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by ooknmoo on 2009-04-25
I installed UNR on my Acer One everything is running.. what im trying to figure out is i want a couple 3rd party applications and when I download them they have directions on the notepad doc say extract, and run script. So I assume they mean in root terminal. So I unlocked terminal (which took me forever) and log in as root, got terminal to open and it says something about SUDO so i type sudo and the script line.. but that doesnt do anything. So my question is this... can someone give me an example of how to run a script and when you do.. does it make it possible to run the program scripted auto? and how do you make an icon and permanent link to run the program on the main screen for it. I apoligze in advance to the experienced people who are just reading this shaking thier heads...

---

### Post by ooknmoo on 2009-04-25
also i keep seeing.. "do this in a terminal window" is their more than one terminal aside from root terminal? and do i have to switch to root login everytime to run a script cause thats quite tedious...

---

### Post by eilios on 2009-04-25
If you're using root terminal ignore the sudo.

---

### Post by ddnev45 on 2009-04-25
> **ooknmoo said:**
> I installed UNR on my Acer One everything is running.. what im trying to figure out is i want a couple 3rd party applications and when I download them they have directions on the notepad doc say extract, and run script. So I assume they mean in root terminal. So I unlocked terminal (which took me forever) and log in as root, got terminal to open and it says something about SUDO so i type sudo and the script line.. but that doesnt do anything. So my question is this... can someone give me an example of how to run a script and when you do.. does it make it possible to run the program scripted auto? and how do you make an icon and permanent link to run the program on the main screen for it. I apoligze in advance to the experienced people who are just reading this shaking thier heads...

to run as root in a terminal:

```
$ sudo <script>
```

and the script will run after you enter your password.

in a root terminal:

```
# <script>
```

Remember that commands in Linux are case sensitive.

Are you using Gnome? If so, you can right click on the desktop and select the "create launcher" option (screenshot) from the menu to place an icon on your desktop; the "create launcher" dialogue box is fairly intuitive.

If you're new to Ubuntu you can take a look at the [Beginners Guide]("http://ubuntuforums.org/showthread.php?t=1052065").

---

