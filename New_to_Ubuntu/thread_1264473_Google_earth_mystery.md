---
title: "Google earth mystery"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by nnjond on 2009-09-12
Hi,
It seems  synaptic has allowed me to dl Google earth but i cant find it's icon on any menu? What's gone wrong?

---

### Post by philinux on 2009-09-12
> **nnjond said:**
> Hi,
It seems  synaptic has allowed me to dl Google earth but i cant find it's icon on any menu? What's gone wrong?

It should appear in Applications >Internet.
Try running it from a terminal to make sure it's installed

```
googleearth
```

---

### Post by nnjond on 2009-09-12
Thanks for your help. It's not under apps. What is the terminal command?

---

### Post by philinux on 2009-09-12
Applications>accessories>terminal

Type in googleearth and hit the enter key. If it's not installed then use
```

sudo apt-get install googleearth
```

---

### Post by nnjond on 2009-09-12
nnjond@nnjond-desktop:~$ sudo apt-get install googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package googleearth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package googleearth has no installation candidate
nnjond@nnjond-desktop:~$ 

???

---

### Post by philinux on 2009-09-12
Unless you've already added the medibuntu repos to your sources list then see below.


Click the medibuntu link below and follow the instruction there. Best to copy and paste these commands. Once done you will be able to install it. 

Install it via add/remove or synaptic as the is a graphical EULA to accept.

---

### Post by nnjond on 2009-09-12
Thanks for your help. I have followed your advice. removed and re-installed googleearth package in symnaptic, but my situation hasn't changed?

---

### Post by philinux on 2009-09-12
What does the terminal say when you try to run it.

```
googleearth
```

---

### Post by nnjond on 2009-09-12
nnjond@nnjond-desktop:~$ googleearth
bash: googleearth: command not found
nnjond@nnjond-desktop:~$ sudo googleearth
[sudo] password for nnjond: 
sudo: googleearth: command not found
nnjond@nnjond-desktop:~$

---

### Post by sdowney717 on 2009-09-12
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

you can get it here

are you sure it is installed?

---

### Post by tacantara on 2009-09-12
When I installed Google Earth, it went to the Applications > Internet folder.  Check there (if you haven't already).  Otherwise, the only thing I can suggest is opening a terminal and type the following ```
 googleearth
``` to start the program.  You may see this message when you attempt to run the program via terminal:

```
 Unable to create prefs directory '/home/xxxxxx/.googleearth'. File exists.
```This is not a problem.  Just wait a few more seconds and you will see the Google Earth splash screen, followed by the program's main dialog box.

---

### Post by nnjond on 2009-09-12
I'n not at al sure its installed- and i dont know how to if synaptic didn't do it for me

---

### Post by tacantara on 2009-09-12
In Synaptic, installed packages are marked with a green box to the left of the package name.  If the package isn't installed, mark it for installation by clicking on the box and select "mark for installation".  When you're ready to install, click the Apply (green check mark) button at the top of the Synaptic dialog box, and follow the instructions (at this point, all you should get is info boxes on the status of the install).

---

### Post by nnjond on 2009-09-12
googleearth package is marked green

---

### Post by tacantara on 2009-09-12
> **nnjond said:**
> googleearth package is marked green

Then it's safe to say that the package is installed.

Try running the program again from the terminal, or reboot your computer and see if the program icon appears in your Applications > Internet menu.  If either or both of those solutions doesn't fix the problem, uninstall Google Earth by opening a terminal and typing ```
 sudo apt-get remove googleearth
```, then try reinstalling the program through the terminal by typing ```
 sudo apt-get install googleearth
```

---

### Post by nnjond on 2009-09-12
Solved. Thanks alot

---

