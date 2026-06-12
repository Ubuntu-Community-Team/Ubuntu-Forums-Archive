---
title: "Applications not started, menus empty"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Zeedok on 2009-09-22
I was playing around with Kubuntu-desktop tonight (I am normally using Ubuntu 9.04 with the gnome setup) and really stuffed a few things up.

Firstly, I was trying to keep the KDE and GNOME apps separate, and found this script to do it (I know, a real mistake running a script without understanding the full implications - here's [the blog post]("http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/") and the script is attached below.

Anyway, I had fun playing with Kubuntu, but not so much that I was willing to leave ubuntu, but once I tried to log back into gnome all I could get was a blank desktop (ie no panel+menus, no desktop icons, no window manager even). Only Gnome-do was running, which was helpful in opening nautilus at least (but nothing much else).

After reading a trying a number of things I have worked out how to start applications manually (ie by opening /usr/share/applications and double clicking a program) and I also found the defaults.list there (actually a symbolic link) and I remove the final two lines of my version (the ones that I think the script created).

This has not fixed my problem however - I still have no apps loaded on  login and my menus have very few items in them.

Can someone suggest how I could fix these problems?? I am pretty good about rsync'ing my home folder, so I can copy directories etc if necessary, I'm just not sure which one is the culprit.

Thanks

EDIT: I just switched to a "Guest Account" to see if the problems persisted over there, and they do, so maybe the culprit configs are not in my home folder . . .???

---

### Post by Marflus on 2009-09-22
Since the script creates a backup folder, you ought to be able to simply restore that backup. 
[FONT=monospace]
Something like:
[/FONT]```
cp  ~/.menu-backup/gnome/* /usr/share/applications
cp ~/.menu-backup/kde/* /usr/share/applications/kde

```Might work, just from a brief look at what that blog post is telling you to do.

---

### Post by Zeedok on 2009-09-22
I tried re-installing my home directory (before I realised that there were automated backups) so I think I have deleted them accidentally.  

My problem is that I don't know what the script is doing (I really should never have run it).

---

### Post by Marflus on 2009-09-23
Hrm, that complicates things ;) No bother though, we'll fix it up.

All that script is doing is going through the Gnome applications and adding "OnlyShowIn=GNOME" to their entries (and the same but with KDE apps), so that the applications are only visible in their respective menus. 

I can't see anything in the script that should have caused anything untoward, but perhaps what was inserted into those files conflicted with something already there, for example if a Gnome application contained OnlyShowIn=KDE and then had OnlyShowIn=GNOME added to the end of it. This would obviously cause some problems, and could perhaps result in the problems you're experiencing. I can't imagine why a Gnome application would have OnlyShowIn=KDE appended to it, but perhaps some variant of this is your problem, in which case it ought to be fairly simple to fix.

The best way to check is to first ensure that your /usr/share/applications folder contains all the applications you want in your menus in it. If it doesn't, then all that^ is almost certainly wrong, and we'll have to try something different. If it does, open up one of the files (for example, rhythmbox.desktop) in a text editor, and post the contents. Hopefully it should help out a little.

```

gedit /usr/share/applications/rhythmbox.desktop

```

---

### Post by Zeedok on 2009-09-24
> **Marflus said:**
> Hrm, that complicates things ;) No bother though, we'll fix it up.

Hey thanks for your help and your confidence.  I am almost sorry to say that I took the chicken's option and did a reinstallation.  Thankfully, I started doing regular home directory rsync backups about a month ago and had an updated copy of my home directory on an external hard drive.  I also have DropBox installed, which fixed up any changes from my archive.  So, all in all, the reinstallation was not "such" a big deal.

I'm not anticipating repeating my mistake (to be honest I am really most comfortable with gnome, I am just curious about KDE from time to time), but I'll keep your suggestions in mind if I run into something similar.

Thanks again for the help - sorry I was so impatient!!

EDIT: I realize now that the applications I was missing were in /usr/share/applications - that's how I was able to launch them.  We'll never know now - no I am not running the script again "just to see" - but I think your suggestion may well have been the answer . . .

---

### Post by Marflus on 2009-09-24
No worries, glad you got it sorted out. Reinstallation is usually the most certain answer :P

I'm glad you thought my idea was likely to work, though. 

I for one certainly *will* be trying to repeat your mistake, I want to see how on earth that script backfired like it did :)

---

### Post by Zeedok on 2009-09-24
Good luck - hope you learn something.

Incidentally, do you know how to resize kde application font sizes in a gnome environment??  Ie the global font settings do not apply to kde apps and I'm not sure which kde component is necessary.

---

### Post by Marflus on 2009-09-24
Basically, no, I don't, as I'm more of a GNOME user. I've only ever run one KDE application in GNOME (Amarok), and didn't enjoy the experience so try to avoid it nowadays. However, a quick search turns up this:

[http://ubuntuforums.org/showthread.php?t=60451](http://ubuntuforums.org/showthread.php?t=60451)

Run kcontrol, and apparently you can alter it through Appearances and Themes -> Fonts.

That was a good 4 years ago now, though, so it may no longer work. If it doesn't, I'm sure someone on here will know how it's done nowadays. Make another topic, I guess.

---

### Post by Zeedok on 2009-09-24
Looks like kontrol was part of KDE 3 and is not part of KDE 4.  The replacement, from what I can tell, is provided by a package called systemsettings.  I have installed this package, but it doesn't provide any font size options, so I'm not sure what else I can do . . .

---

### Post by Marflus on 2009-09-24
I'll be installing KDE tomorrow for some playing around, so I'll take some time on this problem to see what works and what doesn't. Should be able to figure something out that way.

---

### Post by Marflus on 2009-09-25
System Settings does it for me. System Settings -> Appearance -> Fonts. Change them as you wish, I managed to put all KDE applications font size to 48 with no bother. I wouldn't do it again, though, was annoying to put it back...

---

