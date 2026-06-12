---
title: "Start up graphic issue"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by BBQdave on 2011-06-18
Hello,

I have a Dell Inspiron 1100 with 1gb or ram.  I am using Ubuntu 10.04.2 LTS.  It works great on my old dell.  The only issue I have is an occasional start up problem of flashing white lines and then blank screen.

I looked up information on using Ctrl-Alt-F1, then Ctrl-Alt-F7; which half the time brings up the graphics (login, then desktop).  The other half of the time it just cycles endlessly through blank screen and flashing white lines.

Any information on this is much appreciated or point me in the right direction of graphic information on Dell Inspiron 1100.

Thanks

---

### Post by dFlyer on 2011-06-18
My first thought is what video card does the dell have?

---

### Post by BBQdave on 2011-06-18
I have found some great information at:

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

I will try these work arounds and indicate whether it was successful.

I apologize if this is old news, and this information is widely known.

Thanks for your patiences

---

### Post by BBQdave on 2011-06-18
Hey Gary,

the Chipset is 845GL with direct AGP integrated graphics at 64mb of video memory.

I will try the work arounds I found, and post my results.

Thanks again

---

### Post by BBQdave on 2011-06-19
I had to change a setting on GRUB.


[LIST=1]
[*]Edit the */etc/default/grub* file. You will need Admin privileges to do so (sudo)
[*]Find this line: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
[*]Replace with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash <option>”
[/LIST]
Possible options:

Older Intel video card: *i915.modeset=1* or i915.modeset=0
nVidia: *nomodeset*
Generic: *xforcevesa*

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

For my dell inspiron 1100, I opened a terminal window and typed:

sudo gedit /etc/default/grub
(entered my password)
I changed: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
Replaced with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;
In gedit, I saved and closed.
In the open terminal window, I ran the command: sudo update-grub
then exited the terminal window (typed exit).

This work around solved my problem!  Much Thanks to the author of the work around (more information in the above link).

---

