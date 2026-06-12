---
title: "Cant get back to GUI"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Britmonkey on 2009-03-27
Following instructions I found elsewhere Ive managed to get my machine to boot into command line, and cant get it back to booting back to GUI.
The command i used was 
$echo "false" | sudo tee /etc/X11/default-display-manager

and to get it back should be 
$echo "/usr/bin/gdm" | sudo tee /etc/X11/default-display-manager

however when checking last night I didnt seem to have a /usr/bin/gdm directory or a kdm or kde one?  

Im obviously missing something stupid, but dont know what.

TIA> 

---

### Post by Britmonkey on 2009-03-27
Sorry duplicate post same as #1. I was too eager

---

### Post by markharding557 on 2009-03-27
does startx work?
and try reinstalling gdm 
> sudo apt-get --reinstall install gdm

---

### Post by iponeverything on 2009-03-27
open /etc/X11/default-display-manager with nano and remove the "false"

---

### Post by aeiah on 2009-03-27
i dont know whether you were given bad instructions or not but people do make mistakes in their howtos and whatnot sometimes. in this case it would have been useful for you to know what echo and more importantly tee do. to get the manual up for tee to give you a rough idea you simple do:
```

man tee

```

---

### Post by decoherence on 2009-03-27
This is wrong on Ubuntu:

```
$echo "/usr/bin/gdm" | sudo tee /etc/X11/default-display-manager
```

Ubuntu keeps GDM in /usr/sbin, not /usr/bin, so you might have better luck with

```
$echo "/usr/sbin/gdm" | sudo tee /etc/X11/default-display-manager
```

For future reference, you can find out where a command lives using the 'which' command, ie

```
which gdm
```

prints out /usr/sbin/gdm

Likely the directions you were following were for a distro that keeps gdm in /usr/bin.

---

