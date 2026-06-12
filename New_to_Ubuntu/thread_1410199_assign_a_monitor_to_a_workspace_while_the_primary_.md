---
title: "assign a monitor to a workspace while the primary moitor can still switch between all"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by beholdforiambob on 2010-02-18
Hey and thanks in advance.

I am trying to find out how to assign a secondary monitor to a workspace while still allowing my primary to switch between all workspaces (even the one the secondary monitor is... monitoring)

I'm not sure I have explained exactly what I am trying to do above so here is the long story.

I am a high school teacher and I use my HP Pavilion tx2500 tablet pc to present power points to my class. I would like to assign the classroom projector to one workspace. I would like my laptop screen to be able to switch between all workspaces even the one the classroom projector is viewing. The reason I want to do this is so that I can use one workspace to take roll, edit my grade book and basically use my laptop while presenting a power point. I like to manipulate my slides by using the mouse (my tablet pen) to underline or circle things in my power point as I teach. Therefore it is necessary for me to be able to use my laptop monitor to switch to and view the workspace that my power point is on.



P.S. if this can be done my next question is would I be able to get my Wii White board function to work with these settings.

---

### Post by achase79 on 2010-02-18
This isn't exactly what I think you want but this may work.
[http://superuser.com/questions/29834/fedora-dual-monitor-one-workspace-per-monitor]("http://superuser.com/questions/29834/fedora-dual-monitor-one-workspace-per-monitor")

---

### Post by mwcrowley on 2010-02-18
this might be an easier solution.  Gnome and KDE handle some things differently so you might have to try each.  Setup the projector to run as dual monitor with your laptop screen.  Maximize a window on the projector screen.  The issue here is that Maximize might span both screens instead of just one, and that is why you might want to try it on KDE.  Or you could just right click on the corner of the window and enlarge it to fit the projector.  Any window in gnome can be "stickied" to appear on all work workspaces so that you can scroll workspaces and the stickied window will appear on all of them.  I think this essentially solves your problem.

---

### Post by beholdforiambob on 2010-02-18
Thanks for the responses guys. They are helpfull.

Just to clarify though, I am able to present the power point on a separate screen however what I need to do is rather specific due to my use of a tablet PC. Crowley, the problem with the split screen method is in order to manipulate the projectors screen I would need to have a mouse to drag over, sense I am using a pen on the tablet it is impossible to "touch" the projectors screen.

---

### Post by beholdforiambob on 2010-02-21
Bump... :(

---

### Post by Favux on 2010-02-24
Hi beholdforiambob,

I think you'd need the projector on an xrandr tv out script and then use another script to switch back to the laptop.  I'm not sure you can assign workspaces to the scripts, never looked into it, but maybe you can.  If Compiz doesn't have that you'd think there would be a plug-in for it.  If so when you leave the projector (TV out script)/workspace you'd run the normal video script to get the other workspaces.  So each script would run a xrandr command line.

[http://wiki.cchtml.com/index.php/TV_Out](http://wiki.cchtml.com/index.php/TV_Out)

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things)

[http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors/ATI](http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors/ATI)

[http://www.linuxpromagazine.com/Issues/2008/95/ASK-KLAUS/(kategorie)/0](http://www.linuxpromagazine.com/Issues/2008/95/ASK-KLAUS/(kategorie)/0)

[http://www.linuxpromagazine.com/Issues/2007/83/ASK-KLAUS/(kategorie)/0](http://www.linuxpromagazine.com/Issues/2007/83/ASK-KLAUS/(kategorie)/0)

---

