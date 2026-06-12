---
title: "Broken internet, minimal install, MSI U180"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by verymadpip on 2015-08-02
Hi everybody.
I'm trying a minimal install on a MSI U180 netbook with the intention of giving the Razorqt DE a bit of a spin.

I finally got the base OS installed today after some repo mirror issues - neither of the options offered to me worked yesterday.
I restarted the box & tried to do an update, at which point everything kinda fell over.
None of the repos in my sources list will resolve & I'm left unable to update the system or install any software.

I've tried with a wired connection & there's no change.
I've edited my sources.list to remove the "gb" part of the lines - no change.  (I'm now putting them back).

My Xubuntu machine uses the same repos & seems fine.

I'm at a bit of a loss & any ideas would be gratefully received.

---

### Post by dino99 on 2015-08-02
check that the meta package (ubuntu-desktop, or the related one) is installed
be sure you are not trying to update from the cd source
check the logs to find something usefull
try a > sudo dpkg -configure --a 

---

### Post by verymadpip on 2015-08-02
Wow!
That command tells me error: unknown option -o
That seems messed up.
I also think I've a network issue.

I've nothing installed thus far besides the basic CLI system.

---

### Post by steeldriver on 2015-08-02
Do you actually have a working internet connection / DNS resolution? can you ping the gateway by numeric IP? can you ping any external host e.g. 8.8.4.4 by IP? what about by hostname e.g. google.com? That would be a good place to start.

---

### Post by verymadpip on 2015-08-02
Alrightey then...
First of all, my network is broken,
That seems like the first thing to fix...

---

### Post by Bucky Ball on 2015-08-02
> **verymadpip said:**
>  First of all, my network is broken,
That seems like the first thing to fix...

Yes, it does, and therefore:

*Thread moved to **Networking & Wireless**.*

I have also taken the liberty of changing your thread title to increase your chances of support (you can change it to something else by editing the post and hitting 'Go Advanced'). ;)

Your broken internet would be why your repos are throwing errors. Once you are online, if you haven't changed the original repos that were installed by the minimal, you possibly won't have a problem with anything and can go ahead and install RazorQT, but run these commands before installing anything.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

PS: Do Not go fiddling around with the sources.list. That would have nothing to do with it and you won't know for sure until you're online. You may cause more problems by tweaking about in a file without knowing if that is the cause, which I'm fairly certain it isn't. Change anything you've tweaked back to what it was originally in sources.list.

---

### Post by praseodym on 2015-08-02
> Wow!
That command tells me error: unknown option -o
That seems messed up.
I also think I've a network issue.

I've nothing installed thus far besides the basic CLI system. 
It is a small A, not a small O

---

### Post by verymadpip on 2015-08-02
I think I'm just gonna start from scratch.
Goodness only knows what I've broken up to now hacking around in there...
I shall return if the problems persist.

---

### Post by Bucky Ball on 2015-08-03
> **verymadpip said:**
> I think I'm just gonna start from scratch.
Goodness only knows what I've broken up to now hacking around in there...


Hehe. I know that feeling! :)

It sound like you will have issues with the wireless so, once installed and at square one, the blinking login cursor, keep the cable in and install whatever you are going to. Reboot to a desktop and we'll see what we can do. You'll need to have a cable connection to install, and also makes things much easier to fix wireless. 

What you could do is post the output of:

```
sudo lshw -C network
```

... so we have an idea of what card you have in there. You could plug a cable in and we'll see how we go from here, but a re-install would put you back at square one and you'll know no extraneous tweaking is confusing the issue. Good luck. As far as I'm concerned, the minimal is worth the effort. :)

PS: One note: if you are intending on installing *buntu-desktop once you have the minimal installed, I wouldn't bother with the minimal. If you, for instance, intend to install 'xubuntu-desktop', that is pretty much the same as installing Xubuntu. May as well just install that to start ...

---

### Post by verymadpip on 2015-08-03
sudo lshw -C network yields:
A bunch of stuff, the pertinent bit being:
Qualcomm Atheros AR9285

I find it a little odd that the wireless connection worked during the install & then bombed out on me on the reboot.
Nevermind, I'll go with wired during the install.  (Ugh, thinking in text...)

My plan is to go minimal plus razorqt, just to see what the fuss is about.  If there is any fuss...
Although I quite like the whole WM with added bits notion.

---

### Post by verymadpip on 2015-08-03
Hi everybody - quick update:
Install went well on a wired connection, after which I installed razorqt, wicd-gtk & some other bits, & all is well with the world :)
...well, with the U180 anyway ;)

I've currently got 3 network icons in the panel, but what the heck, I'll fine tune later.

ETA:  down to 2 icons.  It's a system tray thing I think.
Overall this is a win in my book.

---

### Post by Bucky Ball on 2015-08-03
Excellent news and well done. Mini installs rock. That sounds like it would be pretty zippy and boot in no time. Enjoy. ;)

---

