---
title: "libdvcs problem"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by woop on 2009-06-21
right first problem
I was unable to play dvds-message with something a bout "could not find resources" ran a libdvcs command I found on the forum..............now totem gives failed to connect to stream error 

I could now access the menu but get no further, upon the next update my computer went through a partial upgrade(or something to this effect)   

basically a lot of my applications were removed.........mostly games

now boot up time, and shut down time is slightly longer

and Ive got the acpid: exiting error on shutdown 

I only ran three lines of code in the terminal
wget [http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb](http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2_1.2.8-1_i386.deb) -c
wget [http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2-dev_1.2.8-1_i386.deb](http://ftp.yi.se/pub/software/videolan/libdvdcss/1.2.8/deb/libdvdcss2-dev_1.2.8-1_i386.deb) -c
sudo dpkg -i *.deb


, is there anyway to restore my old computer

HELP!!!:(

---

### Post by Sealbhach on 2009-06-21
None of those commands would have removed anything. The two wget commands just downloaded .deb files from that websites. The dpkg -i command installed the .debs. 

You could look in Synaptic Package Manager under File/History, this will tell you what packages were recently added or removed.

.

---

### Post by woop on 2009-06-21
Commit Log for Sat Jun 13 03:14:17 2009


Upgraded the following packages:
firefox (3.0.10+nobinonly-0ubuntu0.8.10.1) to 3.0.11+build2+nobinonly-0ubuntu0.8.10.1
firefox-3.0 (3.0.10+nobinonly-0ubuntu0.8.10.1) to 3.0.11+build2+nobinonly-0ubuntu0.8.10.1
firefox-3.0-branding (3.0.10+nobinonly-0ubuntu0.8.10.1) to 3.0.11+build2+nobinonly-0ubuntu0.8.10.1
firefox-3.0-gnome-support (3.0.10+nobinonly-0ubuntu0.8.10.1) to 3.0.11+build2+nobinonly-0ubuntu0.8.10.1
firefox-gnome-support (3.0.10+nobinonly-0ubuntu0.8.10.1) to 3.0.11+build2+nobinonly-0ubuntu0.8.10.1
xulrunner-1.9 (1.9.0.10+nobinonly-0ubuntu0.8.10.1) to 1.9.0.11+build2+nobinonly-0ubuntu0.8.10.2
xulrunner-1.9-gnome-support (1.9.0.10+nobinonly-0ubuntu0.8.10.1) to 1.9.0.11+build2+nobinonly-0ubuntu0.8.10.2




Commit Log for Fri Jun 19 18:46:37 2009


Upgraded the following packages:
app-install-data-commercial (10) to 10.3
file (4.24-4) to 4.24-4ubuntu1
libmagic1 (4.24-4) to 4.24-4ubuntu1
tzdata (2009f-0ubuntu0.8.10) to 2009j-0ubuntu0.8.10
tzdata-java (2009f-0ubuntu0.8.10) to 2009j-0ubuntu0.8.10



does this help?
I have also noticed that when I exit firefox sometime I try and open it again 
it then says its currently running

---

### Post by Sealbhach on 2009-06-21
That all seems fairly harmless, is your boot time badly affected?

Do you know how to get your games back?

When you get that acpid shutdown message, does your computer eventually shut down, or does it hang?

.

.

---

### Post by woop on 2009-06-21
ok I dont care about the games, not all are gone just the ones I didnt really use

and the shutdown time is minimally effected not to such a degree that I need it fixed- more of a niggle

but on shut down now I have a flashing _ (underscore) instead of the acpid error 
and it hangs

this is a major problem as everytime this happens I have to turn it off at the tower and on reboot my belkin usb adapter doesnt always work(this is a normal occurence when you shut off at tower which I dont care about as if you reboot a few times it eventually works lol)




sealbhach? thats not Irish is it?

---

### Post by Sealbhach on 2009-06-21
Sealbhach is just my forum name, it's an Irish name, and there was a Scottish king called Sealbhach at one time too.

I don't know about this shutdown error, that's more of a kernel issue I think, I get a similar awkward shutdown sometimes when I'm using wireless on battery, I guess you could look around on launchpad, to see if there's any clues...

e.g. this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302452)

It's interesting to read some of the comments from others, they suggest fixes or ways to workaround the problem until the bug has been officially fixed.

.

---

### Post by woop on 2009-06-21
ok cool Im Irish so hello there lol

oddly as said previously acpid stopped appearing and just a flashing underscore did, I ctrl alt del and it re-booted back into ubuntu
when I done this as said I was unable find network due to the workaround I had to use for my usb network adapter but upon another boot the flashing underscore has gone and all is as normal

In summary it seems to have fixed itself or will not be a consistant problem in the future which perhaps is more annoying than anything else

will report back if it re-occurs

---

### Post by Sealbhach on 2009-06-21
That's good to hear. I have noticed that Ubuntu (or more likely the Linux kernel) seems to correct or "fix" itself somewhat without my really having to do anything. Amazing really. Anyway, oíche mhaith duit. :D

.

---

