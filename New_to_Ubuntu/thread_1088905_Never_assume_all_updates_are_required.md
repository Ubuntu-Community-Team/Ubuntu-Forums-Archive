---
title: "Never assume all updates are required"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by uWitchDoctor on 2009-03-06
Well, I configured my ubuntu got everything working then went to bed. But before I went to bed I clicked on the (down arrow !) button saying there are hundreds of updates available and updated the lot...

Bad idea I guess because a few minutes ago I couldn't boot (just said >intramafs on he screen) :-({|=. Thanks to clonezilla I am back. So what exactly are these updates?

I guess know I know it's safe never to assume they are all needed.

How do I know what updates I need and what ones I don't? #-o

---

### Post by thtrgremlin on 2009-03-06
Don't fix what ain't broke.  Just deselect everything that isn't a security update, and you are going to be pretty safe.

and just to chck, do you have backports or proposed updates enabled? those are the only ones that have ever given me trouble

---

### Post by ScAwN on 2009-03-06
I've gotten every update available so far and have yet to have any problems. I would hope that Ubuntu would only tell you about updates that are safe. Are you sure it was caused by updates?

---

### Post by iKonaK on 2009-03-06
I knew that :) ... I now install only security updates and very rarely the others, since everything works grate it can only go down or remain the same if i update....

---

### Post by thtrgremlin on 2009-03-06
nothing is ever 100% safe 100% of the time. Everything has the potential to break something simply because there are oo many weird situations that just can't be accounted for.

When I used Windows long ago, XP SP2 completely killed my machine. Just something hat happens, just hopefully rarely. Laptops are the most susceptible because laptop makers will do anything to cut a corner / do something cheaper, and you just can't always know how they are going to do that.

---

### Post by uWitchDoctor on 2009-03-06
Scawn... You know what. No I did alot to my system before the reboot. I was just most scared of the updates because there was so many and I didn't want to read them all so I just installed them all.

However, I also did all updates on my eeepc aswell as this one and my eeepc lost the ability to connect to a wireless network, reinstalling the array.org linux-eeepc packages didn't help so I just started again.

but now I have looked for some very useful info

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

One paragraph that gets me is this:

> One of the beautiful things of Linux is that This'll work even on a running system; no need to screw around with boot-cd's or anything. Of course, if you've rendered your system unbootable you might have no choice but to use a live-cd, but the results are the same. You can even remove every single file of a Linux system while it is running with one command. I'm not giving you that command though!;)

Is that true? You can do back ups and restores or even go as far as deleting everything... on a LIVE system?

I don't need to be using clone zilla? can I just run the commands shown here and everything will be fine and dandy in terms of backing up and restoring?

---

### Post by st33med on 2009-03-06
Security updates are tested pretty well before they are launched.  Same thing for Ubuntu multiverse repositories.  Usually, new versions are not allowed in the repositories until the next version of Ubuntu.  Only bug fixes, minor changes, and security updates are allowed.

---

### Post by cmay on 2009-03-06
> **uWitchDoctor said:**
> Scawn... You know what. No I did alot to my system before the reboot. I was just most scared of the updates because there was so many and I didn't want to read them all so I just installed them all.

However, I also did all updates on my eeepc aswell as this one and my eeepc lost the ability to connect to a wireless network, reinstalling the array.org linux-eeepc packages didn't help so I just started again.

but now I have looked for some very useful info

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

One paragraph that gets me is this:



Is that true? You can do back ups and restores or even go as far as deleting everything... on a LIVE system?

I don't need to be using clone zilla? can I just run the commands shown here and everything will be fine and dandy in terms of backing up and restoring?

what he means is that there is one command that can remove all the contents on your harddrive in one stroke. that is not what you want to do.

---

### Post by uWitchDoctor on 2009-03-06
oh yeah, but I am wondering morea bout the back up and restore commands :)

On windows to back up and restore my harddrive couldn't be in use and had to use clonezilla, ghost, or something.

With this, I can do it all live?

So If i boot up one day and my wireless card isn't working because of something I installed but I couldn't determine what and if I luckily backed up at a point when it was working I could run the restore command and presumably reboot and everything will be good?

---

### Post by oldsoundguy on 2009-03-06
only issues I have had with updates is with the restricted drivers.  For that all that is needed instead of a hot boot is a shutdown boot .. in the past it took a re-install of the restricted driver in question, but not noticed the issue of late on any of the builds I run (buntu based).

---

