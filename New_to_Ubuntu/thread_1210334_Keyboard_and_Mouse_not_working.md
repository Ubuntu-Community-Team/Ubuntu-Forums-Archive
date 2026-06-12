---
title: "Keyboard and Mouse not working"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Shadowking on 2009-07-11
Hi all....need some help.

I had a problem with my ubuntu shutting down automatically after reaching a critical temperature. I tried to change this setting by following the advice on these links. (please don't tell me that my computer is dirty...it's not!)

1. [http://burnz.wordpress.com/2009/02/23/ubuntu-auto-shutdown-due-to-high-cpu-temperature/](http://burnz.wordpress.com/2009/02/23/ubuntu-auto-shutdown-due-to-high-cpu-temperature/) (Didn't work)

2. [http://ubuntuforums.org/showthread.php?t=539365](http://ubuntuforums.org/showthread.php?t=539365) (Maybe working, haven't been able to login)

When the advice on the first link didn't work, I tried the second one. When I restarted the computer, the mouse and keyboard wouldn't work. The login screen is there, but I can't type my username or password cos my keyboard was not working. Would appreciate any help.

I have an IBM Thinkpad R40, Intel pentium centrino.

Thanks,
Shadowking

---

### Post by LewRockwell on 2009-07-11
[http://www-307.ibm.com/pc/support/site.wss/MIGR-45916.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-45916.html)

does it work when you use the LiveCD or LiveTD?

---

### Post by LewRockwell on 2009-07-11
I checked out the links you included in your first post

Looks like you might have a problem with your /etc/modules if that was the last modification you completed

If you remember what you did then you can use the LiveCD to go into the file and change it back

```
gksudo gedit /etc/modules
```

.

---

### Post by Shadowking on 2009-07-11
> **LewRockwell said:**
> I checked out the links you included in your first post

Looks like you might have a problem with your /etc/modules if that was the last modification you completed

If you remember what you did then you can use the LiveCD to go into the file and change it back

```
gksudo gedit /etc/modules
```.

Thanks for the suggestion. Live CD works. So, u think it is the modules file that could be causing it? Any idea which specific change? I could undo all changes, but I also want to fix my CPU over-heating problem at the same time.

---

### Post by LewRockwell on 2009-07-11
> **Shadowking said:**
> Thanks for the suggestion. Live CD works. So, u think it is the modules file that could be causing it? Any idea which specific change? I could undo all changes, but I also want to fix my CPU over-heating problem at the same time.

that thread was old and even the OP stated that newer kernels had outdated his advice

I understand that the over-heating is an issue for MANY people but what might have worked for a previous kernel doesn't necessarily work moving on to the next one

my advice to others is "when in doubt...re-install" that way you are always working from the same starting point(here is where a back-up drive containing a clone of your freshly installed and freshly/fully updated partition/drive works wonders)

it doesn't hurt to make notes for yourself as you go along either

bread crumbs placed along the path prevent cold nights alone in the forest...

.

---

### Post by Shadowking on 2009-07-12
> **LewRockwell said:**
> that thread was old and even the OP stated that newer kernels had outdated his advice

I understand that the over-heating is an issue for MANY people but what might have worked for a previous kernel doesn't necessarily work moving on to the next one

my advice to others is "when in doubt...re-install" that way you are always working from the same starting point(here is where a back-up drive containing a clone of your freshly installed and freshly/fully updated partition/drive works wonders)

it doesn't hurt to make notes for yourself as you go along either

bread crumbs placed along the path prevent cold nights alone in the forest...

.
I undid the changes, but still no love. Keyboard and mouse still don't work (I can see the red laser in the mouse though). They still work on XP and live CD. Re-installation is not an option for me...sorry. I just spent too much time editing so many files and customizing my ubuntu that I'm not going to do it again. I would appreciate any other suggestion.

---

### Post by Hobgoblin on 2009-07-12
> **Shadowking said:**
> I undid the changes, but still no love. Keyboard and mouse still don't work (I can see the red laser in the mouse though).

So it's an external mouse, not the trackpad?  Is it an external keyboard?  If so does the internal keyboard work?  Does the trackpad work?

Which version of Ubuntu are you using?

---

### Post by Shadowking on 2009-07-12
> **Hobgoblin said:**
> So it's an external mouse, not the trackpad?  Is it an external keyboard?  If so does the internal keyboard work?  Does the trackpad work?

Which version of Ubuntu are you using?
Touchpad and trackpointer don't work. 
Laptop internal keyboard doesn't work. (I don't have an external keyboard to try). 
I have tried all the obvious solutions in my resources such as disconnecting and reconnecting the mouse etc....

I'm using Ubuntu 9.04 Jaunty Jackalope and am pretty sure it's a software issue.

---

### Post by Shadowking on 2009-07-14
Does Ubuntu have a repair function? Maybe I can repair it and still keep my custom settings.

---

