---
title: "while using s-video terminal is only white box"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by normalson on 2009-07-14
Hi everyone, first post.  trying to get my older nvidia based shuttle SFF PC hooked up to my tube tv using 9.04.  I have installed the nvidia drivers and have everything setup like i need except when i go to the terminal it opens as just a white box, no menu or text or anything.  also the little indicator that says network connected in the upper right corner apprears as just a white box.

i found this thread:
[http://ubuntuforums.org/showthread.php?t=1130010&highlight=terminal+just+box&page=2](http://ubuntuforums.org/showthread.php?t=1130010&highlight=terminal+just+box&page=2)

and i believe it is similiar to my issue but i need the settings for a tv instead.

i  found these on a search, is this how i should be setting up my xorg file?
> Option        "TwinView"
    Option        "TwinViewOrientation" "Clone"
    Option        "MetaModes" "1024x768,640x480"
    Option        "ConnectedMonitor" "CRT,TV"
    Option        "TVStandard" "NTSC-M"
    Option        "SecondMonitorHorizSync" "30-50"
    Option        "SecondMonitorVertRefresh" "60"what is the best way to edit my xorg file to set this up so i the terminal is displayed correctly?

so far i just made changes in the nvidia xserver setup

thanks so much for any help

EDIT: figured it out with some more searching.  it was a bug/config error with nvidia and ubuntu: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/127887](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/127887)

the solution there fixed it!

---

