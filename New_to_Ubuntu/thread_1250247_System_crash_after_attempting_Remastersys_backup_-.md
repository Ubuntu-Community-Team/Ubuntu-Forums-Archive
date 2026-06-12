---
title: "System crash after attempting Remastersys backup - tips on data recovery?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by texla on 2009-08-26
Hey - this is a fairly new user here. I thought I'd have some fun making a backup that worked as a live CD and ended up with a crash! After trying to use Remastersys to create a live CD to backup my Jaunty setup, various problems have occured which led to my system completely crashing. First, the backup tried to use all of my data and it created a file that was 32 GB - not good. Then I tried the dist method and it went to a 16GB file - also not good. 
Now tmy Ubuntu system won't load at all - it says many things are missing and ends with a phrase about a "**kernel panic**".

I'd just assume do a complete reinstall and start over - although I don't see myself using Remastersys anytime again soon - but I thought I'd find out if there was anything I could do to recover the data first. The Ubuntu recovery mode won't load either by the way.
Now there is a good amount of stuff on this drive I would prefer not to erase in a reinstall but if it has to be done, so be it. I just wanted to see if there was a way to access any of it on the hard drive from the live CD or maybe from this rescue Live CD [System Rescue CD]("http://www.sysresccd.org/Main_Page")?

---

### Post by zerhacke on 2009-08-26
I'm assuming that since you had a 16GB dist ISO you tried to write the ISO to the same disk that the ISO was found on.

You can't do that.  You can only dd write to a disk that is not currently mounted.  Given that you can't put 16GB of data on a DVD and almost nobody has a blu ray burner, I can only assume you tried it from the drive you were currently booted into.

---

### Post by texla on 2009-08-26
> **zerhacke said:**
> I'm assuming that since you had a 16GB dist ISO you tried to write the ISO to the same disk that the ISO was found on.

You can't do that.  You can only dd write to a disk that is not currently mounted.  Given that you can't put 16GB of data on a DVD and almost nobody has a blu ray burner, I can only assume you tried it from the drive you were currently booted into.
Yep, I'm now aware of all of those issues with how I used Remastersys - I'm actually not looking for any more how to's for that program.  I would however  like to deal with the dead system now as best as I can.  Is there anyone who knows ways to get at files from an ubuntu system that crashes or even how the best way would be to go about a reinstall?

thanks!

---

### Post by mike555 on 2009-08-26
I had trouble using remastersys with an Ubuntu install that had Wine installed , I don't know if that's your case , but thought I'd mention it ........... maybe others can confirm ...
  or maybe that's not your problem ?

---

### Post by mike555 on 2009-08-26
Might be best to backup your files to a USB or whatever using a live cd , then reinstall ..

---

### Post by texla on 2009-08-26
> **mike555 said:**
> Might be best to backup your files to a USB or whatever using a live cd , then reinstall ..
Thanks Mike!! I just found a post that talks about using the livecd to access the home from my ubuntu install - so I'm sorting that stuff out now onto my usb - whew! found info here:
[http://ubuntuforums.org/showthread.php?t=1250306](http://ubuntuforums.org/showthread.php?t=1250306)

 I wonder if there's any folder or any files with system info in them that I could save from this install that would help me get my new install up and running faster? 

As for Remastersys - tons of problems on my end - wine could be one of them.  My main concern is that the all to simple GUI on the current version failed me as well as the (Remastersys forums and FAQs) - in giving any real warnings about how to use it properly and the potential hazards.  I was a bit worried about it because it looked so easy from all the info I read and I figured it would be a quick uninstall if I didn't like it.  Man, what happened was totally a surprise!  Not something I would recommend for a user without a lot more experience and tons of backups and external drives available.  which brings me to my initial problem of not finding any reliable ways of doing backups easily - but I'll deal with that when I'm up and running again.... still love Ubuntu and will do more data backups from now on to make this less of a pain - also probably will stay with the synaptic approved programs for a while - maybe... :) 

I'm going to try and focus the discussion on the reinstall with a new thread, hope that's ok: [http://ubuntuforums.org/showthread.php?t=1250386](http://ubuntuforums.org/showthread.php?t=1250386)

---

### Post by texla on 2009-08-26
OK, strange enough as this all goes, I attempted the earliest recovery Ubuntu boot possible during the GRUB boot stage and it restored my complete system I think:
Kernel 2.6.28 -11

.  But I can see in my system monitor that there is no SWAP being used anymore.  Any ideas as to what I should do now?  I'm thinking about trying the reinstall now from the newest Ubuntu and see what that does... 
Kernel 2.6.28 -15
- didn't work same errors: Kernel panic - not syncing

but did get this one to recover:
Kernel 2.6.28 -14

---

### Post by texla on 2009-08-26
Well it appears the main problem with this was my lack of space on the root partition to deal with the Remastersys ISO - especially since it was too large of an ISO to begin with.  Now I know and use Remastersys all the time!  But I always leave a lot of room and keep the home folder low in size whenever possible/:)

---

