---
title: "Gnome clock stops"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by expatCM on 2009-08-27
I have noticed that when I play a clip from say youtube that the clock in the system tray stops as soon as I press play.  It will only then restart when I reboot.

Has anyone seen this event or found the fix?

---

### Post by fatality_uk on 2009-08-28
Woah. Odd one!!!!
I am guessing flash related, cause / effect. Visited adobe and see if same happens?

---

### Post by Gribok on 2009-08-28
Can you check if it's just the clock that stops, or does the entire top bar get frozen?  To be more specific, do you you have any other applets that may display some information that no longer display properly, for example the weather applet or the NetworkManager applet?

If this is the same thing as what I'm experiencing, I believe that it's not related to Flash, but something to do with the video drivers.  I'm experiencing this problem when I plug in a projector and extend my desktop to it.  The entire top bar no longer displays any updates, like the seconds on the clock.

Sometimes I can get it back by removing the second monitor, and sometimes not.  Just now it happened again, and after removing the projector it did not come back.  I was able to fix it without rebooting by changing my resolution to something else, and then changing it back.

In case this is hardware related, I'm having this problem on a Dell Latitude D620 with a Quadro NVS 110M card, using the NVIDIA accelerated graphics driver ver. 180, making changes using the Nvidia utility, obviously running 9.04.

I haven't spent much time searching in the forums, but wanted to reply to this post since it's so recent.

---

### Post by expatCM on 2009-08-30
I have been trying to replicate this and have not been able to do so.  Yet.

I have been on youtube twice today but on both occasions the clock did not stop.  So I am trying to work out what I did.  Perhaps the clock stopped just prior to using youtube but that sounds to be a bit strange.

What is clear is that the clock has stopped twice now and on both occasions I was watching youtube but why I cannot replicate this again today is not clear to me.

I will post again when I can replicate the event.

---

### Post by expatCM on 2009-09-04
Clock stopped again this morning.   Booted up the machine and saw that there were updates waiting ....  so I installed them.  Then moved on to Firefox and Thunderbird.  At about that time the clock stopped.

Opening Firefox and Thunderbird is a normal event.  Installing updates happens only now and again.

The menu bar was still active (weather, applications, places, system) it was only that clock that stopped.

---

### Post by expatCM on 2009-09-18
There seems to be some correlation with the Update Manager.  The clock stopped again today after logon.  There were updates available.  Update Manager reported that it could not get an exclusive lock and install the updates (no idea why since no other repository related event was running) and the clock stopped.

Everything else is working ....

---

### Post by expatCM on 2009-09-24
I have recorded what happened in the log file the last two times the clock stopped.  This is what I saw

```
Sep 22 08:24:41 machine sudo: pam_sm_authenticate: Called 
Sep 22 08:24:41 machine sudo: pam_sm_authenticate: username = [user] 
Sep 22 08:24:41 machine sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 


Sep 24 08:41:18 machine sudo: pam_sm_authenticate: Called 
Sep 24 08:41:18 machine sudo: pam_sm_authenticate: username = [user] 
Sep 24 08:41:18 machine sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 

```

It seems to be the same event.  There are no other events logged at this time (or just before or just after) and yet this is the exact time that the clock stops.

Any idea what the last line means?  I am not running any encryption at this time but I have just installed Truecrypt.

---

### Post by humphreybc on 2009-09-24
Do you live anywhere near the Large Hadron Collider?

---

### Post by expatCM on 2009-09-24
nope .....  the biggest activity here is watching the rice grow.  That really is fun.  You may want to try it ...

---

### Post by Shmalignant on 2009-10-05
I have the same problem.  Sometimes when I watch Youtube videos my entire panel stops updating.  killall gnome-panel fixes it, but its a pain in the butt.  This has been happening for about 2 weeks.

---

### Post by expatCM on 2009-10-05
You may want to take a look at your log files.  I have been doing that and I notice that 100% of the time when the clock stops there is always this line logged

```
sudo: Warning: Using default salt value (undefined in ~/.ecryptfsrc) 
```

As to what this means ...........   well google knows all about it but I have been unable to find any source that explains what it is and how to fix it in terms that I understand.

---

### Post by Shmalignant on 2009-10-06
Another etiology, at least for me could be Gnome-do.  It seems that this problem began around the same time I installed Gnome-do.  I already have bugs with Gnome-do if I add it to start-up programs (doesn't load properly and hogs cpu sometimes).  Also when watching you tube videos, if I hover over the icons on my docky the you tube video flicks.  Maybe there's a relationship between these and the panel apps not updating.

---

### Post by Derek_ on 2010-03-10
Any resolution to this?  Has a bug been filed?

---

### Post by ondre on 2010-06-04
My clock has been stopping too. It's tough to pinpoint but the only way mine starts again is with some panel activity.  For example, if I restore/minimize Liferea, the clock will catch up again after being stuck for 5-10 min.

I figured I would get around it by adding the fortune fish applet but I noticed that was stopping too, just like the clock.

Let me know what log files I can check and maybe we can pin this down.

---

### Post by asv on 2010-06-14
I'm experiencing the same issue. The Gnome-clock applet crashes constantly.

---

### Post by ondre on 2010-06-14
I gave up.
Started using Avant Window Navigator instead. 
[http://wiki.awn-project.org/](http://wiki.awn-project.org/)

Started getting to work on time.

---

### Post by smellems on 2010-08-17
I have installed Ubuntu 10.04 on 5 computers and only 1 has this problem.  Almost every time the clock will stop right after booting.  it will start again with some panel activity. sometimes the gnome-panel clock-applet will crash and I will get an error message.  does anyone know what is causing this?

---

### Post by viking350 on 2010-08-17
I suggest getting google gadgets gtk in the ubuntu software center

---

### Post by smellems on 2010-08-21
how will the google gadgets help me?  I never thought there was a problem with the clock until this installation.  thanks for your reply!

---

### Post by angel_buntu2007 on 2010-09-26
***sigh* Im having the same problem, right now is 8:20 PM here and the clock its been freezing showing 3:51:55 PM. All I can hope now is that the upcoming update to Ubuntu 10.10 fix this for once**

---

### Post by bsalem on 2010-09-27
Do you have swap set up? How much physical memory and swap do you have? If you don't have about 1 GB of main memory and a good portion of that in swap space, apps could stop or not run anymore. Look in your /var/log/messages for errors relating to the app or to swap.

---

### Post by rsansores on 2011-03-24
I have the same problem and like others comment is really hard to diagnose what actions trigger this behavior.

---

### Post by jpetit on 2011-10-11
I have the same problem: from time to time the gnome clock freezes.

---

