---
title: "Can the black background after login but before gnome is full loaded be changed?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by diablo75 on 2009-11-23
My laptop is connected to an HDTV and I use this TV as the primary monitor; the lid on the laptop is never opened unless I have to force it to power off or something like that (rare).

This TV does a kind of "Auto Sync" whenever the screen resolution changes.  The purpose of this auto sync is to adjust horizontal/vertical placement and stretching to make the video feed fit perfectly in the screen.

Right now I have Ubuntu setup to auto-login, so it skips the login screen and goes strait from the bootsplash to the desktop.  However, when the bootsplash is replaced with the desktop, the screen resolution changes, and so the TV begins to auto sync.  Unfortunately, for the next 6 or 7 seconds, all the TV can see is the "thinking" mouse cursor overtop a solid black background and so it doesn't know where the edges of the video feed are and does a bad auto adjustment, resulting in a misaligned picture once Gnome finishes loading.  I have to grab the remote and initiate another auto-sync by hand.

This problem doesn't happen in Windows (I dual-boot) because Windows is able to get something on the screen that isn't solid black in less than one second.

So what I was wanting to do is find a setting somewhere that can change the color of the black background you see in between the boot-splash screen and final-load of the GUI.  Anyone know of a way to adjust this?

---

### Post by gackt on 2009-11-24
Hi there, 

try this: right click the desktop > change desktop background > (in background tabs) > Solid Colour > choose your colour

---

### Post by ninjapirate89 on 2009-11-24
> **gackt said:**
> Hi there, 

try this: right click the desktop > change desktop background > (in background tabs) > Solid Colour > choose your colour

I think what the OP is referring to isn't the background wallpaper, but the black screen with white ubuntu logo that is new to Karmic.

---

### Post by gackt on 2009-11-24
Yes i do understand because in ubuntu 8.10 there is screen after login before gnome and i used to change that screen colour, but if the OP means differently then i have no idea how to change it :D

---

### Post by diablo75 on 2009-11-24
> **ninjapirate89 said:**
> I think what the OP is referring to isn't the background wallpaper, but the black screen with white ubuntu logo that is new to Karmic.

Right, I'm not refering to the desktop background (aka, Wallpaper).  That is about the last thing to finally load before I can start to use the OS.  Before that happens, the background is solid black with the cursor.  The mention of this white screen new in Karmic sounds like it might do the trick but I'm going to hold off on the upgrade till the .1 updates are released.  Until then I'll be running 9.04... so if there is a setting that can be tweaked somewhere, a value that can be changed, to make the default background that is shown while the GUI is busy loading be changed, that'd be great!

And just in case anyone out there is wondering, I did attempt to change the background color within the Appearance settings manager, but it had no effect.

---

### Post by bilalakhtar on 2009-11-24
Try this link. It is related to changing the XSPLASH wallpaper. 
[http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html](http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html)
Hope this helps.:popcorn:

---

### Post by ninjapirate89 on 2009-11-24
> **bilalakhtar said:**
> Try this link. It is related to changing the XSPLASH wallpaper. 
[http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html](http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html)
Hope this helps.:popcorn:

Getting closer but I'm not sure the part the OP wants to change is the XSPLASH. He (she) wants to change the screen that shows up after the XSPLASH but before the final desktop  is loaded. AFAIK there is no way to change it.

This part:
[IMG]http://ubuntu-tutorials.com/wp-content/uploads/2009/10/ubuntu-beta-install-2.png[/IMG]

---

### Post by diablo75 on 2009-11-24
> **ninjapirate89 said:**
> Getting closer but I'm not sure the part the OP wants to change is the XSPLASH. He (she) wants to change the screen that shows up after the XSPLASH but before the final desktop  is loaded. AFAIK there is no way to change it.

This part:
[IMG]http://ubuntu-tutorials.com/wp-content/uploads/2009/10/ubuntu-beta-install-2.png[/IMG]

Something close to that.  I've never seen that little white ubuntu logo on the black background before, so I'm assuming that's part of Karmic, which I've not upgraded to yet.  And while it would be cool to change my XPLASH screen... I believe that is also a feature of Karmic, and not Jaunty.

In any case, it's not a huge deal.  Though I would think there would be a config file somewhere that has a value for what is displayed immediately after X is loaded.

---

### Post by ninjapirate89 on 2009-11-24
> **diablo75 said:**
> Something close to that.  I've never seen that little white ubuntu logo on the black background before, so I'm assuming that's part of Karmic, which I've not upgraded to yet.  And while it would be cool to change my XPLASH screen... I believe that is also a feature of Karmic, and not Jaunty.

In any case, it's not a huge deal.  Though I would think there would be a config file somewhere that has a value for what is displayed immediately after X is loaded.

If you haven't upgraded to Karmic yet then that can't be what you are seeing. It sounds like you'll just have to live with it unfortunately.

---

