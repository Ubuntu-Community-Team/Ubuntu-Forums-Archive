---
title: "Ubutuntu won't load GUI/kicks into console on load (aka I broke it)"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by ProjectAzar on 2009-05-16
I am rather new to the Linux world, and I barely understand the little I can do on linux as is.  However, Ive wanted to move away from windows, and thought linux would be a good option.  Well, I installed it on my AMD 3.0 ghz dual core, 2 gig ram, nVidia 8800 gt system, and wanted to update the nvidia drivers (as ubuntu was whining abou tthem).  I follow the steps on the nvidia website, but I managed to break my installation, so it acts like there is no graphics card at all, and boots into the console.  Well, Ive been fiddling with this for a while now, following steps on multiple forums trying to fix this.

So far  I have attempted the following:

Simply typing startx...results in a "Saw signal 11. Server Aborting"  message. I have no idea what this means.

running dpkg for the xserver. I go through a series of screens about my keyboard and then it kicks out with a warning about a possibly custimized file.

Ive tired editing my xorg.conf file, but it looks odd, as it doesn't list any devices other than "configured Video Device"  There is nothing else in there except "Configured Monitor" under the monitor section.


I haven't got a clue as to what to do to fix this. Any help would be much appreciated, but if you tell to run a command or edit/open a file, I would appreciate explicit instructions on what to do. Like I said, I am a beginner at this.

---

### Post by coffeeaddict22 on 2009-05-16
Easy solution: boot up, choose the recovery console, and select "repair my graphics" (or something along those lines).
Post back if it doesn't work.

---

### Post by Keith Hedger on 2009-05-16
after you log in try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
this should give you your  gui back and allow you to try again

---

