---
title: "Removing Python"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-07-12
I was trying to find out what ```
sudo apt-get autoremove 
``` does and I tried on python. Know, a lot of gnome depends on python and luckily I stopped it midway. But, I'm still missing the gnome file browser and a lot of things. How can I get these back without reinstalling Ubuntu? How can I reinstall gnome?

---

### Post by rockerphil on 2009-07-12
the first thing that pops to mind for me would be to run 

```
sudo apt-get install ubuntu-desktop
```

that normally installs everything that Gnome carries. hope this helps,

Phil

---

### Post by kpkeerthi on 2009-07-13
```
man apt-get
```

---

### Post by Poincare101 on 2009-07-13
> **rockerphil said:**
> the first thing that pops to mind for me would be to run 

```
sudo apt-get install ubuntu-desktop
```

that normally installs everything that Gnome carries. hope this helps,

Phil
It did install well but know I have a new problem. The computer comes out of shutdown, and I log in. But, then the screen is just grey and despite me moving the mouse for 5 minutes it just stays grey and the desktop or anything doesn't appear. What should I do?

---

### Post by DustyMP on 2009-07-13
Try this. When your login screen appears press ctrl+alt+F1. This lets you access a terminal only version of your system. At the prompt enter your username. Next enter your password. Let's make sure gnome installed correctly by entering:

```
 sudo apt-get install -f gnome 
```

If there are any broken dependencies or anything the -f switch will attempt to fix them. When it's all said and done and you're back to the prompt enter:

```
 logout 
```

This should take you back to the login screen you're used to seeing. Try logging in again.

---

### Post by Poincare101 on 2009-07-13
Nope. Still not working :(

---

### Post by DustyMP on 2009-07-13
Ok, you mentioned before you tried autoremove on python and halted halfway through, so follow the same process as before and after you log into the terminal enter:

```
 sudo apt-get install -f python 
```

Then logout and try again.

---

### Post by Poincare101 on 2009-07-13
When I used that command, it doesn't install anything and i'm back in the same position after I log out.

---

### Post by Java Geek on 2009-07-13
Maybe your issue is when you install, your internet is not working so it cant download it. If you are running on wireless, try a direct link to your modem and try again.

---

