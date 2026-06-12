---
title: "Newb - a few minor annoyances..."
date: 2010-12-31
forum: New to Ubuntu
---

### Post by ~Maxx on 2010-12-31
Hi folks.  I just got Lubuntu running on this ancient Compaq Deskpro.  It's performing fantastically.  Even Firefox is running better than I would have thought.  I'm brand new to Linux though (toyed around with Xubuntu a few years ago, but lost interest), and I've got a few minor things I can't seem to find answers to.  Hopefully someone can point me in the right direction...

First off, I accidentally deleted the shutdown icon on the right side of the (bottom) panel or "taskbar", and I can't seem to get it back.  I'm fairly sure it was listed as an "application launch bar", but there doesn't seem to be a shutdown option under that heading.  In fact I can't find it anywhere in the "add/remove panel items" options.  Any ideas?  Along the same lines I'd love to have a "reboot" icon as well if anyone knows how to do that.

I'm also looking for a way to get the pc to actually power down when the shutdown option is selected.  Currently it just logs you out of Lubuntu and stays on a screen that says something to the effect of "system halted".  Is there a BIOS setting I'm missing?

Lastly - I'd like to find a way to change the NumLock state at startup.  I never use the upper row keys, and it's rather annoying to start typing passwords, etc... only to find that the number pad is rendered all but useless when the system boots.  I seem to recall having the same problem with Xubuntu.  Not sure if I ever found a way to fix it.

I'm sure I'll be back with other things as I learn my way around, but these are the annoyances that I can't seem to find answers to on the web.  Any advice would be much appreciated.  Thanks in advance!

---

### Post by Bluenoser81 on 2010-12-31
"Add to panel.." > Indicator Applet Session, or "Shutdown" for just the plain ol' big red button. The red button can also be used as reboot, just click on it and chose 'reboot' instead of shutdown. I don't know about the caps lock problem. Anyone?

---

### Post by ~Maxx on 2010-12-31
Thanks for the quick reply Bluenoser81.  It would seem, however, that Ubuntu and Lubuntu have their differences in this regard.  If I right click the panel and choose add/remove panel items, then select the "add" button, there is not an option labeled "shutdown" anywhere in the list.  I can add an "indicator applet", but I have no idea what it "indicates" as it only seems to add a line of text to my panel saying "No Indicators".

I suppose it might be helpful if i set up some screenshots so that those of you not familiar with Lubuntu's gui differences could see what I'm working with.  Unfortunately I haven't taken the time to learn about screenshots on this OS yet.

---

### Post by ~Maxx on 2010-12-31
Solved the numlock issue.  Found an old reference to a "numlockx" package available in the repositories.  Installed it.  Worked like a charm!

Next?

---

### Post by cavalier911 on 2010-12-31
**Restore the lxpanel power off button.**
Simple Method to Restore Default Panel:
thread #11
[http://ubuntuforums.org/showthread.php?t=1490938&page=2](http://ubuntuforums.org/showthread.php?t=1490938&page=2)

**Try acpi=force to poweroff old hardware.**
Open lxterminal
```
gksudo leafpad /etc/default/grub
```
Add whats in bold,save,close leafpad
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi=force**"
```
sudo update-grub
```
Shutdown,reboot,shutdown

---

### Post by paparoo on 2010-12-31
Maxx

Right click in a clean area of the panel. Choose 'Add to panel'. From the list, choose 'Shutdown'. Then click ADD at bottom.

It sounds like you're clicking ADD before you choose Shutdown.

All done. Good luck.

paparoo

---

### Post by verymadpip on 2010-12-31
~Maxx,

I run Lubuntu on a couple of boxes & the guys on lubuntu irc channel are really helpful.

Fire up xchat from the internet category in the main menu, connect to freenode & join #lubuntu.

---

### Post by steve7777777 on 2010-12-31
> **~Maxx said:**
> ...I'm also looking for a way to get the pc to actually power down when the shutdown option is selected.  Currently it just logs you out of Lubuntu

I'm on Ubuntu 10.10 and the something similar just popped up. When I hit "shut down" the re-boots, instead of powering down. I've been using the the command line instead:

$ sudo halt

Not a big deal since the system is always on, but anyone know why "shut down" reboots?

---

### Post by ~Maxx on 2010-12-31
> **cavalier911 said:**
> **Restore the lxpanel power off button.**
Simple Method to Restore Default Panel:
thread #11
[http://ubuntuforums.org/showthread.php?t=1490938&page=2](http://ubuntuforums.org/showthread.php?t=1490938&page=2)

**Try acpi=force to poweroff old hardware.**
Open lxterminal
```
gksudo leafpad /etc/default/grub
```
Add whats in bold,save,close leafpad
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi=force**"
```
sudo update-grub
```
Shutdown,reboot,shutdown
Both of these solutions worked perfectly, and without hassle.  Thanks a million cavalier911!

> **paparoo said:**
> Maxx

Right click in a clean area of the panel. Choose 'Add to panel'. From the list, choose 'Shutdown'. Then click ADD at bottom.

It sounds like you're clicking ADD before you choose Shutdown.

All done. Good luck.

paparoo
Just an FYI...  Not sure which desktop you're using, but it seems to me like LXDE is a bit different from XFCE and GNOME.  When I right click the panel and select "add/remove panel items" it opens up a list of what I *already* have on the panel.  Clicking "add" from there will then produce a list of other items that can be added.  "Shutdown" is not an option featured on either of these.  Resetting to default seems to be the only way to get the icon back (based on the above post).

> **verymadpip said:**
> ~Maxx,

I run Lubuntu on a couple of boxes & the guys on lubuntu irc channel are really helpful.

Fire up xchat from the internet category in the main menu, connect to freenode & join #lubuntu.
Fantastic!  Thanks for the invite!

---

