---
title: "Graphics problem in Ubuntu 8.10. Terminal method?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by MJGK on 2009-01-04
Hi, just note that this is my first thread here, and I only started with Ubuntu 8.10 yesterday; my first ever attempt with Linux.

My mistake is pretty simple; I changed "My Preferences", under "Screen Resolution" to 1024x768, which causes my computer to run considerably faster. This was perfectly fine, until today when I modified it *again* from the default 1280x1024 that repeatedly comes up. I selected 1024x768, and pressed 'OK'. I noticed, however, as soon as I pressed it that the 'refresh rate' had defaulted to '0', and the screen promptly decided to skew my entire viewing (with the vertical lines traversing the screen diagonally).

I can now only use the command line, or use my imagination to skew the screen back and use the mouse controls (it's only the display that is incorrect). I soon gave up on the latter, and now I can either entirely reinstall Linux, or possibly use the Terminal to edit the file that determines the settings at startup (the preferences have become the 'default').

I don't know if I have determined what this problem is correctly (so feel to suggest possible alternatives, in order to help me). In all seriousness, I would prefer to not re-install Ubuntu 8.10, as it would teach me nothing / not prevent a recurrence.


If you would like any more information please ask me as soon as possible to prevent any time issues. Thanks a lot, and if possible give a decent explanation for your solution to allow me to do this in the future if required, or help any others who are using the OS (it would be (mostly) useless to not know what I'm doing).

Any feedback on my question style would also be appreciated (first technical forum).

---

### Post by stoogiebuncho on 2009-01-04
Boot into the recovery kernel, and select the "Root Command Line" option (or whatever it's called.  the option that gets you to the command line.)

There are two things you can do here.  First, you can try fixing the problem yourself.  Navigate to the X11 folder:

```
cd /etc/X11/
```

Second, make a backup of your xorg.conf file (just in case)

```
cp xorg.conf xorg.conf.backup
```
(so the backup file is now called xorg.conf.backup)

Now open the file to edit it:

```
nano xorg.conf
```

If you scroll down you should find some information about your monitor and display.  You can try changing the resolution there.  There's no danger of screwing it up because it's already screwed up and you have a backup.  When you're done, save the file and type:

```
reboot
```


The other option is to skip trying to fix it and just reset everything.  Boot to the recovery kernel, go to the command line, and type:

```
dpkg reconfigure xserver-xorg
```

It will ask you a lot of questions about your system, including your keyboard and lots of things unrelated to your display settings.  There might be some questions you don't know the answers to.  If that happens, just select the default answers that the computer suggests to you.  It's pretty good at guessing what you need.

When it's done, type 

```
reboot
```


If you have any questions, post back.  Good luck.

---

### Post by MJGK on 2009-01-05
Just to say, the reconfigure required a '-' before it, which took a while to sort out. I did the reconfigure, but it asked no questions about my computer, and so I tried filling in xorg.conf myself (looking at tutorials).


I feel, however, that xorg.conf is not related to the issue. It was the same before I changed 'My Preferences', and I am now looking for a way to modify such preferences. It would be a simple matter (not requiring terminal commands) since I still have the Live CD, and I have been able to access my Ubuntu partition from it. Do you have an idea for how to access 'My Preferences', or am I barking up the wrong tree? 

PS: The error happens as I enter the desktop; I can see the mouse and various dialog boxes perfectly beforehand; does this have anything to do with Gnome settings? I hope I don't seem like an idiot, but this is the idea I get from it all.

---

