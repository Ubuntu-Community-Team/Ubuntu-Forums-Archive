---
title: "Automatic updates issue in Hardy"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Glw8z on 2008-12-07
Ubuntu keeps searching for updates every day even though I've disabled that task. It's totally meaningless on a box that's pretty much always offline.

Anyway, I've gone to Software Sources, there to the Updates tab and removed the check mark from "Check for updates". Previously I had there check for them weekly, but it still did that every single day ](*,).

I've got a screenshot of it just to show you I should've done it right. (Right?)

What am I supposed to do to prevent those useless daily searches for updates, updatedb.mlocate always kicking in (visible in System monitor) even if it's disabled here?

Is this a bug of some sort, or what's causing this? 

This can't be related to wireless issues b/c there's only an Ethernet card for my infrequent online use.

Is there something I'm missing here? And is there a remedy available? I don't want my system to be hyperactive, just to do what it's told and otherwise keep quiet and don't make a scene. 

And it's not like I'm neglecting the updates b/c the box in question's not online at all, and if I ever connect to the web w/ that one, I always check for updates manually. 

I'd appreciate some helpful tips.

---

### Post by cdtech on 2008-12-07
You may need to check your roots crontab:
```
sudo crontab -e
```
It may be listed there. Just comment it out if it is.

Just a thought......

---

### Post by Glw8z on 2008-12-07
I tried that command, but it says "no crontab for root - using an empty one", and obviously, there's nothing there.

---

### Post by HotShotDJ on 2008-12-07
System --> Preferences --> Sessions
Under the "Startup Programs" tab, find "Update Notifier"
Click on the check box to deselect it.
(I recommend that you NOT remove it, just uncheck it)
Click close.

---

### Post by Glw8z on 2008-12-08
> **HotShotDJ said:**
> System --> Preferences --> Sessions
Under the "Startup Programs" tab, find "Update Notifier"
Click on the check box to deselect it.
(I recommend that you NOT remove it, just uncheck it)
Click close.

Thanks a lot. This did it for me. I'd seen it there before, but didn't realize it also had to be unchecked. Anyway, now Hardy's no longer having ants in her pants. Problem solved. :D

---

### Post by Glw8z on 2008-12-12
No, no, no. I was too quick to celebrate. This unwanted update search has been continuing anyway. No check mark there in the Startup programs, nothing in Software Sources to encourage Hardy to check for updates, but it does it all the same. :mad: What's left to check? Is this time for a bug report? Or does anybody care about Hardy's glitches anymore? Should I just tolerate this quirkiness of behavior or can I feed something to the ADHD patient of mine?

---

### Post by SamNSane on 2008-12-12
Have you looked on the Current Session tab in the Sessions application? Is update notifier still running in there? Unchecking it in the Startup Programs tab, AFAIK, doesn't turn it off in the current session, so unless you've rebooted...

Of course, if you have rebooted, then I'm all wet.

---

### Post by Glw8z on 2008-12-13
> **SamNSane said:**
> Have you looked on the Current Session tab in the Sessions application? Is update notifier still running in there? Unchecking it in the Startup Programs tab, AFAIK, doesn't turn it off in the current session, so unless you've rebooted...

Of course, if you have rebooted, then I'm all wet.

I have rebooted several times since that first time when it appeared to work (i.e. kept quiet like instructed). And it does that check once a day, persistently. I don't know, maybe I just have to grin and bear it. Maybe this constitutes a bug, cos it's sure bugging me. I haven't felt like making an upgrade, cos everything's all set in that system and the LTS is running.

---

### Post by SamNSane on 2008-12-13
What happens if you remove the checkmarks in the upper part of that dialog? (From the wording of the dialog, I wouldn't think it would be necessary. But who knows?)

If even that doesn't work, I'd try removing the software sources from the Ubuntu software and third party software tabs. If it has no place to look, maybe it stops looking.

---

### Post by Glw8z on 2008-12-14
There are no check marks anymore. The update notifier shouldn't be activated. 

I didn't remove the software sources there (yet), cos I wouldn't wanna mess with the whole updates system, i.e. that those updates still work when I connect the box to the web and do a manual check. What I did do as a further experiment was go to the Services settings and there deselected two Action schedulers (anacron and atd). At least yesterday, that move appeared to calm the system, but I guess time will only tell if this has any impact on the update issue. I just don't know what de-activating anacron and atd really does, what else they control and determine.

---

### Post by OrangeCrate on 2008-12-14
Honestly, I'm really having a problem understanding this. If you've turned off the daily updates, and you've unchecked the update daemon in your session start up list, it's not checking for updates.

If your computer is still chugging occasionally, it might be the tracker indexing service updating it's files. And yes, you can go to tracker in Preferences, and uncheck the box to allow the service, and then uncheck any listing for tracker/trackerd in Sessions.

However, instead of worrying about what's happening in the background, why don't you just let your operating system just do it's thing?

If you want an absolutely quiet box, though I've never tried it myself, I suppose you could do an Ubuntu minimal install, and roll your own version, including features you want, and excluding those you don't.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by SamNSane on 2008-12-14
> **Glw8z said:**
> There are no check marks anymore. The update notifier shouldn't be activated. 

I didn't remove the software sources there (yet), cos I wouldn't wanna mess with the whole updates system, i.e. that those updates still work when I connect the box to the web and do a manual check. What I did do as a further experiment was go to the Services settings and there deselected two Action schedulers (anacron and atd). At least yesterday, that move appeared to calm the system, but I guess time will only tell if this has any impact on the update issue. I just don't know what de-activating anacron and atd really does, what else they control and determine.

Oh, I really only meant to uncheck the sources on the first two tabs, not to remove them in the sense of going into the configuration file and deleting them.

But you're right. You shouldn't have to go to either extreme.

Concerning killing the scheduler services I'm no familiar enough with Linux or Ubuntu yet to know whether or not there might be unwanted consequences. The only obvious, end-user-apparent scheduled operations I've noticed so far would be the update checks and the file system check that occurs after xx number of boots. However, I doubt that the latter has anything to do with the scheduler itself, unless the scheduler presets it to happen during the previous desktop session.

---

### Post by Glw8z on 2008-12-14
> **OrangeCrate said:**
> Honestly, **I'm really having a problem understanding this**. If you've turned off the daily updates, and you've unchecked the update daemon in your session start up list, it's not checking for updates.

If your computer is still chugging occasionally, it might be the tracker indexing service updating it's files. And yes, you can go to tracker in Preferences, and uncheck the box to allow the service, and then uncheck any listing for tracker/trackerd in Sessions.

However, instead of worrying about what's happening in the background, why don't you just let your operating system just do it's thing?

If you want an absolutely quiet box, though I've never tried it myself, I suppose you could do an Ubuntu minimal install, and roll your own version, including features you want, and excluding those you don't.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

It is checking, or what does updatedb.mlocate do then? I always hear the box getting into gear a couple of minutes after I've logged in and then in System monitor that updatedb.mlocate coming on. Nothing else there in active processes besides the said gnome-system-monitor and xorg, which doesn't cause the same grinding.

It can't be Tracker, since it's not on that system. 

And this is not "normal" behavior, what Hardy **should** be doing, since I've disabled the checking as it's totally useless. The OS isn't "doing its thing". It's acting when it shouldn't. It did the same every day even when the checking was enabled, but when I'd selected the weekly check option in the Software Sources.

And I'm not keen on a new install, since I've already got everything I need (not much anyway) on that old 800MHz box that doesn't need the extra workload. 

Anyway, since I unchecked those Actions schedulers anacron and atd in Services settings yesterday, I haven't heard that update check kick in. I'm now in a wait-and-see mode, not counting my herons before they're hatched.

---

### Post by MountainX on 2009-08-18
> **Glw8z said:**
> what does updatedb.mlocate do then? 

It indexes your hard disks. It has nothing to do with the Ubuntu updates.

---

