---
title: "Lost desktop icons, controls"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by kbrittt on 2011-05-01
I recently upgraded to 11.04  and had tried to enable desktop cube through Compiz,,,,I've lost all my desktop controls, no icons and I don't know keyboard commands to bring these back

---

### Post by sffvba[e0rt on 2011-05-01
> **kbrittt said:**
> I recently upgraded to 11.04  and had tried to enable desktop cube through Compiz,,,,I've lost all my desktop controls, no icons and I don't know keyboard commands to bring these back

Hi,

Ok, the answer you seek seems to be in the post below mine... so you can ignore my initial post:

>  [I][SIZE=1]Not sure this will fix the issue, but could you press Ctrl+Alt+t and in the terminal that will open run sudo unity --replace.

(This is as much for my own learning as your benefit [/SIZE][SIZE=1]:) )[/SIZE][/I] 



404

---

### Post by atul1412 on 2011-05-01
i had also lost my menu, icons and everything....
when i tried this my Problem got Solved.
 
You will need to reset compiz and unity settings. Switch to a text terminal by pressing Ctrl+Alt+F1. Login there, and issue the following commands.
Code:
gconftool-2 --recursive-unset /apps/compiz-1unity --reset
You better reboot now
Code:
sudo reboot now
and Unity should now launch properly when the system is ready again.
 
Hope it will work wid u also..
GOD BLESS !!!

---

### Post by kbrittt on 2011-05-01
tried using the gconf  command line and maybe I'm missing spaces where they should be or inserting them where they shouldn't be I keep getting "command not found" or something to that nature.  Working fromk one laptop to another so I don't have the copy/paste option

---

### Post by sffvba[e0rt on 2011-05-01
> **kbrittt said:**
> tried using the gconf  command line and maybe I'm missing spaces where they should be or inserting them where they shouldn't be I keep getting "command not found" or something to that nature.  Working fromk one laptop to another so I don't have the copy/paste option

Have you tried running just "gconftool-2" in terminal? (Just to check it is there...)

If it works, then I will replace all of the spaces with asteriks (*) for you below:

gconftool-2*--recursive-unset*/apps/compiz-1unity*--reset


404

---

### Post by kbrittt on 2011-05-01
i tried using the command line "gconftool-2*--recursive-unset*/apps/compiz-1unity*--reset"  and get a message  "unknown option --reset      ?????

---

### Post by sffvba[e0rt on 2011-05-01
> **kbrittt said:**
> i tried using the command line "gconftool-2*--recursive-unset*/apps/compiz-1unity*--reset"  and get a message  "unknown option --reset      ?????

At home now and I don't see any --reset option for gonftool-2... try and run it without the --reset flag, then reboot and see...


404

---

### Post by Michael Dooley on 2011-05-01
Hopefully, I'm not hi-jacking this thread. After updating yesterday, I have yet to see a unity desktop.

```
gconftool-2 --recursive-unset /apps/compiz-1unity
``` 

I tried running the command above without the (space)--reset at the end and I still get an empty 11.04 desktop upon rebooting - just the desktop background and a single icon left over from the 10.10 desktop. No panels, no launcher bar to the left, nada. Other options at the log-in stage work, why doesn't this one?

Any help would be appreciated. Thanks...

I'm going to continue Googling this problem.

---

### Post by Michael Dooley on 2011-05-01
I found a solution in another thread.

[http://ubuntuforums.org/showthread.php?t=1743747]("http://ubuntuforums.org/showthread.php?t=1743747")

Ctrl+Alt+F1 to get to a terminal.

```
unity --reset
```

Ctrl+Alt+F7 to get back to the desktop. At first, I didn't see a change, but after wiggling the mouse, the launcher and top panel displayed.

The issue is solved for me.

Upon rebooting, I got the empty desktop again. 

There must be a way to save the desktop settings - as a matter of fact, I'm sure that there is. I'll see what I find and report back.

---

### Post by Michael Dooley on 2011-05-01
No way found yet to make unity load automatically. Rats!

I did test to see that my graphics supported unity by entering the below command:

```
/usr/lib/nux/unity_support_test -p
```

which got the following:

```
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV350
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```

I am through spending time on this today but would like any light that anyone could shed on my problem. I would like to avoid doing a clean install which I suspect would fix this. Oh well....

---

### Post by Michael Dooley on 2011-05-01
I did a clean install - the same result.

I'm done with this. I'm going back to my old set up for now. I'll check periodically for some kind of solution but I don't expect much for the next few days.

If I find something, I'll post back here.

Edit:

Nothing found so far that will enable my test machine to boot directly into Unity. *And* once in unity, tweaking the test system to my specifications does not always work. Things need way too much time just to get to the working stage and the launcher interface appears to be a bit half baked, imho. 

In this instance (as far as upgrades), I have decided to forgo 11.04 as being insufficient to my needs - I'll reload 10.10 or perhaps even the 10.04 LTS edition. Hopefully, 11.10, due out in the fall, will be a more fully formed successor and not need as much work to install and configure.

---

### Post by frigginjoe on 2011-05-01
I dropped a launcher on my desktop for /usr/bin.ccsm so I can get back to the config utility which will refresh at least my launchbar on the left, but I'm just losing the launcher and/or toolbar to blankness or graphical corruption too much to actually get work done.

I do like Unity, for the most part, but I find myself having to tend to the issues a bit too often by restarting it or relogging and it's just not worth it.  For the time being, back to classic gnome for me.

---

### Post by Jored on 2011-05-14
I had exactly the same problems with the same laptop model and think it has something to do with the graphics chip and/or hardware acceleration.
I installed Unity 2D with Synaptic, rebooted and chose Unity 2D as the default desktop at the bottom of the login screen and it works perfectly.

---

### Post by wildmanne39 on 2011-05-14
> **frigginjoe said:**
> I dropped a launcher on my desktop for /usr/bin.ccsm so I can get back to the config utility which will refresh at least my launchbar on the left, but I'm just losing the launcher and/or toolbar to blankness or graphical corruption too much to actually get work done.

I do like Unity, for the most part, but I find myself having to tend to the issues a bit too often by restarting it or relogging and it's just not worth it.  For the time being, back to classic gnome for me.

Hi, many people including myself had this happen to them by changing settings in compiz, and typing unity --reset in the terminal by bringing it up with with alt f2 or ctrl alt +t fixed the problem. You have to give this a few minutes to run once you issue the command, at least 3 minutes then reboot and it should have returned unity back to normal. On the log in screen at the bottom make sure you have clicked on it to log in to unity. I am sorry that you are having so much trouble with this issue, I hope this helps. :)

---

