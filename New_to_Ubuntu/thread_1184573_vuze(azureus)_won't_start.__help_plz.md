---
title: "vuze(azureus) won't start.  help plz"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by enri2 on 2009-06-11
installed azureus and it doesn't start, nothing happens when I click it. any ideas.

---

### Post by zeroseven0183 on 2009-06-11
How did you install it?

---

### Post by TeoBigusGeekus on 2009-06-11
Type vuze (or azureus) in command line and see if you get any error messages.

---

### Post by reeseslover531 on 2009-06-11
make sure you have java as well.

---

### Post by enri2 on 2009-06-11
installed the latest version (.deb)  vuze starts  but can't update . it tells me that the folder  user/share/vuze is not writable.... how do i fix this???

---

### Post by zeroseven0183 on 2009-06-11
Reinstall the application. Try doing it Add/Remove... or through the Terminal by typing

```
sudo apt-get install vuze
```

Or you may change the permission of the folder by opening Nautilus as root

```
sudo nautilus
```

---

### Post by superprash2003 on 2009-06-12
run the application in the terminal and try

---

### Post by Joe Eye on 2010-05-10
> **superprash2003 said:**
> run the application in the terminal and try

I had the exact same issue in Lucid. When I tried to run Vuze from the terminal I got the following error

[INDENT][warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
[/INDENT]I found the solution at [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/543366](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/543366), which involved navigating to the directory and creating the missing swt link with 

[INDENT]sudo ln -s swt-gtk-3.5.1.jar swt.jar
[/INDENT]Worked like a charm for me.

---

### Post by z987k on 2010-05-15
> **Joe Eye said:**
> I had the exact same issue in Lucid. When I tried to run Vuze from the terminal I got the following error

[INDENT][warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
[/INDENT]I found the solution at [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/543366](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/543366), which involved navigating to the directory and creating the missing swt link with 

[INDENT]sudo ln -s swt-gtk-3.5.1.jar swt.jar
[/INDENT]Worked like a charm for me.

Great find!  10.04 broke vuze or the new version of vuze broke itself.  Either way, I'd be willing to bet a lot of people are having this problem.

---

### Post by StarWarrior on 2010-05-16
reinstalling the package libswt-gtk-3.5-java 
also solved this issue for me.

got it from here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568940](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568940)

---

