---
title: "No Desktop on 8.10!!!"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Aizen13 on 2009-02-05
Hey everyone.  I'm completely lost right now.  I downloaded the new distribution and it completely ate my you-know-what.  I tried going through the BIOS menu and everything was in order.  I went through the boot menu, where there are about 8 kernels to boot from.  I tried ALL of them.  A couple actually DID NOT recognize my mouse or keyboard, so I had to reboot.  The others recognized the peripherals but when I go through the log in, all I've gotten is a blank orange screen.  I don't know if this is a hardware problem or if there was a defect and/or virus attached to 8.04.  Anyway, I would appreciate any and all help.  I hope I posted the right place.

---

### Post by RomeReactor on 2009-02-05
Hi. Sounds like you upgraded from 8.04 to 8.10, correct? If you're dropped to a command line, try:
```
sudo /etc/init.d/gdm start
```
If it says it's already running, try:
```
startx
```
If you get errors, please post them.

---

### Post by Aizen13 on 2009-02-05
Cool...  Thanks, but how do I get dropped to a command line?  It's going straight through to the log in screen.

---

### Post by RomeReactor on 2009-02-06
Did you reach your graphical desktop? If so, make sure **Graphical login manager (GDM)** is checked in "System->Administration->Services". Did you install--and then remove--KDE or another desktop?

---

### Post by Aizen13 on 2009-02-06
That's a distinct possibility that I DID do that.  I'm not sure what I actually did, but it could be a conflict between GNOME and KDE.  Anyway, I used the command lines you gave me.  The first one, nothing happened, but I was in the boot kernel menu.  Secondly, when I used "startx" all it gave me was a gray screen.  I can't even get to a menu, because I have NO graphic interface AT ALL.  I have gone through every kernel which is there- as there are 6, plus the system check at the end.  I'm still getting nothing.  Should I reinstall through a CD?

---

### Post by RomeReactor on 2009-02-06
Try booting in recovery mode and selecting XFIX. It's also possible that some packages are missing, so make sure **ubuntu-desktop** is installed:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Aizen13 on 2009-02-07
So... this didn't work either.

---

### Post by Bölvaður on 2009-02-07
ok lets check if this is just gnome problem. We do it by installing anything that is easy to install and comes "instead" of gnome.... like fluxbox.

You should be able to select a "session" from the login screen. Pick any that you can use to install software with... recovery mode, failsafe with terminal.... anything.

When you have logged in and found the terminal, type:

> # apt-get install fluxbox
note that the # means the command is done by root (which can be activated with sudo before the command)

then (depending on the session you are logged on) you can type "exit" to go to the login page again or "reboot".. .which is not as nice way.

When you see the login screen again choose fluxbox from the "sessions".


Do you see anything now?
you should be able to right click to get a menu of applications.

if you see something now then we just need to fix your gnom:KS

---

### Post by Aizen13 on 2009-02-07
I had to run it in recovery mode.  I went to the options, selected "sessions," and ran it in "xterm."  After that, I got my terminal and ran the command line you gave me.  However, nothing is happening after a right click:  no menu, no options from ther...  nothing.  I'm still hitting a wall, guys.

Wanted to mention this: When I run it in any kernel besides a recovery mode kernel, it doesn't recognize my mouse or keyboard.  I think we're almost there, though...  i'm not giving up and going back to Windows:p.  (Thanks for your help-BTW)  :KS

---

### Post by marcusesses on 2009-02-07
I recently resolved a similar problem that came up while installing some 8.10 updates.

If you are doing a fresh intall of Ubuntu, then my advice is useless, but if you're upgrading from 8.04, then see this thread...

[http://ubuntuforums.org/showthread.php?t=1057181&page=2](http://ubuntuforums.org/showthread.php?t=1057181&page=2)

My problem was that X server didn't (initially) recognize my device driver...anyway, check out the thread and see if it's helpful.

---

### Post by Bölvaður on 2009-02-08
Sometimes when there is no linux expert on the location which can see exactly what can be done... reinstalling a different version (alfa version of next release or older release).

---

### Post by Aizen13 on 2009-02-10
Okay...  my question at this point is do I reboot the computer again and go to the XFIX or do I stay with the terminal?:confused:

---

### Post by wlg on 2009-07-20
I was using 8.04 for several weeks then all at once I had no desktop on boot-up.  Tried reinstalling from factory disk, still no desktop (Using Gnome).  Installed 8.10 from distro disk, still no desktop.. What up?:confused:

---

