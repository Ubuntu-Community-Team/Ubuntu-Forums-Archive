---
title: "getting the basics of linux down"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by originalsynthesis on 2009-01-07
ok, so i am new to linux, ive been using ubuntu studio for awhile now as an audio workstation. I freaking love it. but ive gotten tired of being stuck in gnome as a windows refugee who has no idea how to work the basics of the terminal. ive been trying out new desktop environments and window managers because i want to try getting away from gnome to save on cpu resources and really take advantage of what linux is about. the thing that i love and hate about linux is that there is simply so much...option. and with that comes an ocean of things to learn. all you ppl on the forums are extremely helpful and knowledgeable, but ive gotten to the point where i am sick of relying on the forums for basic stuff.
    like right now, im trying out xfce and enlightenment, and i need to know how to get them to auto mount (i think thats what i need) my windows partition like gnome does. i believe i need to use fstab, but i dont know what the rest of the com would be. im sure i can find it on forums somewhere, but there seems to be so many little differences from distro to distro and its hard to find an answer specific to my version (without posting the question myself)  
    so my long introduction aside, i guess what im asking is: is there a tutorial that anyone knows of that focuses on all the major terminal operations a newbie such as myself would need in their search to learn to navigate the linux ocean? or maybe some just some wisdom.  if not, that's cool too, it was good to vent some frustration at being the guy who hasn't learned to walk yet, if you know what i mean..

---

### Post by Melk79 on 2009-01-07
Something like this? [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by Paqman on 2009-01-07
> **originalsynthesis said:**
> i need to know how to get them to auto mount (i think thats what i need) my windows partition like gnome does. i believe i need to use fstab

So I take it you were mounting your Windows partition manually every time? By navigating to it and clicking on it?

The simplest thing to do is install ntfs-config (even though it's a Gnome app) as it'll get your NTFS partition set up in /etc/fstab automatically for you. After that you can switch to any desktop environment you like and it'll keep on automounting.

---

### Post by Bucky Ball on 2009-01-07
Excellent page, Melk79! Cheers.

OriginalSynthesis: Step by step and you will be running before you know it!

Off topic but my bit of wisdom. I loaded Xubuntu then installed Ubuntu Studio packages and the rt (realtime) kernel (no Studio desktop or artwork - don't like it). Works a treat and nice and speedy, keyboard shortcut for all the most used apps and couldn't be happier. That is my multimedia workstation setup (which dual-boots with Windoze running ProTools, Sibelius, Cubase etc ... don't have much choice there, especially with Sibelius and refuse to run Wine!).

Good luck and happy tweaking. Be aware that in Xubuntu there is an option to load Gnome and/or KDE dependencies (I think it is) at boot. Can't remember where it is and am on laptop. This should be switched to the negative so you are not loading them. Just trimming the fat ... :)

---

### Post by originalsynthesis on 2009-01-07
> **Melk79 said:**
> Something like this? [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

sweet. yes this is exactly what i was looking for! mucho gracias!

---

### Post by fireball1953 on 2009-01-07
I'm in the same boat with you originalsynthesis. Thanks for posting your question. I basically just said the same thing on another thread. 

and thanks to melk79 for the reply and suggestion.

Many thanks.

---

### Post by originalsynthesis on 2009-01-07
> **Paqman said:**
> So I take it you were mounting your Windows partition manually every time? By navigating to it and clicking on it?

The simplest thing to do is install ntfs-config (even though it's a Gnome app) as it'll get your NTFS partition set up in /etc/fstab automatically for you. After that you can switch to any desktop environment you like and it'll keep on automounting.

 well, with gnome i got used to it showing up automatically in my Places tab, right under the .home folder.  now, with xfce and E, it shows up as a link on my d.t. to  /freedesktop/Hal/devices/volume_uuid_906445FC6445E616 that opens up in firefox. weird, right?  
  anyway, ntfs-config worked just fine, on X and E. thnx for the suggestion.

---

### Post by Bucky Ball on 2009-01-07
The other thing you can use in Xfce is Thunar. It works like Nautilus (which is a Gnome app). If you open Thunar, go to /media then drag the partitions you want in 'Places' in to the bottom window of the left hand panel of the Thunar window, you should then find them in 'Places'.

Hope that makes sense.

---

### Post by originalsynthesis on 2009-01-07
> **Bucky Ball said:**
> 

Good luck and happy tweaking. Be aware that in Xubuntu there is an option to load Gnome and/or KDE dependencies (I think it is) at boot. Can't remember where it is and am on laptop. This should be switched to the negative so you are not loading them. Just trimming the fat ... :)
 
That was something i was gonna bring up sooner or later, actually. glad you brought it up, b/c i doubted i was using kfce alone just by installing it and logging into a new session. So does that mean I've got gnome running underneath Xubuntu, where xfce is acting just as a window manager?

---

### Post by Bucky Ball on 2009-01-07
If you attempt to use a Gnome application and it works, you must have Gnome dependencies happening somewhere. That is as long as you know the app only works with Gnome. Look for that switch which disallows Gnome and KDE at boot. I will post the location later when I am on my other machine.

Also, you can try:

```
top
```... in a terminal and keep your eye open for anything Gnome-like to check if it is running. (rather than Xfce.) It could take awhile. Is Compiz-Fusion still available? If so, then you are not just running Xfce.

---

### Post by Paqman on 2009-01-07
> **Bucky Ball said:**
> If you attempt to use a Gnome application and it works, you must have Gnome dependencies happening somewhere. Look for that switch which disallows Gnome and KDE at boot.

That won't make any difference to whether it runs or not. Regardless of whether they're loaded up at boot, any Gnome or KDE app will bring up whatever libs it needs to run when you launch it. All that setting does is prevent them from being preloaded (the idea of preloading them being to reduce the amount of time they take to start up)

This goes for running KDE apps on Gnome (or vice versa) as well. The first time you launch an app from another DE it will be quite slow to launch because it has to start up all the gubbins that would normally be running under that DE. That's why some people don't like running apps from other DEs, as it chews through a bit more memory than sticking to apps native to your desktop.

---

