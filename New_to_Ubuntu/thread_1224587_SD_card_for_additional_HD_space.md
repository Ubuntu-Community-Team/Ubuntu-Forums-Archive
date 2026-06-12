---
title: "SD card for additional HD space?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by veg-o-matic on 2009-07-27
Hi, everyone.
I looked through the forums and saw some similar threads, but nothing exact, so will go ahead and ask.
 
I have a Dell netbook that has a 4GB SSHD and that's just not enough room. Even after dumping all the applications I'd never use, it's still 77% full and there's not enough room to install updates.
 
So I had an question. Is there a way to use a SD card for additional space on /? I guess my thought would be to extend the / filesystem to include both the build in HD and the SD card.
 
Really not sure how to do this and figured I'd ask the experts before I fry the whole thing.
 
Thanks in advance!
 
veg

---

### Post by philcamlin on 2009-07-27
i dont think you can do that :(

you mean combile the 2 disks as one right

you could put your music etc on the other sd card and use the other for ubuntu thats what i do

---

### Post by Taylor13 on 2009-07-27
It's possible, in theory at least. I did something like that in windows 2k using several SCSI 1gig hard drives. In essence it's a virtual striped raid. 

The only problem would be that you'd have to set it up before you installed anything to it, or even before formatting for that matter. I wouldn't have a clue how to do so under Linux.  :(

Going a different direction, have you tried clearing your apt cache out?  That would likely get you some more space if not.

---

### Post by dlmarti on 2009-07-27
You can do this with symbolic links.
Lets say you have an essential root directory with the minimal files you need day to day on it.  Inside the root directory (at various locations) you would have symbolic links to programs that only exist on the removable media.

For example....
/usr/bin/acroread would point to /media/extras/bin/acroread

Most of the time the link would be dead, and typing acroread would net you a file not found, but when you plugged in the media named "extras" you would get the program acroread.

Many embedded Linux products use this method for extending a root partition seamlessly.

---

### Post by veg-o-matic on 2009-07-28
Thanks for the help!
 
I have not tried clearing my apt cache.  Mainly because I've never heard of it!  How does one go about doing that?
 
veg

---

### Post by Taylor13 on 2009-07-28
You can clear the apt cache by running the following:

```
$ sudo apt-get clean 
```

---

