---
title: "Desktop completely white!  No applets showing."
date: 2010-02-18
forum: New to Ubuntu
---

### Post by lunalilo on 2010-02-18
First off, I am 100% newbie material, but I love the thought of learning linux.  Like when you have your first naughty thought of that girl in junior high.  Anyway...

...I am Kubuntu 9.1 Netbook edition. I look under the monitor and notice plasma-netbook is running but everything is completely white, and all I see is a grey bar on the top that won't auto-hide.  Kubuntu always restarts like this, and I need help in the form of step by step information on how to reset everything.  Thanks to anyone who is willing to help!

Lilo
Kaneohe, Hawaii.

---

### Post by lunalilo on 2010-02-18
bump... i need this working, I have internet connection and I can run the run command and find things, but nothing is showing... picture attached... like i said I can do everything I want manually, My Desktop is just Blank and I dont't know how to add anything back.

---

### Post by phrackcreak on 2011-02-10
And now, a year later, I am seeing this behavior on my netbook.

I have been running 10.04 lucid kubuntu edition for a while on my netbook and everything has been working great. About 3 weeks ago (not exactly sure -- I was working on travel arrangements and am now traveling and decided to ignore the problem since the computer continues to operate fine) I boot to a white screen with a working applet container, working alt-f2 and generally working computer. Except, plasma desktop just shows up white. Also, plasma crashes whenever I shut down the computer.

From these symptoms, I suspect that plasma does not completely finish initializing and later crashes when sent a SIGTERM during shutdown.

How I got here:

* I accidentally clicked the minus sign on the home directory icon on the desktop to the right of the 'system settings' icon and my home directory dolphin shortcut disappeared.
* I did this once before and a reboot later, everything was fine. So, I reboot and my dolphin shortcut is still missing. I search for ways to add it back.
* I recall switching something called something like 'desktop styles' and finally settled back on the (as best as I can remember) the search and launch interface and the home shortcut was still missing.
* I added a desktop widget for the home dir. Rather than appearing large and near the top (where it was before) it appeared small and toward the bottom of the desktop. I went through 2 or 3 variations on this trying to re-instate my home dir shortcut as it was.

At some point I reboot and I now find:

* The desktop displays no icons and instead shows a white background.
* Desktop boots and session management is still in place (if I had Konsole running, a new Konsole is started with the same tabs and working directories).
* Applications start normally from Konsole and the Alt-f2 shortcut.
* The panel works fine.

I have read through the logs and the first really suspicious log line I can find is in ~/.xsession-errors and reads:

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/phoenix/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kwin(1689) KWin::Workspace::updateClientArea: screens:  1 desktops:  3
kwin(1689) KWin::Workspace::updateClientArea: Done.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXQueryDrawable" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
kwin(1689) KWin::SceneOpenGL::selfCheckFinish: Compositing self-check passed.

So in these serial log lines, we discover that ibus is not running correctly and that (probably) kwin is trying out some GL features, failing, and reporting success. The latter looks like a sequence of feature discovery rather than application error to me so I am wondering about ibus.

Has anyone else seem the plasma desktop white screen of ghostly life?

Is there any further diagnostic information I could post to try to figure out why plasma boots to white rather than icons?

---

