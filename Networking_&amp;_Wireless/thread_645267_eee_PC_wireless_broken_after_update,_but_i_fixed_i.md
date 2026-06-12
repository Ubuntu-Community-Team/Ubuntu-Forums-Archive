---
title: "eee PC wireless broken after update, but i fixed it"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by bitter_mike on 2007-12-19
So I've got Gutsy running off my EeePC and recently, the Update Manager popped up, told me there were updates and as usual, I installed them without looking too hard. A couple of the updates had to do with the Kernel headers and after I did the reboot the Update Manager requested, my wireless card was no longer picked up. 

Thankfully, all I had to do to fix it was re-install the madwifi drivers exactly the same as I installed them before and the wireless card was detected on reboot. I thought I'd post this in case other people were running into the same problem after updating.

---

### Post by mckwant on 2008-04-25
Thanks for the post, and apologies, but how'd you do THAT?  My wired network interface doesn't seem to work either, so am I stuck getting the DVD(s) and reinstalling madwifi that way?

How quaint.

Thanks,
mckwant

---

### Post by bitter_mike on 2008-04-26
Did your ethernet connection stop working after you did an update or did it just not work out of the box? Because mine didn't work out of the box for some reason. I had to toggle the option in the bios a couple of times before it started to function correctly. But my updating of the kernel headers only screwed up my wireless.

You can still download the patch and the drivers on another computer and use a thumbdrive to move it over. That should work without a problem.
As to your wired, I have no idea why it would've suddenly stopped being detected by Network Manager, but I'd toggle the bios option a couple times.

---

### Post by mckwant on 2008-04-26
Thanks, figured it out.  I wasn't at my brightest last night.  Moved madwifi onto a flash drive, copied it over, set it up per the link below, and everything seems well again.

[http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_install_Ubuntu_Hardy](http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_install_Ubuntu_Hardy)

helped.  

Just got annoyed, and frustrated at the "upgrade" taking 24 hours to download, then breaking the most important part of the system.  I mean, if your umpc doesn't do wifi, what exactly is the point?

So thanks, anyway.

mckwant.

---

### Post by mckwant on 2008-04-27
And actually, it was this page:

[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly)

---

