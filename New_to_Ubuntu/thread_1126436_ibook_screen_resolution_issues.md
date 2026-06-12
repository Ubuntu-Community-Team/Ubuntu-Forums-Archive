---
title: "ibook screen resolution issues"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Monk22 on 2009-04-15
hey everyone,

i had previously been running xubuntu 5.something on this old ibook laptop so my friend could get to her email and such.  i had tried to upgrade to 6.0 but PPC architecture support had been discontinued.  anyway i clicked the ubuntu 8.04 LTS upgrade just to see if it would work, and it did!  everything seems to work perfectly except for the screen.  i attached a screen shot so i dont have to explain it.  im sure its just something with the x.org config or whatever but im useless with most linux stuff.  any help would be appreciated, just want to strech the screen to fit. [IMG]http://i120.photobucket.com/albums/o194/Monk22/IMG00009.jpg[/IMG]

---

### Post by llamabr on 2009-04-15
Ubuntu no longer supports the ppc architecture.  Things will just get worse and worse for you, until they don't work any longer.

I run debian lenny on my ibook, with no complaints.

What size screen does it have?  After installation, I always have to rerun:

 sudo dpkg-reconfigure -phigh xserver-xorg

to reconfigure the xserver.

This may solve your problem in ubuntu, too.

---

### Post by llamabr on 2009-04-15
Also, re-reading your post, it's a bad idea to go directly from 6 to 8.04.  You should do the intermittant upgrades, too, or else fresh install.

It's likely that other things are messed up, too, from your dist-upgrade.

---

### Post by DGortze380 on 2009-04-15
> **llamabr said:**
> Ubuntu no longer supports the ppc architecture.  Things will just get worse and worse for you, until they don't work any longer.


PPC Builds have community support.

Try hear, very helpful, and very stable. You shouldn't have any problems.

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

---

### Post by Monk22 on 2009-04-19
> **llamabr said:**
> 
 sudo dpkg-reconfigure -phigh xserver-xorg

ok, i tried that but it didnt seem to do anything.  ill head over to the ppc forums and see what i can dig up.  it appears to support 1024x768 but its only in 800x600 at the moment. thanks for the help though.

---

### Post by Monk22 on 2009-04-19
ok i ended up fixing it with [this thread]("http://ubuntuforums.org/showthread.php?p=7101957#post7101957").  thanks for pointing me over to the apple forums.  dont know how i didnt think to do that first. :P

---

