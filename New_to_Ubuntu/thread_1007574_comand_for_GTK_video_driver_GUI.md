---
title: "comand for GTK video driver GUI?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by klemperal on 2008-12-10
For the life of me I can't remember this command.  I remember it worked for Hardy and from within the program you could select from various video drivers for your card.  Please let me know if you know the command.

---

### Post by SuperSonic4 on 2008-12-10
EnvyNG-gtk I believe

---

### Post by klemperal on 2008-12-10
No, that's not it.  The program was included with Ubuntu.  It could have been the graphical front end of xserver.xorg.

---

### Post by Michael.Godawski on 2008-12-10
```
sudo dpkg-reconfigure xserver-xorg --frontend=gnome
```

---

### Post by igknighted on 2008-12-10
> **Michael.Godawski said:**
> ```
sudo dpkg-reconfigure xserver-xorg --frontend=gnome
```

But... this will not work in intrepid (8.10) due to a change in the way X is configured.  To reconfigure you now need to go a TTY and switch init runlevel 1 (or reboot to recovery mode or whatever they call it now) and run select xfix.

Is there anything in particular you are trying to change/fix that we could help with?  The original request is, well, rather cryptic and doesn't make much sense.  If you elaborate on what you are trying to do we could point you in the right direction.

---

### Post by klemperal on 2008-12-10
Ok, here is a picture of what I'm trying to run.  Unfortunately the article where this pic came from didn't include the name of the program or its command.

[IMG]http://files.fosswire.com/2007/08/displayconfiggtkdriver.png[/IMG]

[IMG]http://files.fosswire.com/2007/08/displayconfiggtk.png[/IMG]

---

### Post by roger_1960 on 2008-12-10
Hi

Thats displayconfig-gtk

Its not included after Hardy - I believe there is a loged bug that there is no GUI for resolution/display configuration in Intrepid yet!

---

### Post by klemperal on 2008-12-10
Dang.  Alright, thanks everyone for the effort.

---

### Post by Michael.Godawski on 2008-12-10
yep see here:
[https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/286998](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/286998)

It will be replaces with x-kit:
[https://edge.launchpad.net/x-kit](https://edge.launchpad.net/x-kit)

---

