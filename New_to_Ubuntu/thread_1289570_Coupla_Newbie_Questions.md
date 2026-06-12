---
title: "Coupla Newbie Questions"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Xalor on 2009-10-12
Hey Everyone, I just started Ubuntu yesterday. First time ever installing it. I've used it once before in a VM but thats pretty much it. I'm loving it right now, and its much faster than or any other OS I've used. 

The main reason I installed Ubuntu is because I wanted to see if Vista was the reason my computer repeatedly overheated and shut down, it hasn't heated up much when I use Ubuntu. 

I have a couple of questions though:

1) I can't seem to get compiz cube to work properly. It doesn't activate when I use the shortcuts. The other effects work, and I'm pretty sure my graphics card is good enough for compiz cube, because the other effects work perfectly. 

2) Is emerald or metacity better? Also, when I use emerald --replace, where do I put the emerald themes, when I go to theme manager, it still has the gtk/metacity themes in there. 

3) What is the difference between Ubuntu and Xubuntu? I know Kubuntu has KDE instead of GNOME and Edubuntu is educational, but what's Xubuntu for?

Other than that, I can't believe how easy it was to install ubuntu. The partitioner was pain-free and it booted into a GUI so fast. The drivers were automatically installed and everything works, when I reinstalled Vista to wipe my harddrive as a cleanup it took me a couple of hours to find the correct drivers since dell had provide them, and the old ones don't work anymore. 

Oh and if anyone could point me to a quick guide on the terminal, I would be very happy. 

Thanks, and I hope to join the community

---

### Post by sandyd on 2009-10-12
> **Xalor said:**
> Hey Everyone, I just started Ubuntu yesterday. First time ever installing it. I've used it once before in a VM but thats pretty much it. I'm loving it right now, and its much faster than or any other OS I've used. 

The main reason I installed Ubuntu is because I wanted to see if Vista was the reason my computer repeatedly overheated and shut down, it hasn't heated up much when I use Ubuntu. 

I have a couple of questions though:

1) I can't seem to get compiz cube to work properly. It doesn't activate when I use the shortcuts. The other effects work, and I'm pretty sure my graphics card is good enough for compiz cube, because the other effects work perfectly. 

2) Is emerald or metacity better? Also, when I use emerald --replace, where do I put the emerald themes, when I go to theme manager, it still has the gtk/metacity themes in there. 

3) What is the difference between Ubuntu and Xubuntu? I know Kubuntu has KDE instead of GNOME and Edubuntu is educational, but what's Xubuntu for?

Other than that, I can't believe how easy it was to install ubuntu. The partitioner was pain-free and it booted into a GUI so fast. The drivers were automatically installed and everything works, when I reinstalled Vista to wipe my harddrive as a cleanup it took me a couple of hours to find the correct drivers since dell had provide them, and the old ones don't work anymore. 

Oh and if anyone could point me to a quick guide on the terminal, I would be very happy. 

Thanks, and I hope to join the community
1) have you tried installing your graphics drivers through
```

jockey-gtk

```?
2) don't know, never used it

3) Xubuntu is a lighter version of ubuntu. It uses XFCE, a desktop environment that consumes less sytem reqources

---

### Post by jmszr on 2009-10-12
Xalor,

Welcome aboard!

This is a good Terminal guide: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) . You may find this useful, also: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)

---

### Post by Xalor on 2009-10-12
Thanks for the help, I did install my graphics drivers, well I believe I did, and would Xubuntu be better on a slightly older computer like a Pentium 4 2.8ghz, and 1gb of ram, dunno the rest of the specs, its not that old, or would ubuntu be fine?
Only because my parents find reading their own language easier than english, and ubuntu has a translated version of that langauge.

---

### Post by Abu_Dayya on 2009-10-12
1 - well, since other effects are working, I assume the graphics drivers are installed. Did you set your desktop size? Open CompizConfig Settings Manager, then click on General Options. There you'll find a tab named Desktop Size, set the Horizental Virtual Size to 4, Vertical to 1, and Number of Desktops to one.

2 - Sorry, I don't use emerald

3 - Ubuntu is fine for your specs. Besides, I heard some people say that XFCE is not that much lighter than Gnome.

Hope that helps!

---

### Post by ugm6hr on 2009-10-12
I would suggest sticking with Gnomne until you familiarise yourself with Linux.  I personally use XFCE (and used it prior to Gnome), but think if you have the hardware for Gnome (as you do), it is sensible to start with Gnome for simplicity.

Remember, most users here either use Gnome, or are at least familiar with it, so it is easier to get assistance in Gnome.

I'm afraid I haven't used Compiz for a few months, so can't help there.

As for Terminal, there is no "quick guide" that covers everything.  See the Terminal link below to see what it does, but there are thousands of commands for use, which you will have to find and use as you navigate your way through the forums.  The most useful is the "man" command. e.g.

```
man apt-get
```

---

### Post by howefield on 2009-10-12
> **Xalor said:**
> Is emerald or metacity better? Also, when I use emerald --replace, where do I put the emerald themes, when I go to theme manager, it still has the gtk/metacity themes in there.

Download your emerald theme(s)then open Emerald Theme Manager from the System > Preferences menu and press the import button. Navigate to where you have put the emerald files.

If you want emerald to start at boot up, you can add the emerald --replace command to your "Startup Applications" via the System > Preferences menu.

---

### Post by Xalor on 2009-10-12
Whoa didn't expect so many quick responses. Thanks for all the help. I found the Emerald Theme Manager, but I think I'll just play around with Metacity and GTK for now. 

Actually looking at compiz and virtual desktops, I don't really need it, Gnome Do Docky is much more easier than swapping desktops

---

### Post by ConXtionS on 2009-10-12
Yeah.... I cant believe that there are people willing to hang out here just to help us ...

its a great crew

I wish you the best with UBUNTU.... I would like to suggest however that overheating is a bad sign....

you need to grab a can of compressed air (5 bucks at walmart) TURN OFF AND DISCONECT the computer

open the case, make sure one hand keeps touching the case at ALL TIMES (for static)

Clean out the CPU fan and HEATSINK

if your Video card has a fan clean it too

Same for your power supply

THEN

plug the puter back in, turn it on, and insure that all the fans are turning, but keep your fingers out (No TOUCHIE the magic stuff)

If you feel its all clean and all the fans are working, reassemble and test the puter really hard.... play games, watch movies, surf porn... you know the drill

WELCOME TO LINUX

Jim

---

