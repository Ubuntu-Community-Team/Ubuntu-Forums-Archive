---
title: "PS3 + Ubuntu = slow!  Try Xubuntu?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by sweitzen on 2009-08-04
Hello all!
 
I installed Ubuntu 9.04 on my PS3 last night, and then installed VLC. Connected to my server and tried to watch my movie collection there (which is my goal in this project). The playback was slow and choppy.
 
I read that only 256MB is available to the other OS when installing another OS to the PS3, and (IIRC) not the full GPU, so this may be why it was slow.
 
Since, if I understand correctly, Xubuntu is designed for low-RAM systems, I am considering installing Xubuntu 9.04 on the PS3, and seeing if VLC runs better then.
 
Any suggestions?

---

### Post by philinux on 2009-08-04
Why not just use mediatombe or fuppes?

Also YDL is optimised for the ps3.

---

### Post by CatKiller on 2009-08-04
[This page]("http://en.wikipedia.org/wiki/Linux_on_the_PlayStation_3") might give you some ideas, or link to some more information.

---

### Post by sweitzen on 2009-08-04
> **philinux said:**
> Why not just use mediatombe or fuppes?
 
Also YDL is optimised for the ps3.
 
 
Mediatomb and fuppes are just mediaservers?  I have Windows Media Server and PVConnect on the Windows Home Server, so unless those two would give me something the others don't...
 
Downloading YDL 6.1 for PS3 (I see version 6.2 has just been released for free download from the mirrors, but not a version for PS3 yet).
 
I will try Xubuntu first (supposedly will run fine on 64 MB PII machine), and then YDL, and see which I like better.
 
Thanks for the tip about YDL.  Looking up Fuppes and MediaTomb to see if they do anything particular I want.

---

### Post by wizard10000 on 2009-08-04
Even Xbuntu won't help a whole heck of a lot.

A PS3's only got 256mb of RAM.  Eight cores, but only 256mb.

JMO, but a Playstation makes a lousy PC.  IIRC there's still no way to make wireless work under Linux.

edit:  You can just install xubuntu from the repos rather than reinstalling if you've got the disk space.

sudo apt-get install xubuntu-desktop

then just change your window manager  :)

---

### Post by insane_alien on 2009-08-04
just because something CAN function as something else, doesn't mean its going to be good at it. just like how you CAN use a fork to cut things but god help you if you're trying to cut up a tough steak.

use things for what they were designed for.

---

### Post by sweitzen on 2009-08-04
> **insane_alien said:**
> just because something CAN function as something else, doesn't mean its going to be good at it. just like how you CAN use a fork to cut things but god help you if you're trying to cut up a tough steak.
 
use things for what they were designed for.
 
 
Well, ultimately, if it just doesn't work, I'll need something else. My TV has a Wii and a PS3 hooked up to it -- before I went and put a computer under my TV, I figured I'd try to use what assets I already had in place.  I may end up getting something like the Dell Studio Hybrid, use the TV as the monitor, and problem solved.  But I'd like to see if i can make this work, first.
 
Really, all I want is to be able to access and play the virtual DVDs in my media libray the same as I can on a computer -- as if the DVD itself was in the drive; full menus, sound/language options, DTS/Dolby5.1, subtitles, etc.
 
I can partly solve my problem simply by transcoding the DVDs to a single mpeg-4 file, but I lose all the options that way.

---

### Post by sweitzen on 2009-08-04
> **wizard10000 said:**
> Even Xbuntu won't help a whole heck of a lot.
 
A PS3's only got 256mb of RAM. Eight cores, but only 256mb.
 
JMO, but a Playstation makes a lousy PC. IIRC there's still no way to make wireless work under Linux.
 
Well, VLC *almost* played acceptably under Ubuntu.  It was close.  I have a wired ethernet connection, and I'd be using a USB keyboard/touchpad combo with it. 
 
> **wizard10000 said:**
> edit: You can just install xubuntu from the repos rather than reinstalling if you've got the disk space.
 
sudo apt-get install xubuntu-desktop
 
then just change your window manager :) 
 
OK, this is Day Two of my linux experience.  Can you break that down just a little bit more?  
 
advTHANKSance

---

### Post by wizard10000 on 2009-08-04
> **sweitzen said:**
> OK, this is Day Two of my linux experience.  Can you break that down just a little bit more?

Sure.

Open a terminal window and type in there

```
sudo apt-get install xubuntu-desktop
```

and when it finishes installing reboot the playstation.  When you log back on you'll see the graphical login manager where you put in your username and password - on the "Sessions" menu you'll see where you'll be able to select xfce as well as GNOME.

---

### Post by sweitzen on 2009-08-04
> **wizard10000 said:**
> Sure.
 
Open a terminal window and type in there
 
```
sudo apt-get install xubuntu-desktop
```
 
and when it finishes installing reboot the playstation. When you log back on you'll see the graphical login manager where you put in your username and password - on the "Sessions" menu you'll see where you'll be able to select xfce as well as GNOME.
 
Thanks!
 
I'll try that, and see what it does.

---

### Post by Ji Ruo on 2009-08-04
You might want to try LXDE instead. I've found it much faster than Xubuntu (on my ancient laptop). [http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html]("http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html")```
sudo aptitude install lxde
```

---

### Post by dv-design on 2009-09-07
Sweitzen,

I have alot of expeirence with using ps3 as a media center. How are your computer and ps3 networked (wireless, wired, etc)? Also, what types of files are you trying to play, are they .iso, avi's, .mkv, etc?

The ps3 isnt the fastest computer for running linux, but it does the job...however linux on the ps3 currently cannot utilize some of the video acceleration that a practicle computer can.

Dependant on your setup i have a few suggestions, some may eliminate the need for linux, some might utilize linux as a tool...all depends on what files and your network setup.

Let me know.

---

