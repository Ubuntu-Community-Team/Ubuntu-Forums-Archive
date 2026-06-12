---
title: "Always breaking! &quot;Loading&quot; ubuntu, black screen, nothing. Low graphics mode works...?"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-15
I just installed 11.04 and downloaded and installed a CRAP LOAD of stuff. I restored some of my settings, so this may be the problem. When I go into boot, I see ubuntu (bunchanumbers), ubuntu recovery, previous linux versions (repeats above two options, IDK whats up with that!), memtest, memtest (some different numbers), windows, windows recovery. When I hit the first option it goes to the ubuntu loading thing, which I thought was only on the CD... it then gives me a black screen adn does nothing. I can tap the power button and the thing you see when you boot off the CD (with the "checking.... state   [ok]") then it says "unmounting weak filesystems" and "halting" or something.... It flashes so quick I can't read it. It then shuts down. When I go into Ubuntu Recovery, I can run all the checks and nothing comes back. I booted into low graphics mode and it worked. What do I need to do?

---

### Post by Ardillo on 2011-08-15
Maybe you can try to boot in low graphics mode

Then try to connect to the internet en type this in the terminal
[PHP]apt-get update[/PHP] and hit enter, then do
[PHP]apt-get upgrade[/PHP] hit enter again.

Maybe it helps to check for some new drivers.

greetz

---

### Post by Lucypie on 2011-08-15
Well, this is the results of that...

alyssa@alyssa-HP-G62-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alyssa@alyssa-HP-G62-Notebook-PC:~$ 


I am going to real quick try some things before I restart just to be sure...

---

### Post by Lucypie on 2011-08-15
Okahy. Nothing worked so far. Ran a bunch more things, reconfigured everything a few times (using recovery) and I found the error in a log...

"Fatal startup error: No screens" 

Uhhh... That would explain the black screen, but why? How to fix?

EDIT: I just restored the failsafe xorg file, started x and got this error

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.



..... 

Going to restart....


EDIT! Fixed! :D

---

