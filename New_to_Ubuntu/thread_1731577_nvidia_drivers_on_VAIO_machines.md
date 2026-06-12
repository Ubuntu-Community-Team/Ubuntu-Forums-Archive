---
title: "nvidia drivers on VAIO machines"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by thorpig on 2011-04-17
I installed a dual boot of Ubuntu 10.10 on my Sony VAIO F-series laptop, and the first thing that I had problems with was the size of the screen; it didn't fit onto my monitor (meaning that the far right and bottom were accessible by the mouse but not visible). To rectify this, I installed the nVIDIA drivers and rebooted, but after the reboot all that came up was a blank purple screen. It would appear that this is a common problem with VAIO notebooks, and while I tried a number of tricks listed I often got lost in the technical jargon. (did I mention that my only experience with Linux was a couple of programming courses some seven years ago back in uni?)

I was using these instructions [http://forum.notebookreview.com/5820189-post2517.html](http://forum.notebookreview.com/5820189-post2517.html) since they were the easiest to understand, but after this line
> sudo mv /home/"youruser"/sonyedid.raw /etc/X11/.                      I got a message to the effect that something or other didn't exist.

For the time being, I have the card drivers uninstalled, but it would be nice if I could resolve this issue - otherwise, it's back to Windows. Any suggestions?

---

### Post by scott-ian on 2011-04-17
-First, make sure to copy the file to your home directory, and name it sonyedid.raw.
-Then, run this command: sudo mv /home/"youruser"/sonyedid.raw /etc/X11/ replacing "youruser" with the linux user name.  
*Remember: In Linux, file names are case sensitive!

---

### Post by thorpig on 2011-04-20
Right, so I was able to put the edid file in that directory, but then when I enter the nvidia-xconfig command, I get this error:

> wade@tengoku:~$ nvidia-xconfig

WARNING: Unable to locate/open X configuration file.


ERROR: Unable to write to directory '/etc/X11'.


---

