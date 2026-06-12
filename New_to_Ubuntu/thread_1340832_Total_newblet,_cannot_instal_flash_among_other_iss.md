---
title: "Total newblet, cannot instal flash among other issues"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by xcrimsonlegendx on 2009-11-29
Okay, I was forced to try out Linux due to an expired copy of XP and I'm totally lost.
I can't get flash to install at all and it's getting rather frustrating...

It keeps saying that it's not available with my hardware architecture and what not.
(didn't realize every site on the interwebs needed flash these days O_o)

Second, I was trying to get this "AMSN" thing to get my chat on and that won't work either.

Lastly, it feels like everything is too big on my screen.
On Windows I had maximized my desktop space and now everything looks huge and 
it's beginning to make my brain hurt.
That and things seem stretched out vertically...
A 100x100 pixel image shouldn't be a rectangle.

So, there you have it.
My newb-rant about Linux, help if you dare.

:popcorn:

EDIT: I'm not the greatest at mega techno-jargan so take it easy on me.

---

### Post by jrrader on 2009-11-29
for flash, open up terminal (alt+f2 then type gnome-terminal) and type

```
sudo apt-get install flashplugin-nonfree
```

press enter then enter your password.

You can find flashplugin-nonfree in synaptic if you don't want to type in terminal.

---

### Post by ad_267 on 2009-11-29
You should probably read this about how to install software in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It will probably help with your flash and aMSN troubles. You could also try emesene rather than aMSN. You will probably want to install the ubuntu-restricted-extras package. That will install flash, mp3 codecs and other useful stuff that can't be included in Ubuntu by default for legal reasons.

---

### Post by xcrimsonlegendx on 2009-11-29
> **jrrader said:**
> for flash, open up terminal (alt+f2 then type gnome-terminal) and type

```
sudo apt-get install flashplugin-nonfree
```press enter then enter your password.

You can find flashplugin-nonfree in synaptic if you don't want to type in terminal.It said it couldn't find it.

---

### Post by xcrimsonlegendx on 2009-11-29
> **ad_267 said:**
> You should probably read this about how to install software in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

It will probably help with your flash and aMSN troubles. You could also try emesene rather than aMSN. You will probably want to install the ubuntu-restricted-extras package. That will install flash, mp3 codecs and other useful stuff that can't be included in Ubuntu by default for legal reasons.I found the restricted package thing but like Amsn it says "not available in the current data" or something of that nature.
:(

---

### Post by ikt on 2009-11-29
> **xcrimsonlegendx said:**
> It said it couldn't find it.

System > Admin > Software Sources

Is the first 4 boxs ticked? (main, universe, restricted, multiverse)

---

### Post by xcrimsonlegendx on 2009-11-29
> **ikt said:**
> System > Admin > Software Sources

Is the first 4 boxs ticked? (main, universe, restricted, multiverse)
Yes, they are.

---

### Post by ikt on 2009-11-29
> **xcrimsonlegendx said:**
> Yes, they are.

You don't see this?

[IMG]http://dl.dropbox.com/u/2161836/pictures/synaptic.png[/IMG]

---

### Post by xcrimsonlegendx on 2009-11-29
I found that and searched for flashplugin-nonfree but it didn't come up with that.
Sorry, feeling rather frustrated at this point.
Probably not thinking clearly.

---

### Post by jrrader on 2009-11-29
hmmm, have you ran your first update yet?  That is generally the first thing that should be done after installing (alt+f2 "update-manager").  Usually it pops up on it's own a few minutes after you first log in.

---

### Post by xcrimsonlegendx on 2009-11-29
> **jrrader said:**
> hmmm, have you ran your first update yet?  That is generally the first thing that should be done after installing (alt+f2 "update-manager").  Usually it pops up on it's own a few minutes after you first log in.Nope, nobody suggested that thus far.
-does so-

---

### Post by jrrader on 2009-11-29
How about your screen resolution.  Have you tried system preferences display to change your screen resolution?  I'm hoping you don't have to mess with xorg to get things displayed right. What monitor are you using?

---

### Post by ad_267 on 2009-11-29
For the screen problem, check if you have any drivers available from System - Administration - Hardware Drivers. Depending on what video card you have there may be a driver listed there that you can install.

---

### Post by xcrimsonlegendx on 2009-11-29
> **jrrader said:**
> How about your screen resolution.  Have you tried system preferences display to change your screen resolution?  I'm hoping you don't have to mess with xorg to get things displayed right. What monitor are you using?
I did mess with all the display settings but nothing seems to do it.
Everything looks big and stuff.

I did mess with the monitor to make it not stretched vertically.
I just mashed things down but now I have black bars on the top of the screen.

The monitor I'm using is an old HP one I swiped from an old compy.

---

### Post by jrrader on 2009-11-29
check system > administration > hardware drivers as mentioned above.  My HP monitor will not display correctly without the nvidia drivers selected there.

---

### Post by xcrimsonlegendx on 2009-11-29
> **ad_267 said:**
> For the screen problem, check if you have any drivers available from System - Administration - Hardware Drivers. Depending on what video card you have there may be a driver listed there that you can install.I found some hardware drivers for my nvidia card but when I try to active them it says "SystemError: Failed to lock /var/cache/apt/archives/lock"

---

### Post by jrrader on 2009-11-29
That's because update is running (it is running, right?).  You'll have to wait until it's done.

---

### Post by xcrimsonlegendx on 2009-11-29
After the update I just followed the onscreen directions to install flash and it worked without issue...

I don't get why that update never popped up before now.

Now I'll retry some of the suggestions from before to fix the other issues.

---

### Post by xcrimsonlegendx on 2009-11-29
I got amsn to work as well, now to try to fix my screen settings.
Thanks to everyone who's trying to help me make this transition as easy as possible.

---

### Post by jrrader on 2009-11-29
Well, welcome to Linux.  We all start out this way.

---

### Post by xcrimsonlegendx on 2009-11-29
n_n

Now to figure out if my programs and stuff are compatible...
I got this xbox memory card transfer kit thing but I don't think it is.
I can't seem to find it.

---

### Post by jrrader on 2009-11-29
You should probably click on thread tools at the top of this and select "mark thread as solved" and then start a new thread somewhere (maybe in the gaming forum, I'm not really sure) for the xbox card.

---

