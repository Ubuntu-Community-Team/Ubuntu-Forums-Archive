---
title: "[SOLVED] VLC controls during fullscreen are gone"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-12-17
Last week when I played a video in fullscreen mode using VLC, the controls would show up from the bottom of the screen whenever I moved my mouse, and then disappear after couple seconds of non-movements.  This feature is gone all of a sudden.  How can I get these controls back?  Thank you.

---

### Post by halitech on 2008-12-17
right click somewhere and you will get the control menu to pop up

---

### Post by FAMUgolfer on 2008-12-17
Thank you for the quick reply.  

I know I can always right-click, but I'm lazy and would like to just move the cursor around.  Before when I did this a nice little box would appear at the bottom of the screen allowing me to play, pause, skip, etc.

How can I get that magic little box back? Thank you.

---

### Post by halitech on 2008-12-17
never noticed that in mine before but I'll take a look and see if I can find any option that looks similar. do you remember clicking on anything that might have closed that option?

---

### Post by mc4man on 2008-12-17
Tools -> preferences -> interface type -> show a controller....

---

### Post by FAMUgolfer on 2008-12-17
Nope. It's strange.  I have never messed around with any of VLC settings, they are all default.  I also don't remember being any significant update to VLC since last week either.  Go figure.

---

### Post by FAMUgolfer on 2008-12-17
Tools -> preferences -> interface type -> show a controller.... 

That's also checked, but that doesn't seem to help either.

---

### Post by halitech on 2008-12-17
just played around with mine and I don't see anything to give a toolbar type controller at the bottom of mine either. Maybe there was an update and you missed it

---

### Post by mc4man on 2008-12-17
If your running a 0.9.x version of vlc the fullscreen controller should be available.

To reset vlc back to defaults go home folder (view -> show hidden files) -> .config and delete the vlc folder.
Then start vlc up again. (you should get the privacy and network pop up

---

### Post by redandgreen on 2008-12-17
i and shift+i toggle the interface on and off.

If you want to be even lazier, all the other keyboard shortcuts still work in fullscreen. Space to pause, N for next, P for previous, f to toggle between fullscreen and normal size, etc.

---

### Post by FAMUgolfer on 2008-12-17
> **mc4man said:**
> If your running a 0.9.x version of vlc the fullscreen controller should be available.

To reset vlc back to defaults go home folder (view -> show hidden files) -> .config and delete the vlc folder.
Then start vlc up again. (you should get the privacy and network pop up

Thank you mc4man, deleting the folder worked!!!  But why is this? Sorry for being paranoid, but does deleting this folder put me at risk? (ie security, updates, etc)

---

### Post by mc4man on 2008-12-18
> does deleting this folder put me at risk

Not at all, it's just contains 2 configuration files for vlc.
As soon as you start vlc it's recreated with the default install options.

The only thing you lose is any option changes you made in tools -> preferences, if so just redo them.

If things go 'bad' in 0.9.x it's the first thing to do.

If vlc happens to freeze up and you do a 'force quit' then also ck. in system monitor -> processes for vlc (and do a kill process on it, otherwise it _may_ not restart

---

### Post by jackmetal on 2009-01-04
Don't flame me for posting to a solved (and old thread)..  :-)

I just wanted to note that this still occurs with VLC.  I've had it happen a few times myself still.  (I suppose I need to go make a bug report).

It's resolved every time by deleting the config files (.vlc dir), but then I lose all of my changes every time.  Has anyone determined what's actually causing this yet, or should I just go ahead and check on a bug report for it (if one hasn't already been listed).

Thanks!!

---

### Post by FAMUgolfer on 2009-01-04
No worries Jackmetal.  

Maybe I'm just lucky but I don't need to delete that specific file anymore.  Doing it the first time solved it for me.  A bug report won't do any harm, so go for it.

---

### Post by jackmetal on 2009-01-04
:-)  Yeah, it's strange.  It happened to me a couple weeks ago and I tried everything to get it back, including copying my vlc config from another 'working' system.  Nothing worked, except deleting .vlc dir.  

Now it's happened to me again  Controls gone in fullscreen.  lol

---

### Post by petsanikas on 2009-01-18
Hey i had this issue after a resolution change, from 1440x900 to 1024x768. Can anyone confirm that?

---

### Post by jackmetal on 2009-01-18
Interesting.  I haven't had it occur after a resolution change, but it just seems to occur randomly with no changes at all.  It just happened to me again and I've made no changes at all.  Really strange!  I haven't been able to pin down any cause yet, but when it happens you have to remove the vlc config file (and of course lose any settings you've changed, which is a pain)..  :-)

I hope they figure out what the fix is and take care of it soon.

---

### Post by petsanikas on 2009-01-19
Well, neither I am 100% positive that it was the resolution change that caused it. Just a workaround for the prevention of settings loss... if you backup your config folder, delete it, start vlc (config is re-created) and then replace the newly created folder with the backed up one, does it revive your settings (eliminating of course the fullscreen controls issue)?

---

### Post by nightfox91 on 2009-04-04
Sorry for reviving a slightly old thread, but I came up with a sligtly better option for fixing fullscreen control woes.

In the .config/vlc/ folder there is a file called "vlc-qt-interface.conf"
If you open that file, under the section [FullScreen] change the pos line to something like "pos=@Point(100 100)"
This will move the control bar back to the 100,100 coordinate and bring it back into view. This will also maintain all of your other settings. Make sure vlc is closed before you edit the file, otherwise the change may not take effect.

---

### Post by krisniiran on 2009-04-27
@petsanikas the same thing happened to me. I went from something like 1920x1200 to 1280x1024 (my monitor went out on me), I think that the fullscreen controls are still there they just sit somewhere so low on the screen that they're actually off the screen. I guess in the settings they try to sit at a specific pixel location and when I lowered the resolution it lost that location. But deleting the settings folder in %appdata% worked so it's all good.

---

### Post by GNUbee40 on 2009-05-04
Hey Guys!

Interesting thread.
My fullscreen controls appeared in Intrepid, but have vanished with the upgrade to Jaunty. None of your tricks here have effect.
I read on the VLC forum, it might have something to do with the video not beeing integrated in the interface - a feature which has been disabled because in the latest versions of VLC because of Bugs in the QT4 interface (no idea what that is).

---

### Post by svivian on 2009-05-06
@GNUbee40: Yes I have this problem too in Jaunty. I've tried every setting I can find but no fullscreen controls. Looks like it's not going to be possible...

---

