---
title: "Gnome and KDE"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Musick Man on 2009-12-09
Hi,

If I know my facts correctly, Gnome and KDE are two different types of graphical interfaces that you can use. I know that Ubuntu comes with Gnome installed. Is there a way that I could install and use KDE on my ubuntu 9.10 machine? 

Thanks,

Musick Man

p.s. Sorry if this doesnt make any since... I have a feeling that I am trying to explain something that is a little over my head. :o

---

### Post by Chesamo on 2009-12-09
[http://www.kubuntu.org/](http://www.kubuntu.org/)

Kubuntu is Ubuntu except with KDE instead of GNOME.

---

### Post by jbrown96 on 2009-12-09
You can install kde with ```
sudo apt-get install kubuntu-desktop
``` in a terminal (apps-->accessories). 

KDE is a graphical environment. It also comes with its own applications. There are many great ones: Amarok (music player), ktorrent (torrent app), and many others. They are really what makes KDE great. You can also install these applications without all of KDE.

KDE is really about customization. The more you like to customize, the more you will like KDE.

---

### Post by jimmy the saint on 2009-12-09
Fire up synaptic and look for kubuntu-desktop.  It will auto-select a few (a big few) packages.  I suggest synaptic over the command line for this because it may be easier for you to see what else is being installed and give you a better idea of what is happeneing.

Essentially, it is a dummy package that requires a lot of other programs to be installed (the KDE desktop environment and related apps).  Once this is done, when you start up Ubuntu, you can choose to boot into gnome or KDE by selecting the appropriate session at the login screen.

---

### Post by liamnixon on 2009-12-09
EDIT: Nevermind, others have already explained it.

---

### Post by sandyd on 2009-12-09
> **Musick Man said:**
> Hi,

If I know my facts correctly, Gnome and KDE are two different types of graphical interfaces that you can use. I know that Ubuntu comes with Gnome installed. Is there a way that I could install and use KDE on my ubuntu 9.10 machine? 

Thanks,

Musick Man

p.s. Sorry if this doesnt make any since... I have a feeling that I am trying to explain something that is a little over my head. :o
```
sudo apt-get install kubuntu-desktop
```
when you get to the login screen, choose "KDE" as your session

---

### Post by MelDJ on 2009-12-09
see: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

