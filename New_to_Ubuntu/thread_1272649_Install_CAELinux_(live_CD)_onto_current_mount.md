---
title: "Install CAELinux (live CD) onto current mount"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Gripp on 2009-09-22
ref [http://caelinux.com/CMS/index.php?option=com_frontpage&Itemid=1]("http://caelinux.com/CMS/index.php?option=com_frontpage&Itemid=1") to see what I'm referring to.

its been a couple of years since I've cracked open linux (unfortunately i rely on Autodesk products to much to use linux to the extent that I would wish) so please throw me as many bones as you can here - want to get back up to speed rapidly...

My problem is that I have graphical issues in the live boot method, and do not want to partition my workstations HD (its not mine to ruin, if that were to happen)
So I've opted for a Wubi style install.  However, this brings up the issue of how to install everything that comes with the CEAlinux package onto my full 9.04 install?

I've looked into installing the individual packages, but am finding that a number aren't included in aptitude or the standard add/remove progs app.  And I can't remember the install package that I used to prefer (please make sugg)

more than anything, however, is that I'm lazy\\\\ i mean strapped for time... and would prefer to be able to simply migrate the softs installed with the CAE package to my current install - any help would be very much appreciated.


edit: 
to be specific about the troubles with installing the packages individually - try figuring out how to install [http://www.salome-platform.org/](http://www.salome-platform.org/) - the very first soft in the [CAE package]("http://www.caelinux.org/wiki/index.php/Doc:GettingStarted")... as another user on this forum said "its not a walk in the park"


edit 2:
i just remembered that old skool (i.e. stand alone) wubi had the ability to port most any ISO and had some amount of information on how to do this.  from what I'm finding now however they do not support this functionality (it says it works with 8.10 ubuntu) 

and one know how to do this?

---

### Post by keplerspeed on 2009-09-25
In the long run, partitioning will save you a lot of hassles. I would encourage you to partition and install CAElinux. Remember, CAElinux is massive, especially with the salome-meca package.

What on CAE do you need? There is a standalone salome-meca package avaliable on the CAELinux website. I have used this to install salome and it was quite easy.

There is just so much stuff that comes with CAE, gigs of applications. So whats wrong with sticking with the liveCD session? Are you using the latest CAElinux based on ubuntu? In this case, what graphical issues are you having?

---

### Post by Gripp on 2009-09-28
My dual monitors are not supported is the main issue - I get one monitor flashing with all kinds of garbage.  fixing this using nvidea's driver requires restart.  more than anything however, I would just like a permanent install.  mainly for my work email access - I need to be able to readily respond to my work emails. and as I mentioned b4 this is my 'work'station, so I'm very reluctant to take the risks associated with partitioning, more than just pissing off the admin I have years worth of various softs that I have installed that I really don't want to have to find/install again.  

my thing is that their ISO just an overlay of 8.04 - so that vs of Wubi should work - but it will not recognize the ISO (i've tried renaming it to trick wubi) and insists on DLg a new iso..

as for manual installs - I really need a number of those softs, plus on trying to install salome I hit a dead end rather quickly.  and my thought is that if I have to go thru that much pain for just the first of many softs, then its not worth the time to figure that route out.  

[http://ubuntuforums.org/showthread.php?t=961645](http://ubuntuforums.org/showthread.php?t=961645) has some decent info one how to accomplish my issue.  and may be a ruote that I'll take, but I'm still looking for something simpler - again, b/c ubuntu 8.04 IS the OS, and wubi should be able to install it with some prodding.  

push comes to shove I'll get a second comp set up and use it dedicated - this is actually what our admin suggested.  maybe you can tell, I ***really*** don't want to partition.

---

