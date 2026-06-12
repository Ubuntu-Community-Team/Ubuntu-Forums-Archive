---
title: "mount of filesystem failed-can't start Ubuntu"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by pottzie on 2010-01-15
I'm getting a message that "mount of filesystem failed", and that a maintenance shell will now start, but nothing happens. Some of what shows up when I try the recovery option is "mountall:fsck/ [385] terminated with status 4" and "init:mountall main process [377] terminated with status 3." I also saw a "710" show up as I shut it down.
 I'm writing this from a live cd, and have tried to get the terminal to open, but I can only  get the terminal that's on the cd, so I'm kinda screwed as far as inputting anything into the terminal as far as I can tell.
 Anyone (smarter than me) know what I should do?

---

### Post by ubudog on 2010-01-15
> **pottzie said:**
> I'm getting a message that "mount of filesystem failed", and that a maintenance shell will now start, but nothing happens. Some of what shows up when I try the recovery option is "mountall:fsck/ [385] terminated with status 4" and "init:mountall main process [377] terminated with status 3." I also saw a "710" show up as I shut it down.
 I'm writing this from a live cd, and have tried to get the terminal to open, but I can only  get the terminal that's on the cd, so I'm kinda screwed as far as inputting anything into the terminal as far as I can tell.
 Anyone (smarter than me) know what I should do?

You can access the hd via the terminal on the livecd by typing ```
mount /dev/sda1/
```

---

### Post by pottzie on 2010-01-15
Thanks, I'll try it. There was a post somewhere about fixing the filesystem mount, but without access to the terminal I was lost. Now to see if I can dig up that post!

---

### Post by pottzie on 2010-01-15
No dice. I got:"mount: according to mtab, /dev/sda1 is already mounted on /media/PRESARIO_RP
mount failed"

---

### Post by ubudog on 2010-01-15
> **pottzie said:**
> No dice. I got:"mount: according to mtab, /dev/sda1 is already mounted on /media/PRESARIO_RP
mount failed"

Do ```
ls /media
``` and post the results.

---

### Post by pottzie on 2010-01-15
Here's what I got:
 
ubuntu@ubuntu:~$ ls /media
PRESARIO  PRESARIO_RP

---

### Post by ubudog on 2010-01-15
> **pottzie said:**
> Here's what I got:
 
ubuntu@ubuntu:~$ ls /media
PRESARIO  PRESARIO_RP

It looks like your computer only has windows installed on it.  Maybe start the install from the live cd and select the "Install Ubuntu next to the other operating systems" or something like that.  Then once it's done installing reboot and see if it works.  Hope that helps!

---

### Post by pottzie on 2010-01-15
Well, I got it to work....
 Tried to reinstall from the live cd, but things got ugly when Gparted wanted to know where my boot partition was. If you've ever stared blankly at a command prompt that asked if you liked playing "Eenie, meanie, miney mo..." with your boot loader, or worse decided that lady luck is going to come to the rescue and whatever you tell it to do will work, well....
 I saw that my swap was the size of a small state, so I shrank it. But before I did that, I thought better of it and decided not to, hitting the cancel button. Gparted obliged by going ahead and shrinking it to the size I'd specified before I chickened out. Nice.
 At that point I called it quits before I really screwed things up, and got out my Gparted boot disc and made the swap smaller, and gave the Ubuntu partition some more elbow room. When Gparted runs, it says that it checks files, and fixes them if it can. I don't know if that's what happened, but when I rebooted, Ubuntu loaded up like it's supposed to. 
 God watches out for fools.

---

