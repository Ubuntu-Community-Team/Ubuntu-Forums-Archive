---
title: "Out of range problem..."
date: 2009-11-21
forum: New to Ubuntu
---

### Post by MehdizLinux on 2009-11-21
Hi,
I installed the 3D game Trigger. But when I run it my monitor goes blank and says:

Out of Range
81.4 KHz / 65 Hz

Ant Ideas ?

---

### Post by SlugSlug on 2009-11-21
have a poke round your home folder's hidden directorys for the games config, and edit that text file

:popcorn:

---

### Post by MehdizLinux on 2009-11-21
Interesting! Can you explain more?

---

### Post by nikhilbhardwaj on 2009-11-21
its a resoulution problem
the game tries to start with a resolution your monitor doesn't support

so find the config files for your game
and change the game's resolution to match your current resolution

---

### Post by MehdizLinux on 2009-11-21
Where can I find the config file most probably?

---

### Post by MehdizLinux on 2009-11-22
Hi,
Any suggestions? I need to know at least what the file name looks like or the location. Thanks...

---

### Post by Perfect Storm on 2009-11-22
You'll find the file at

 ~/.trigger/trigger.config


when open the file look for;

<video
		width="800"
		height="600"

---

### Post by MehdizLinux on 2009-11-22
Thanks, But does it mean my Monitor cannot support 800X600 ?!! My current resolution is 1280x1024.

---

### Post by Perfect Storm on 2009-11-22
Could be.
Or the resolution of 800x600 is missing due to poor driver or bug in detection the resolution of your monitor.

---

### Post by MehdizLinux on 2009-11-22
Thanks AI. I learned something. It worked!  But I wish it wouldn't!! :D It looks like the second stage of a PS3 game under construction which will come out Jan 2011 !! :)

---

### Post by Perfect Storm on 2009-11-22
You may try taking a look at:

[http://gwos.org/doku.php/games:alphabetical:r:racer](http://gwos.org/doku.php/games:alphabetical:r:racer)

[http://gwos.org/doku.php/games:alphabetical:t:torcs](http://gwos.org/doku.php/games:alphabetical:t:torcs)

[http://gwos.org/doku.php/games:alphabetical:v:vdrift](http://gwos.org/doku.php/games:alphabetical:v:vdrift)

[http://gwos.org/doku.php/games:alphabetical:c:car_arena](http://gwos.org/doku.php/games:alphabetical:c:car_arena)

[http://gwos.org/doku.php/games:alphabetical:m:maniadrive](http://gwos.org/doku.php/games:alphabetical:m:maniadrive)

[http://gwos.org/doku.php/games:alphabetical:u:ultimate_stunts](http://gwos.org/doku.php/games:alphabetical:u:ultimate_stunts)

---

