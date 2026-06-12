---
title: "Desktop and bars disapeared"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by DangerDaveoo7 on 2009-09-08
I just installed Ubuntu on a 4G Eee PC.

I installed a car tuning software. Haven't done anything else.

Upon restart my desktop is gone and I cannot see the bars on the top or bottom. I did put the new program I installed on the desktop, I can still see the program and use it. I still can create folders.

When I create a new folder and open it, there are no buttons to close the window, nor no minimize option. I also cannot right click on the window and do anything. 

Alt+F2 doesn't do anything. 

I can hit Ctrl+Alt+F2, but then I don't know what to do from there.

I cannot see any off the stuff that was on the bar, so I cannot open a terminal.

Please bear with me as I'm new to Linux.

I have searched on here and google, and I'm getting a headache. Nothing seems to be up to date or it's a different problem.

Can anyone walk me though what might be wrong?

I assume that my resolution went to something else?

---

### Post by izziere on 2009-09-09
Seems to be a common problem.

Anyway, on your machine there may be another way to activate terminal.  Perhaps by Ctrl-Shft-T or something.  Alternatively log into Ubuntu via a terminal window rather than GUI.

Next, follow the instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=392387]("http://ubuntuforums.org/showthread.php?t=392387")

Alternatively you can sudo killall gnome panel, which should do the trick.  Maybe need to restart.

With regards to desktop icons - there is an option under Nautilus that allows for the icons to be hidden.  Not on my Ubuntu computer at the moment, but try googling it - there are many suggestions.

Good luck.

---

### Post by DangerDaveoo7 on 2009-09-09
> **izziere said:**
> Seems to be a common problem.

Anyway, on your machine there may be another way to activate terminal.  Perhaps by Ctrl-Shft-T or something.  Alternatively log into Ubuntu via a terminal window rather than GUI.

Next, follow the instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=392387]("http://ubuntuforums.org/showthread.php?t=392387")

Alternatively you can sudo killall gnome panel, which should do the trick.  Maybe need to restart.

With regards to desktop icons - there is an option under Nautilus that allows for the icons to be hidden.  Not on my Ubuntu computer at the moment, but try googling it - there are many suggestions.

Good luck.

None of this worked. Nothing worked from the other post.

I still cannot open a terminal. "No process killed" when using killall gnome panel and killall gnome-panel.

Nothing changed. I already re-installed once before. I don't mind doing it, but it I do it again, it is going to happen again. 

How would I go about fixing this with a fresh install? Any options I can change.

Edit: I forgot to add that I also did a apt-get install desktop.

Edit2: I'm doing a fresh install as I type this.

---

### Post by DangerDaveoo7 on 2009-09-09
So I re-installed Ubuntu, but now I cannot right click on my desktop.

---

### Post by izziere on 2009-09-12
Are you able to load a terminal and do you have panels back? If you can, start gconf-editor in terminal and it will load GUI.  Go to apps/nautilus/desktop and you will gets loads of useful options.  Make sure 'show desktop' is enabled.

Hope this works for you.

---

