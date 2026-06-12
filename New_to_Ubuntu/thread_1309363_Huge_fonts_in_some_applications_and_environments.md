---
title: "Huge fonts in some applications and environments"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by koleoptero on 2009-11-01
So, I've had this problem in the past and I hadn't been able to solve it. I hope someone can provide some insight this time. :)

The problem is:
When I installed kubuntu 9.10 for the first time all the fonts appeared HUUUGE. I mean like size 150 or even bigger. That happened on all applications (even in the login screen).
Then I installed ubuntu 9.10 and *poof* problem gone. All applications appeared with normal fonts, no problem whatsoever. I am a bit tired of gnome though so I wanted to switch and I tried xubuntu as well.
So I install xubuntu 9.10, everything seems normal. I install vlc and k3b (cause I love them) and there is the problem again, but it affects only those applications (I assume all qt applications that is).

At the same time I have a video problem with totem. When playing a video in totem it appears skewed (the proportions are wrong, like 9:16 instead of 16:9) and no matter what ratio I select they remain wrong. No problem with video playback in vlc in gnome though (I don't know about kde or xfce cause the font problem made the progam unusable), or in mplayer with some settings (I had to change to gl2 driver to have proper playback).

**So **the real problem is the huge font problem. I am currently posting from xubuntu (which I intend to keep cause I have an old laptop). I believe though that the root of the problem must be something with the video drivers. I didn't have this problem in Jaunty, but I had it in the past with Gutsy.

My laptop is a Toshiba m70, with intel 945GM graphics.

Any idea will be appreciated. :)

EDIT: **A fix for the fonts has been issued. See post #8**

---

### Post by Gadgetech on 2009-11-01
You might try renaming the defaults files for you problem applications. Most applications do a nice job of resetting to their original defaults and creating a new defaults file/folder if the file/folder can't be found. I don't see any .k3b folder in my home directory, but there is a .qt folder (KDE apps are based on QT). Try renaming it to .qt-bak or something and then run k3b.

There's a .vlc folder on my system, try renaming that and see if it helps with vlc.

You could also try editing the files within those directories. The qtrc file contains all kinds of defaults, including fonts.

For Totem, the default settings are stored in $HOME/.gconf/apps/totem.

---

### Post by koleoptero on 2009-11-01
Well I purged and reinstalled vlc, opened it and closed it, then found folders of it in ~/.local and ~/.kde so I renamed those, and then restarted it but it's the same.:(

EDIT: there was no .vlc or qtrc file in my home folder.

---

### Post by koleoptero on 2009-11-01
Bump.:frown:

---

### Post by sameat on 2009-11-07
Is there any resolution to this?  Having the exact same problem with VLC in xubuntu 9.10.

Intel Extreme 2 graphics.

---

### Post by sameat on 2009-11-07
I have no idea what this might effect, but my vlc fonts appear correctly after I created the file ~/.Xresources with the following:

Xft.dpi: 90

After I saved the file and restarted X, vlc fonts were normal.  qtconfig had the same problem and seems to be fixed as well.

I found this in the web but I can't find my way back now.

Hope it helps.

---

### Post by koleoptero on 2009-11-07
Thank you! I'll try it as soon as I can.

---

### Post by koleoptero on 2009-11-08
Yes it works, verified. I'm now in Kubuntu 9.10 :D Thank you very much sameat.

For the new user that needs detailed instructions:

**Kubuntu 9.10**
You'll probably see huge fonts when booting from the Kubuntu 9.10 cd so you'll probably need to do this twice, to install and then again after the setup has finished and you have restarted to you installed system.
[LIST]
[*]Press ctrl+alt+F4 at the same time to go to the shell. There login with your username and password (if you're using the live cd then you won't need to login).
[*]Type: nano .Xresources (and press enter)
[*]Type: Xft.dpi:90
[*]Press ctrl+o and then enter
[*]Type: exit (and press enter) (if you use the live cd you again don't need to do this)
[*]Press ctrl+alt+F7 to go to the graphical interface again. It'll still be with large fonts.
[*]Press Alt+SysReq+k to restart the X-server. (the SysReq might be seen as print screen on your keyboard)
[*]Enjoy.
[/LIST]

**Xubuntu 9.10**
Sice most applications show OK you just need to:
[LIST]
[*]Open the Leafpad text editor.
[*]Type in it: Xft.dpi:90
[*]go to File -> Save as, and enter as the filename .Xresources
[*]Press Alt+SysReq+k to restart the X-server. (the SysReq might be seen as print screen on your keyboard)
[*]Enjoy.
[/LIST]

That's it. If it scares you know that it's easier that is seems, I've just overanalyzed the process to make sure you make no mistakes.

---

