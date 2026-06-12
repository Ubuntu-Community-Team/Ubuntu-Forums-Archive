---
title: "SWScanner not running/have to use root?"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by acidblue on 2007-03-27
I installed SWScanner from syanaptic, and it put two icons on my 'interne't menu.
one regular and one ' as root'.
My problem is i can run the regular one but it won't scan cause i need root
permissions to that.
So i try to usr the 'as root' one but i get an error:
 Failed to execute child process "kdesu" (No such file or directory)
I don't know what kdesu is, is it sudo for kde?
what ever it is how do i install it, did search for it in sysnaptic with no
results.

please help i'm stumped!

Oh yes i did try it from command line "sudo SWScanner'
but that didn't wotk either...'command not found'

---

### Post by Floppyjoe on 2007-03-27
SWScanner is a KDE program and you need to have Kubuntu desktop installed to run that program or the base for Kubuntu anyway.

---

### Post by acidblue on 2007-03-28
Thanks....
Guess i'll look for a gnome app scanner----though i have 
Kwifimanager installed and seems to work fine
just dosn't find any networks but my own.
Kismet finds dozens

---

### Post by A*p on 2007-04-22
You can edit the launcher to use the Gnome root launcher.  Just change the **kdesu** with **gksu** so that it becomes **gksu swscanner %f**

---

