---
title: "how do I modify xorg.conf?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by techteam on 2010-01-14
I'd like to modify my computer so that it will work correctly, if you may know how please help.
Or point out a step-by-step procedure on how to do so if you know of any.

---

### Post by bkratz on 2010-01-14
I think you might want to include more information--like what is wrong

---

### Post by klock on 2010-01-14
More information regarding exactly what you would like to do is required as stated above.

Are you having problems with your video setup? Is it not displaying the correct resolution? 

As stated in your message header, you were inquiring about your xorg.conf

To modify this file:

-open gnome terminal or any other terminal program you have installed
-navigate to /etc/X11 [cd /etc/X11]
-- at this point you should be using the sudo command to be able to perform the functions from now own.
-make a backup copy of your current xorg.conf [sudo cp ./xorg.conf ./xorg.backup.conf]
- open your xorg.conf in a text editor, vi, nano, whatever
[sudo nano -w xorg.conf]

At this point you will be able to make the required changes to your xorg, following documentation available elsewhere on these forums and on the internet. 

If you have any more trouble, please reply to this thread.

---

### Post by snowpine on 2010-01-14
Ubuntu no longer uses xorg.conf by default... maybe you are following an old tutorial for an older release?

If you could give more details on the problem...

---

### Post by gabo.cr on 2010-01-14
> -open gnome terminal or any other terminal program you have installed
-navigate to /etc/X11 [cd /etc/X11]
-- at this point you should be using the sudo command to be able to perform the functions from now own.
-make a backup copy of your current xorg.conf [sudo cp ./xorg.conf ./xorg.backup.conf]
- open your xorg.conf in a text editor, vi, nano, whatever
[sudo nano -w xorg.conf]

I don't think that will work in Karmic, but I don't know what the OP has.

---

### Post by audiomick on 2010-01-14
> **gabo.cr said:**
> I don't think that will work in Karmic, but I don't know what the OP has.

As far as the process of editing goes, yes it should. Did it on mine just the other week, although with
```
gksu gedit
```
and not with nano.

The question is, if there is an xorg.conf there at all, and it there is, if editing it will change what the OP wants.

---

### Post by bkratz on 2010-01-14
My Karmic did not have one--I had to create it first before editing.

---

### Post by gabo.cr on 2010-01-14
> The question is, if there is an xorg.conf there at all, and it there is, if editing it will change what the OP wants.

That is very interesting...
I didn't have the xorg.conf file, and many people don't either.
I had to create my own xorg.conf file.
I wonder if it's related to the video card on installation.
:-k

---

### Post by audiomick on 2010-01-14
> **gabo.cr said:**
> That is very interesting...
I didn't have the xorg.conf file, and many people don't either.
I had to create my own xorg.conf file.
I wonder if it's related to the video card on installation.
:-k

Not the video card.
Ubuntu is moving on. Things like xrandr (I think that is the right name) are being used to set up stuff that used to be a matter for xorg.conf.

The state of things is that an xorg.conf isn't necessarily needed anymore, but will be read if it is there. As far as I can tell, the nVidia drivers need them. I have one that was created by nvidia-settings, but that might also be only because I have two monitors. Maybe with a basic setup it wouldn't have needed it.

Also, the "input device" sections that used to be necessary for keyboard and mouse are commented out (not from me) with the comment
> # commented out by update-manager, HAL is now used

---

