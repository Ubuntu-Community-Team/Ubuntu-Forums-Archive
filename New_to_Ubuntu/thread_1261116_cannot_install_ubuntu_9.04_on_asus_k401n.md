---
title: "cannot install ubuntu 9.04 on asus k401n"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by kolkhoz on 2009-09-08
When I try to run Ubuntu 9.04 Live CD on my asus k401n notebook , I get BUG Int 6 cr 2 followed by numbers and stuff. I know it's not a faulty CD. I tried to contact asus about it, they do not support ubuntu.

---

### Post by Jazzy_Jeff on 2009-09-08
Try installing with the Alternate install cd. It is text based but easy to follow [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate).

---

### Post by kolkhoz on 2009-09-08
thanks for prompt reply. i'm downloading it right now. if i use the alternate install, does that mean i won't be able to "preview" ubuntu without installing it?

---

### Post by Jazzy_Jeff on 2009-09-08
That is correct. But your post says that you cannot install ubuntu.

---

### Post by kolkhoz on 2009-09-14
Ok, i tried alternate ubuntu. that didn't work. i tried wubi. that worked installation-wise, but when i rebooted it looked like it was loading and stuff, then all of a sudden BUG Int 6 cr2.

Can it be that the machine is not compatible with ubuntu, or maybe a further BIOS update might fix something? 

Any thoughts welcome

---

### Post by Sef on 2009-09-14
> or maybe a further BIOS update might fix something? 

In [bug report #291158]("https://bugs.launchpad.net/ubuntu/+bug/291158"), the OP did a BIOS upgrade to resolve the problem.

---

### Post by kolkhoz on 2009-09-14
yeah, i saw that. i upgraded my BIOS (from ASUS website) a couple of days ago and it still doesn't work. is it possible i need a separate BIOS from intel website? i thought they were only for desktops.

also, on a related matter. i just uninstalled wubi from a partition (since it's not working and all), but it still shows up in boot menu. how could i remove it from there? it's a bit annoying.

---

### Post by ben2talk on 2010-06-23
Ok - a little late.

K401N laptop - I started using one a couple of weeks back, installed Ubuntu 9.04 and couldn't fix up networking - later on I tried a 9.10 alternate cd installation and it was fine. (after the 9.10 failed to get networking on the Desktop CD... strange)

Next - 10.04 Desktop CD failed to boot (graphics get mashed when the desktop arrives) This won't boot on my HP now (first fail since 7.04 guys - it's going  backwards)

10.04 alternate is a mess too. Install failed on the Asus laptop and the upgrade trashed my desktop - good that I kept backups and separate drives/partitions.

Next - use 9.10 alternate to install to both computers (HP desktop and Asus laptop).

Update, install the nVidia drivers, get compiz going to make sure it's working right.

My next step failed (upgrade using 10.04 alternate disk) - and a few hours later (to get back to this point) I simply did an upgrade online - that works fine.

Now I have 10.04 booting on HP desktop and Asus K401N....

However, I still don't have a live CD for recovery (just a beta 9.10 Desktop CD).

One more slip, and Ubuntu will be gone from both my computers - time to switch distro? What's the story?

---

