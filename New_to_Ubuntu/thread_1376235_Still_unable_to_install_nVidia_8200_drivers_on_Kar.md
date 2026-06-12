---
title: "Still unable to install nVidia 8200 drivers on Karmic"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by JoJerome on 2010-01-08
Graphics running slow and choppy in all programs.

Following the instructions in [this thread,]("http://ubuntuforums.org/showthread.php?t=1322398&highlight=geforce+8200m") I'm still having the following issues:

When I try to install the nVidia drivers I downloaded from their site, I get an error message that I'm still running X server and need to exit. I've closed all programs and did ctrl+alt+f1, which I thought exits X but apparently doesn't. 

Also, 

sudo /etc/init.d/gdm stop

tells me command not found.

Help? Thanks!

---

### Post by JoJerome on 2010-01-09
Actually, I think I got it.

sudo start kdm

Peering into my init and init.d files, I guessed that kdm is just this install's version of gdm? Anyway, took a chance, ran the command, and victory instead of OS death. 

Scary, but ... victory is mine!
:popcorn:

---

### Post by markjensen on 2010-01-09
I guess you can confirm which version of the driver you tried downloading from the nvidia site.  Also, are you running the 32-bit version of Karmic?

You might be able to do an
**sudo apt-get install nvidia-kernel-common** to get all that you need.

EDIT:  Nevermind.  :)

Yes, kdm does the same as gdm.  gdm is the login/display manager for gnome systems, and kdm is the one for KDE systems (though any of them will work regardless of what desktop you use).

---

### Post by JoJerome on 2010-01-10
Thank you Mark. I'm having a number of other issues now which might just drive me to wipe and re-install. If I do, I'll try the nvidia drivers your way.

---

