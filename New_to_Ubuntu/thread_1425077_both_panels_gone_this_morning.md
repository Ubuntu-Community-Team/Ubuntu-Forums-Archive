---
title: "both panels gone this morning"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Michael Dooley on 2010-03-08
Jaunty 9.04

I recently (a few weeks ago) upgraded from 8.04 to 8.10 and then to 9.04 on my main machine. The upgrade process seemed to go smoothly but I noticed that there was an extra window manager added in Fusion Icon.

Last night, after I opened a file manager named Dolphin, my k9copy gui seemed to not display correctly. I finished all my work and shutdown the machine. This morning, upon booting to 9.04, there were no panels at all and there were two instances of sysmonitor (a screenlet) running. I created a launcher for xterm by right clicking on the desktop and started up the panels by typing "gnome-panel" and pressing enter. However, I got the following warning(s):

```
(gnome-panel):3105: libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
```

Google was no help there. Plus some other warning about 

```
*No GLX_EXT_texture_from_pixmap with direct rendering context ... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
* Using the GTK Interface
```

I used apt-get to remove dolphin - no help there.

I reinstalled 9.04 but only the / files, leaving the home partition untouched. And by the way, I did not format the / partition.

After renaming .gconfig to .gconfig.old and then using apt-get to first remove the ubuntu desktop and then re-install it, rebooting, no fix, I'm stumped. I'd like to avoid doing a fresh install but I'm preparing for that eventuality by backing up my /home partition while I'm waiting for a knowledgeable suggestion.

Thank you all for taking the time to read this. I'll gladly give more details if needed.

---

### Post by Sir Jasper on 2010-03-08
Hi,

You might try copying and pasting your error message/(s) in the google search box. That has sometimes worked for me.

My regards

---

### Post by Michael Dooley on 2010-03-08
Thanks Sir Jasper.

It sometimes works for me too.

So far no luck in getting this fixed.

---

### Post by MichealH on 2010-03-08
> **Michael Dooley said:**
> Thanks Sir Jasper.

It sometimes works for me too.

So far no luck in getting this fixed.

I am quoting what I just said in another post... with the same issue

> ** MichealH said:**
> [QUOTE=Maxcore;8936120]Oh cool. All my panels are gone though, so is there a way to create new ones from the command line?

> **Maxcore said:**
> Wow, I just realized that this really sucks. I don't know how to launch any of my applications without using the menu bar. I tried creating a launcher on my desktop to "bash" but nothing happens when I run it. I also tried creating a launching to gnome-panel but nothing happened when I ran that as well. What should I do?

ALT+F2
Type in:
```
gnome-terminal
```
Then do what NightwishFan said :D

Which was:
> **NightwishFan said:**
> Run this in the terminal.
```
gconftool2 --recursive-unset /apps/panel
```[/QUOTE]

---

### Post by Michael Dooley on 2010-03-08
I'll get back to you on that MichealH just as soon as I save my stuff to a flash drive. My last total back up was almost a month ago.

So it goes...

Thanks for the suggestion.

---

### Post by MichealH on 2010-03-08
> **Michael Dooley said:**
> I'll get back to you on that MichealH just as soon as I save my stuff to a flash drive. My last total back up was almost a month ago.

So it bgoes...

Thanks for the suggestion.

No worries I might not reply soon... Have to get my beauty sleep!

---

### Post by Michael Dooley on 2010-03-08
Pressing Alt-F2 while at the panelless desktop gets nothing. I think this may be significant. Using the xterm launcher gets a command line box and when I type in

```
gconftool2 --recursive-unset /apps/panel
```

I get

```
-bash: gconftool2: command not found
```

Also I get the same response when using Ctrl-Alt-F! at log-in screen.

Thanks for the suggestion mate.

---

### Post by MichealH on 2010-03-08
There is another way but It includes rm -rf so be careful!

If you want It will be easier click CTRL+ALT+F1 and You will see a terminal Login with your username and Password If you are not comforatable you can do It annother way get the Terminal you just used back up and enter this command either way will restore your pannels and wallpaper back:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Oh, I will be gone for 9 hours or so...

---

### Post by Michael Dooley on 2010-03-08
Thanks MichealH, I'll be trying this shortly. 

I think I've already removed these items before except for .metacity. And I was doing some nice stuff with that, enabling desktop effects with no restricted drivers. I'll let you know how it goes.

Thanks again.

---

### Post by Michael Dooley on 2010-03-08
Rats!

It didn't work to restore my panels. I used the above command both in xterm and at the log-in window using Ctrl-Alt-F1. No joy either way.

I'm going to step outside for a few minutes and see the real world. If upon returning to the forums (and this small room), I can't find an answer to my problem, I'll do a fresh install, reinstall most of what I had and copy the data bck into the new installation.

But not for at least 90 minutes, if then. 

I want to solve this, not cover it over.

Thanks MichealH.

---

### Post by lidex on 2010-03-08
Is this kubuntu?

---

### Post by Michael Dooley on 2010-03-08
No, this problem involves Ubuntu and Gnome. However, since I use a few Kubuntu native programs, k9copy comes to mind, I thought it might have something to do with discovering Dolphin in my applications (I had never intentionally downloaded it) and opening it last night. 

Maybe setting some Dolphin preference screwed up my panel settings or something else in Gnome. I don't know. I used apt-get to remove dolphin however. If that makes any difference.

Thanks for your interest. I'm going to look at this with a different slant and see if I can come up with some kind of fix - other than starting gnome-panel with a terminal every time I boot.

---

### Post by Michael Dooley on 2010-03-08
Right now I'm performing a clean install of Jaunty. 

After trying a variety of solutions offered both on the forums and on the internet, I'm just a little worn down. Thank g_d it isn't a re-install of W--X-, that's all I can say. 

Thank you all for your help.

---

### Post by lidex on 2010-03-08
> **Michael Dooley said:**
> Right now I'm performing a clean install of Jaunty. 

After trying a variety of solutions offered both on the forums and on the internet, I'm just a little worn down. Thank g_d it isn't a re-install of W--X-, that's all I can say. 

Thank you all for your help.

Sorry, I was waiting for your answer - wanted to make sure was a gnome issue - to post this:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Michael Dooley on 2010-03-09
Thanks lidex, I tried those commands too. I'm now posting from the new installation and will post a follow-up in a week or so. Right off the bat, I suspect that my old install was loaded with cruft of various sorts. I did a lot of stuff in 8.04 and was quite satisfied to stay with 8.04 until I noticed that my other machines (that were running newer Ubuntu releases) seemed to be fine. 9.10 being the exception...

I looked at my partitions with gparted and the / partition in the new install is much, much less packed with whatever was living there - bits and bites I suppose. 

But I'll report back once I get all the VMs and such up and running.

Thanks for your help lidex. See you around the forums.

---

### Post by MichealH on 2010-03-09
](*,)Man, I forgot to tell you to pkill gnome-panel shows how tired I was :P

---

### Post by Michael Dooley on 2010-03-09
Late nights tend to produce the same results in me too. I'll post back here in about a week. Thanks MichealH.

---

### Post by Michael Dooley on 2010-03-12
My problems probably started long before I got the missing panels situation. I decided in March of 2009 to create a seperate /home partion and move my home to it. Please see [this thread]("http://ubuntuforums.org/showthread.php?t=1104354") for the details of my adventure.

The last picture I took of my partitions before the missing panels showed the / filesystem taking up 19.51 Gigabytes of space. As far as I know, that's a bit too much. In contrast, my re-installed 9.04 / filesystem, after all (or at least most) of my software was re-installed, occupies 4.47 Gigabytes of space. As far as I know from cruising the forums regularly, it seems to be unusual for / to need more than a 10 Gig partition. Please correct me if my conclusion is incorrect.

So after a bit of work reinstalling on one machine, I synchronized my various installations, all being dual boot at the minimum and kind of tidied up things.

I don't know what *exactly* bolloxed the panels, but my suspicions are that I had several /homes in / although I never saw more than one. My other suspicion involves something I know next to nothing about, - .GVFS seemed to be much larger than either / or /home. What the heck is the gnome virtual file system anyway? Why was mine so large?

Maybe one of these days I'll find out what I did while messing with copying my home to a seperate /home partition. If you have any ideas about that, please don't hesitate to let me know.

Thanks...

---

### Post by MichealH on 2010-03-13
> **Michael Dooley said:**
> My problems probably started long before I got the missing panels situation. I decided in March of 2009 to create a seperate /home partion and move my home to it. Please see [this thread]("http://ubuntuforums.org/showthread.php?t=1104354") for the details of my adventure.

The last picture I took of my partitions before the missing panels showed the / filesystem taking up 19.51 Gigabytes of space. As far as I know, that's a bit too much. In contrast, my re-installed 9.04 / filesystem, after all (or at least most) of my software was re-installed, occupies 4.47 Gigabytes of space. As far as I know from cruising the forums regularly, it seems to be unusual for / to need more than a 10 Gig partition. Please correct me if my conclusion is incorrect.

So after a bit of work reinstalling on one machine, I synchronized my various installations, all being dual boot at the minimum and kind of tidied up things.

I don't know what *exactly* bolloxed the panels, but my suspicions are that I had several /homes in / although I never saw more than one. My other suspicion involves something I know next to nothing about, - .GVFS seemed to be much larger than either / or /home. What the heck is the gnome virtual file system anyway? Why was mine so large?

Maybe one of these days I'll find out what I did while messing with copying my home to a seperate /home partition. If you have any ideas about that, please don't hesitate to let me know.

Thanks...

Ahh Well, I had the same problem weirdly 1 day ago... but in Karmic i just used

```
killall gnome-panel
```

And It started again and I had them!

---

