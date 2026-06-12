---
title: "I uninstalled gnome and screwed things up."
date: 2009-05-14
forum: New to Ubuntu
---

### Post by xeticus on 2009-05-14
I started with kubuntu 9.04 and installed gnome to give it a try. I decided I liked KDE better and then decided to uninstall gnome. It seems I went too far. I lost a of programs but I was able to get vlc, amarok and brasero installed easily. I was able to use sudo to reinstall synaptic package manager. I lost a couple of things though. I lost the icons for several programs including pidgin, firefox and synaptic. In my k launcher next to synaptic there was a another package manager that just said add/remove applications. That's gone also. And when I open my email there and would open an attached file whatever was the the default program for that is gone also. How can i get my icons, package manager and default picture viewer back please. And please don't ask my why I want that package manager back when I have synaptic. I liked it and want it back is all. Thanks!!!

---

### Post by xeticus on 2009-05-14
No answers? :(

---

### Post by Happy_Man on 2009-05-14
Run ```
sudo aptitude install kubuntu-desktop
``` That should get your kubuntu system back.

Whenever pidgin, firefox, etc. update, the icon will come back automagically.

---

### Post by xeticus on 2009-05-14
I tried sudo apt-get install kubuntu-desktop before and that didn't work. Trying aptitude now.

---

### Post by xeticus on 2009-05-14
nope I tried it. It definitely installed some packages. I logged out and logged back in and nothing changed.

---

### Post by Dr.Vista on 2009-05-14
> **xeticus said:**
> nope I tried it. It definitely installed some packages. I logged out and logged back in and nothing changed.
Try this.
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by xeticus on 2009-05-14
> **Dr.Vista said:**
> Try this.
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)That's how I got into this position in the first place. I used the command line they had there but ommitted the install kubuntu portions at the end. I thought in my noobishness that I was happy with my kde so didn't
need to install it again.

---

### Post by Dr.Vista on 2009-05-14
> **xeticus said:**
> That's how I got into this position in the first place. I used the command line they had there but ommitted the install kubuntu portions at the end. I thought in my noobishness that I was happy with my kde so didn't
need to install it again.
That command should work. It will reinstall KDE and remove all GNOME's programs.

Edit:I know what happened. When you unistalled Ubuntu-desktop it disinstalled all the programs the come shipped with it. You'll have to install them again because when you ran the command it was notified that Pidgin, Firefox, etc programs to be removed.

---

### Post by xeticus on 2009-05-14
> **Dr.Vista said:**
> That command should work. It will reinstall KDE and remove all GNOME's programs.

Edit:I know what happened. When you unistalled Ubuntu-desktop it disinstalled all the programs the come shipped with it. You'll have to install them again because when you ran the command it was notified that Pidgin, Firefox, etc programs to be removed.
Yup and i installed most of them already. I don't know how to install that one default package manager as i don't know it's name. It didn't appear to be Synaptic or kpackage as I installed those. Also I still have no icons for a lot of the programs. just question marks. And I still have no clue on what to do so I can open up pictures in my email.

---

### Post by nothingspecial on 2009-05-15
```
sudo apt-get install gnome-app-install eog
```

That should get Add/Remove and your image viewer back.

---

### Post by xeticus on 2009-05-29
> **nothingspecial said:**
> ```
sudo apt-get install gnome-app-install eog
```That should get Add/Remove and your image viewer back.Thanks very much. It got my package manager back. You are my hero!!!

---

### Post by nothingspecial on 2009-05-29
No problem :D

---

