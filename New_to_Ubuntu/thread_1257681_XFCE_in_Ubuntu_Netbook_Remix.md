---
title: "XFCE in Ubuntu Netbook Remix"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by arinlares on 2009-09-04
I just installed Ubuntu Netbook Remix on my Asus EEE 1000ha, and find that it is in fact not that much faster than Windows XP, that came on it.  So, I'm wondering if using XFCE, rather than GNOME would take a little bit off of the resource load.  And, would I be able to install XFCE in Ubuntu Netbook Remix and keep the alternate Netbook Remix desktop?  And most important:  Will I still be able to use the camera and microphone the same way as GNOME?  I'm still learning what exactly Ubuntu can do, and this is my first time running it on actual hardware.

I won't be able to respond this weekend, but I'll be back on Monday, since it's labor day, so don't think I ditched this thread. :D

---

### Post by kerry_s on 2009-09-04
yes, just unselect netbook-launcher & maximus in the session startup when you use xfce4.

all the unr stuff is made to run on gnome, if you want to run it in xfce4 it will take some tweaking and its not easy, i'm running maximus on debian xfce4.

---

### Post by arinlares on 2009-09-04
Do I need to worry about this if I'm already using the normal Ubuntu desktop?  Or will the processes cause a conflict?

---

### Post by kerry_s on 2009-09-04
> **arinlares said:**
> Do I need to worry about this if I'm already using the normal Ubuntu desktop?  Or will the processes cause a conflict?

nope, should be fine.

---

### Post by t0p on 2009-09-04
Install the xfce desktop and apps with the command

```
sudo apt-get install xubuntu-desktop
```

But you need to be aware of this: the netbook remix gui is a customized version of Gnome.  If you run it with xfce, you will not get the netbook remix-type desktop.  If you want to keep the customized desktop you'd need to find (or write) a customized version of xfce.  Otherwise your desktop will be the standard xfce desktop.

In my opinion, default desktops look better than the netbook remix interface.  I installed netbook remix on my EeePC but didn't like the look of it.  Now on my EeePC I've got Eeebuntu with a standard Gnome interface.  I know some people think the default desktop doesn't look so good on a netbook's small screen: but I think Gnome looks just fine on my EeePC's 7" display.  That netbook remix UI looks too childish to me.  Fisher Price's "My First Computer kind of looks.  Makes netbooks look like toys.

---

### Post by arinlares on 2009-09-04
The 9.04 netbook edition with the default Ubuntu desktop looks like the normal version, though.  I'm not using the netbook desktop, either.  I'm not a big fan of the netbook desktop either.

So, I installed it, and the top bar keeps changing from when I'm hovering over the desktop to when I hover over the bar, adding and removing System, and the emblem on the top right corner going from the XFCE mouse to a six-pointed rainbow star.  Did I do something wrong?  I'm back in GNOME for now.

---

### Post by winotree on 2009-09-04
Since **xfce** is a modular system -- you can use any of its components without installing all of them -- perhaps **xfdesktop4** would be a better choice than the entire Xubuntu desktop, no offense to **t0p**.  :D  Can you return your system to its previous state and give this a try??  If it works for you -- and I don't know why it wouldn't as I'm using it now, you could then add which modules appeal to you.  ;)

EDIT - my bad!  The xfce desktop **is** in the repositories -- use synaptic...

---

### Post by arinlares on 2009-09-07
So, I've run into a bit of a hangup.  I used apt-get install xubuntu-desktop, and can't seem to stop maximus from running when I switch sessions into XFCE.  I've even removed it from the startup applications.  Is there anything I'm missing here?  I was playing with it when I was out of town this weekend, but couldn't ask for help because I didn't have an internet connection.

---

### Post by winotree on 2009-09-07
That's rotten luck...but there was a thread with a possible solution two days ago.  It dealt with removing or at least stopping *Maximus* from working.  

EDIT - here you go [http://ubuntuforums.org/showthread.php?t=1258645&highlight=maximus+remove](http://ubuntuforums.org/showthread.php?t=1258645&highlight=maximus+remove) 

(You'd think I'd have remembered posting in it, though).  :?  ;)

---

### Post by kerry_s on 2009-09-07
> **arinlares said:**
> So, I've run into a bit of a hangup.  I used apt-get install xubuntu-desktop, and can't seem to stop maximus from running when I switch sessions into XFCE.  I've even removed it from the startup applications.  Is there anything I'm missing here?  I was playing with it when I was out of town this weekend, but couldn't ask for help because I didn't have an internet connection.

if you don't want maximus just uninstall it using synaptic.
if you want to use it i can tell you how, just let me know.

---

### Post by arinlares on 2009-09-07
I'd actually like to keep Maximus, since it's possible.  So long as no coding is required, I'd like to give it a try.  By allowing it to work for XFCE, would it still work for GNOME?

Thanks, winotree, I didn't know what it was for, but I'm not interested in removing it as of yet.  Last resort, maybe.

---

### Post by kerry_s on 2009-09-08
to use it in xfce4 you would replace xfwm4 with metacity.
you also need to create a button to close the windows.

in terminal:
**killall xfwm4**

press-> **alt+f2** (you might have to use the run from the menu, can't remember)
type-> **metacity**

for the close button you need to install a program & create a script.

**sudo apt-get install xautomation**

[B]mkdir ~/bin
mousepad ~/bin/close[/B]

put:
```
[B]#!/bin/sh
xte 'keydown Alt_L'
xte 'key F4'
xte 'keyup Alt_L'[/B]


```

make it executable:
**chmod +x ~/bin/close**

if you did it right, clicking on that file should close the current program.

log out & back in so it add's your ~/bin to the path.

now just create the launcher in your panel with "close" as the command.

it would look something like this.

---

### Post by arinlares on 2009-09-08
It didn't work.  I'm not sure why.  I installed XFCE using apt-get install xubuntu-desktop, as previously mentioned, and want to uninstall everything to do with XFCE to take it back to just GNOME, and start over.  How can I do this?  I'm stuck in this position, and can't really go forward until I do, I think.

Is Metacity a window manager for GNOME?  It's always running.  And I have somewhere around five instances of maximus running when I enter my XFCE session, as well as the taskbars switching between XFCE and what I'm assuming to be GNOME.  I'm actually thinking of reinstalling, but don't think I need to, as my GNOME session is fine.

---

### Post by kerry_s on 2009-09-08
sorry, just got up & running, switched to a 64bit install to try it out.

you can use synaptic to uninstall xfce4 & what ever programs you don't want.

yes, metacity is the gnome window manager.

once maximus is running you suppose to uncheck it from the startup. you can use the session tab to kill off the extras.

yeah, you can reinstall if you want, thats up to you.

---

### Post by arinlares on 2009-09-09
I'll just stick with GNOME for until I can actually know what I'm doing.  Thanks for your help, all, but at this point, I should just familiarize myself with Ubuntu first. :D

---

### Post by arinlares on 2009-09-15
Ok, I figured I'd post to update, I did what t0p recommended and installed xubuntu-desktop.  The problem I had was the the UNR and UME launchers.  I gave up because I thought it was too frustrating, but curiosity and boredom led me back to this thread to try again.  So, it worked, and I thank everybody for your help.  I tried the xfdesktop4 package, and realized I wouldn't know what the heck I needed to install to have a fully functioning system, so I used the xubuntu-desktop, as I mentioned earlier.

Odd thought, but should there be an entry in the community documentation?  I posted this thread because there was little or no information in existence on this topic.  I'll gladly write/test it on my computer as far as Maximus working.

---

### Post by kerry_s on 2009-09-15
> Odd thought, but should there be an entry in the community documentation? I posted this thread because there was little or no information in existence on this topic. I'll gladly write/test it on my computer as far as Maximus working.

a lot less people mix the desktops these days, they just use what works.
i'm about to add xfce4 to this gnome install, so i should be able to help you easier, since i'll kinda be in the same boat now. i'm seeing what i can get out of my old 450mhz 256mb ram laptop.

i'll give you a before & after. 
so this is gnome as i got it now with maximus, i plan to setup my xfce4 the same way.

---

### Post by kerry_s on 2009-09-15
it lives! just some fine tunning here & there. i got to try and tweak the gnome slab menu to work with xfce4. :)

here's some pics:

---

### Post by arinlares on 2009-09-15
I sure hope you know I meant submit documentation, not programming when I said write :D  It looks great, by the way.  Are the second set of screens running XFCE, or GNOME?  It's hard to tell because it looks like some lovechild between the two.

---

### Post by kerry_s on 2009-09-15
> **arinlares said:**
> I sure hope you know I meant submit documentation, not programming when I said write :D  It looks great, by the way.  Are the second set of screens running XFCE, or GNOME?  It's hard to tell because it looks like some lovechild between the two.

:lolflag: more like one of those nights you want to forget.
the second images is all xfce4, i really wanted to keep the gnome slab menu, but it kept crashing the panel, just does not want to play nice.
in fact, i really don't like how it feels at all, gnome feels like its faster after i tweaked it for low resource. i don't think i'm going to keep xfce4. :(

---

### Post by gjoellee on 2009-09-15
> **t0p said:**
> Install the xfce desktop and apps with the command

```
sudo apt-get install xubuntu-desktop
```



Installing xubuntu-desktop wont help much when it comes to performance...

For a light a faster desktop:
```
sudo apt-get install xfce4
```

---

### Post by winotree on 2009-09-15
I see you've marked this thread as solved -- hope you're happy with your results.  :)

Been fiddling with other distributions lately and* that* helped me remember what I'd done to get mine the way it is: I'd originally downloaded the minimal install of Xubuntu, tweaked it to near-satisfaction, then removed the Xubuntu Desktop, in effect leaving only xfce.

EDIT - If, as you say, this all works with the NBR I'll have to give that a try.    :D

---

