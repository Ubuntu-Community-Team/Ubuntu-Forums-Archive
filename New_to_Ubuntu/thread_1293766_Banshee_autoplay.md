---
title: "Banshee autoplay"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-10-17
In banshee 1.4 the terminal command ```
banshee --hide
```didnt work, it was a listed bug that was supposed to be fixed for 1.5.1, the problem is that this command works but ```
banshee --play
``` doesnt, i cant find anything googling about it.  Anyone using banshee 1.5.1 that can confirm, is this a bug?? I basically want banshee to load up in the background and start playing music when i log in, heres the terminal output. ```
mark@mark-desktop:~$ banshee --hide --play
[Info  18:16:47.806] Running Banshee 1.5.1: [Ubuntu 9.04 (linux-gnu, i486) @ 2009-10-15 02:49:59 UTC]

(Banshee:13548): Gtk-WARNING **: Theme directory  of theme Azenis Red Icons has no size field

[Info  18:16:48.806] All services are started 0.80776s

(Banshee:13548): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
[Info  18:16:49.481] nereid Client Started

```

EDIT: i also tried $banshee --hide && banshee --play
just in case but the same thing happened

---

### Post by CaptainMark on 2009-10-19
Sorry to bump! 
Does no one know whats up with this

---

### Post by braete on 2009-10-19
heh, didnt knew about --play option for it :oops:

either way it doesnt work for me either

banshee --play/stop/... works only after banshee is already started

banshee && sleep x && banshee --play also doesnt work

edit: workaround O_o
i did a play.sh file, chmod +x it (sleep 5 && banshee --play) and i added it in the start up applications then i added a second entry with banshee --hide.
(noobish solution, but it gets the job done ;) )

---

### Post by CaptainMark on 2009-10-21
sounds good to me, is this a bash script, i dont know anything about them. Can you recommend a good place to learn how to use them???

---

### Post by CaptainMark on 2009-10-22
Right im really gonna throw a spanner in the works now, ive looked up some basics about bash scripts and bumbled my through to this point. I have a file /home/mark/.scripts/play.sh, here is its cat output```
mark@mark-desktop:~$ cat /home/mark/.scripts/play.sh 
#!/bin/bash
sleep 15 && banshee --play
mark@mark-desktop:~$
```i have run the command chmod u+x /home/mark/.scripts/play.sh
and i have added two lines to the startup applications list, 1. banshee --hide   2. /home/mark/.scripts/play.sh

Now who wants to take up the challenge and riddle me this??
Why does this not do want i want it to when i turn on my computer, but it does work if i logout and then login again???
Its driving me up the wall now.

---

### Post by HarrisonNapper on 2009-10-22
> **CaptainMark said:**
> Right im really gonna throw a spanner in the works now, ive looked up some basics about bash scripts and bumbled my through to this point. I have a file /home/mark/.scripts/play.sh, here is its cat output```
mark@mark-desktop:~$ cat /home/mark/.scripts/play.sh 
#!/bin/bash
sleep 15 && banshee --play
mark@mark-desktop:~$
```i have run the command chmod u+x /home/mark/.scripts/play.sh
and i have added two lines to the startup applications list, 1. banshee --hide   2. /home/mark/.scripts/play.sh

Now who wants to take up the challenge and riddle me this??
Why does this not do want i want it to when i turn on my computer, but it does work if i logout and then login again???
Its driving me up the wall now.

That is exactly right, you want banshee to start in hide mode at startup and then autoplay 15 seconds after startup. 15 seconds might be a little too long (it's longer than you think), most I've used is 10 and I use that for things like conky that I have to launch after compiz starts. When you log out and log back in, X is already initialized. Something you might try doing is having banshee --hide sleep for a second or two. That would be my only guess. You could probably just add it to the same script and call it .banshee_startup or something like that.

Cheers.

---

### Post by CaptainMark on 2009-10-22
fifteen seconds is a good time because the default login sound for ubuntu is quite long, thats no problem, if its because X is not initialised how can i make sure that happens first, youll have to forgive me if im being dumb, i dont fully understand what X is, im still trying to get my head round that, 
the weird thing is if i have banshee --hide and banshee --play they wont work in the same terminal, so they wont work in the same script, i think thats a banshee bug? anyway banshee --hide work fine but not the script for banshee --play.
I even tried making a plain script to sleep a bit then run another script that plays banshee. 
okay im waffling, ill stop now, any thoughts?

---

### Post by HarrisonNapper on 2009-10-22
> **CaptainMark said:**
> fifteen seconds is a good time because the default login sound for ubuntu is quite long, thats no problem, if its because X is not initialised how can i make sure that happens first, youll have to forgive me if im being dumb, i dont fully understand what X is, im still trying to get my head round that, 
the weird thing is if i have banshee --hide and banshee --play they wont work in the same terminal, so they wont work in the same script, i think thats a banshee bug? anyway banshee --hide work fine but not the script for banshee --play.
I even tried making a plain script to sleep a bit then run another script that plays banshee. 
okay im waffling, ill stop now, any thoughts?

I don't have banshee personally, but my guess would be that each call to banshee calls to initialize the program which is probably why they aren't working in the same terminal window. That's why I qualified adding them to the same script with probably. You could probably see how to call the --play function without calling the whole program if you take a look at the man page for banshee.

```
man banshee
```

X is the default window manager in Ubuntu. Gnome is the desktop environment and Metacity is the default manager for the GUI, but essentially if you try to launch a program like banshee before those have started, a program in command mode will ask for the graphical interface that it should use, resulting in the program "not starting". My understanding is that generally both X and Gnome will automatically start before anything else, but I've had this issue with other programs like tomboy and conky even before I was using it with compiz. Read the man page and if that doesn't help, try sleep 5&&banshee --hide in a script and see if it works.

---

### Post by J3RI3L on 2011-05-19
> **CaptainMark said:**
> In banshee 1.4 the terminal command ```
banshee --hide
```didnt work, it was a listed bug that was supposed to be fixed for 1.5.1, the problem is that this command works but ```
banshee --play
``` doesnt, i cant find anything googling about it.  Anyone using banshee 1.5.1 that can confirm, is this a bug?? I basically want banshee to load up in the background and start playing music when i log in, heres the terminal output. ```
mark@mark-desktop:~$ banshee --hide --play
[Info  18:16:47.806] Running Banshee 1.5.1: [Ubuntu 9.04 (linux-gnu, i486) @ 2009-10-15 02:49:59 UTC]

(Banshee:13548): Gtk-WARNING **: Theme directory  of theme Azenis Red Icons has no size field

[Info  18:16:48.806] All services are started 0.80776s

(Banshee:13548): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
[Info  18:16:49.481] nereid Client Started

```

EDIT: i also tried $banshee --hide && banshee --play
just in case but the same thing happened

Try this (It Works for me).

Go to Startup Aplications and Add this 2 comands:
_See Picture Attached_

1- To Start Banshee minimized

**bash -c "_sleep 15_; banshee --hide" &&**

2- To have Banshee Autoplay
**bash -c "_sleep 20_; banshee --play"** && (Set the delay to 20 or something else to allow banshee to startup correctly from the first command)


THAT WORKS SMOOTHLY FOR ME, HOPE FOR YOU TOO!

---

