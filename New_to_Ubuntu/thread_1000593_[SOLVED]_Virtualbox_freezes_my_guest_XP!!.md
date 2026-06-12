---
title: "[SOLVED] Virtualbox freezes my guest XP??!!"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-12-03
I opened up my guest Windows XP using Virtualbox on my host 8.10 recently after not using it for nearly 2 weeks.  Since then there have been a lot of updates to 8.10.  Not sure if one of those updates is the cause.  When I press the start button to open up Windows XP, it loads to the desktop smoothly.  But seconds after the desktop appears, it seems that there is some loading (not quite sure of the terminology) still going on because my HD light keeps flickering for about 10 minutes.  While this is going on, my mouse is frozen on the desktop forcing me to do a hard shut-down.  Even after the flickering of my HD light is off, my mouse is still frozen.  What should I do???? I already tried "sudo apt-get build essentials" to see if the kernel needed to be updated, but that doesn't work.  I've reinstalled Virtualbox via their website but that isn't the problem either.

Thank you for your help.

---

### Post by FAMUgolfer on 2008-12-03
I'm a dumdum.

There was too much memory allocated to XP.

I adjusted it to a base memory of 256mb and now all is good!!

I love how as soon as I make a post I solve it on my own in a matter of moments.

---

