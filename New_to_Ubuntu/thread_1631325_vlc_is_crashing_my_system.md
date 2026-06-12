---
title: "vlc is crashing my system"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by taith on 2010-11-26
hello,
odd issue here, when i run vlc under ubuntu 10.10, every time i open vlc, either directly, or via an avi, it logs me off of ubuntu... i tried opening it via the command prompt and it gave some red errors, but as it logs me off, i cannot copy/screenshot it...

i have tried reinstalling vlc, but its still causing the issue... any ideas?

---

### Post by TeoBigusGeekus on 2010-11-26
Search for any vlc folders in your home partition, as well as in ~/.gnome, ~/.gnome2, ~/.local and delete them. 
Perhaps a misconfiguration is causing the crash.

---

### Post by taith on 2010-11-26
nope, i deleted those, and its still doing the same issue...

after starting some programs, i found that skype is causing the same issue :S it starts, tries to log me in, then logs me out of the compy...

---

### Post by taith on 2010-11-26
trying to run an avi through xine, and its saying

> 
No packages with the requested plugins found
The requested plugins are:
video/x-avi-unknown decoder


and i have all my repositories active :S

---

### Post by mc4man on 2010-11-26
Could be related this bug, (not quite getting where that bug is heading)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/661369](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/661369)
or one of these
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)

What happens if you go from terminal (not using qt4 interface

cvlc /path/to/filename

Have you tried removing skype (+ libqt4-network) and seeing if vlc works w/ default qt4 interface?

---

### Post by kroq-gar78 on 2010-11-26
if you have xinerama enabled (2 monitors), then I hve the same issue. I got my solution here (this is the bug you're having): [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)

---

### Post by motonnerd on 2010-12-23
I am having a similar issue.  Here, I find that I can play videos (though I haven't used your specific format) fine, but if I try to convert/transcode something the screen goes blank and I get dropped back to logon.  I even tried starting VLC in gdb, but to no avail -- it crashed *through* the debugger.  Story of my life.

Anyway, I found some unmet (and, according to Synaptic, unmeetable) dependencies which are probably crashing VLC.  (but why would it bring down the entire (I'm assuming) X server?)  Anyway, unmet dependencies are as follows:
libsdl-image1.2-dev
     Which depends on:
     libjpeg-dev  (Which cannot be found)
     libtiff4-dev "but it is not going to be installed"
          And then going into Synaptic it tells me that this depends on another library which depends on libjpeg-dev, which, as I mentioned before, does not exist.

Thoughts/workarounds?

Actually, I found the correct forum post for this question, and will move this question there as soon as I figure out how -- my apologies.

---

