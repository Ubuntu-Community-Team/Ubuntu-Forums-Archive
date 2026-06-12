---
title: "Complete Ubuntu Fail - Requres manual fsck?"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by den160593 on 2009-09-29
Hi,

My dual boot Ubuntu / WindowsXP boot recently failed. I've been using Ubuntu fine since mid 8.10 release no problems, then all of a sudden it has just failed. Here is a transcript of the error message I get when running Ubuntu in recovery mode (normal mode fails and says run in recovery... lucky have another comp to write out exact text).

> /dev/sda9 contains a file system with errors, check forced
/dev/sda9: Inode 873837 has illegal block(s)

/dev/sda9: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (ie, without -a or -p options
fsck died with exit status 4


It then gives me some vague instructions, that I can type out, but they're long :(, so i'll do so if needed. I'm a fairly bash illeterate so I don't know what to do with the fsck command.

Any instructions and guidance on this would be welcome, or if there is another solution to getting Ubuntu it would be great. I still have my liveCD.

Cheers!
-den

---

### Post by bruno9779 on 2009-09-29
The title is very sensationalistic, It should have read :

[SIZE="3"]COMPLETE HARD DISK FAILURE[/SIZE]

---

### Post by misfitpierce on 2009-09-29
I cant say 100% as I have never actually had to really use fsck except maybe once waaaayyyyy back. Although there is a thread that goes into some detail on how to run and use it and seemed to help this one guy... Check it out see if it helps you any... Sorry I can't be of more help atm.

[http://ubuntuforums.org/showthread.php?t=428406](http://ubuntuforums.org/showthread.php?t=428406)

---

### Post by den160593 on 2009-09-29
bruno, it's not the harddisk. My Windows install still works.

misfitpeirce, thanks for the reply. But how do i run the terminal (or equivalent). Do i have to enter ubuntu in text mode? or can i do it from safe mode where i'm in now? And are you sure that's what my erroris asking me to do?

Thanks

---

### Post by misfitpierce on 2009-09-29
RUN fsck MANUALLY. (ie, without -a or -p options is what your readout says... So I would guess you need to run fsck and you can hit esc when grub is booting and hit boot into safe mode then hit root terminal and enter in the commands from other thread maybe with or without the -f command which is force, try it without first. fsck is just check disk basically which will check for errors and such and the other thread just explains some commands on it... think you can actually enter fsck --help in terminal also for readout of other commands and what they all do also... But from your read it says to run it manually so I would say yes.

---

### Post by misfitpierce on 2009-09-29
Also if you can get into windows partition... maybe try defragging your HDD... I don't have experience dual booting as I don't run windows at all but perhaps that may clean up some crap cluttered around. I am not 100% if super fragmentation can cause errors on Ubuntu side although I would think so if on same HDD regardless since in my opinion windows is sloppy with that NTFS format.

---

### Post by joyson20 on 2009-09-29
try typing the command fsck on the same screen after u log in...initially as you start it might ask you to login(this woud look like the terminal kind of thing)...and once you do that, in the next line type "fsck" and press enter...this worked for me earlier when i had similar problems....

---

### Post by den160593 on 2009-09-29
Thanks heaps for advice misfitpierce. I'd prefer not to try anything on Windows install just 'incase' it stuffs up as well :(

It says I can use bash on safe mode. So i typed in /dev/sda9 fsck

However it gave me error:
bash: /dev/sda9 Permission Denied

I'm probably doing something wrong


Do i have to do: "sudo umount /dev/sda9" first? If so, what doesn't unmounting do? (I'm looking at [http://ubuntuforums.org/showthread.php?t=428406](http://ubuntuforums.org/showthread.php?t=428406))

Thanks heaps!

---

### Post by theozzlives on 2009-09-29
Boot off the Live Cd and go to the terminal and type:
```
fsck /dev/sda9
```

---

### Post by theozzlives on 2009-09-29
> **bruno9779 said:**
> The title is very sensationalistic, It should have read :

[SIZE="3"]COMPLETE HARD DISK FAILURE[/SIZE]

Very helpful... NOT!

---

### Post by bruno9779 on 2009-09-29
> **den160593 said:**
> bruno, it's not the harddisk. My Windows install still works.

misfitpeirce, thanks for the reply. But how do i run the terminal (or equivalent). Do i have to enter ubuntu in text mode? or can i do it from safe mode where i'm in now? And are you sure that's what my erroris asking me to do?

Thanks

Your windows partition works, but the Ubuntu one doesn't. This is a HDD failure (minor or major I wouldn't know).

FSCK : *The system utility fsck (for "file system check") is a tool for checking the consistency of a file system in Unix and Unix-like operating systems such as Linux.*

---

### Post by den160593 on 2009-09-29
Thanks for replies.

I ran 'fsck /dev/sda9' from my LiveCD. It's doing something now, I'll edit this with results. 

It's doing Pass 1D: Reconciling multiply-claimed blocks

Thanks once again!

---

### Post by misfitpierce on 2009-09-29
Hope it works :p

---

### Post by den160593 on 2009-09-29
It says there are 89 multi claimed blocks. It's only option is for me to clone them. Should I do this, and what does this mean? Thanks again!

---

### Post by misfitpierce on 2009-09-29
If its the only option to get it working then probably... Look at this thread

[http://ubuntuforums.org/showthread.php?t=96133](http://ubuntuforums.org/showthread.php?t=96133)

That one person just said yes to everything and got it working... I mean its up to you... It may erase an application or something at worse or maybe even mess it up at the very worst, but if you don't then you may need reformat from whatever this was caused by. I would say yes but its up to you... Sometimes chances must be taken. Try googling it first on the cloning thing to try and find info on it and if you cannot anywhere and are unsure then maybe take the chance. I have helped as far as I know to. Goodluck and sorry I cant be of more assistance!

---

### Post by misfitpierce on 2009-09-29
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/209416](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/209416)

The cloning thing worked for this guy... So perhaps it will work for you!

---

### Post by den160593 on 2009-09-29
Works! Wonderful, thanks heaps misfitpierce and others!!!

---

### Post by misfitpierce on 2009-09-29
> **den160593 said:**
> Works! Wonderful, thanks heaps misfitpierce and others!!!

Whew... thank god... Glad to hear you got it fixed and that I was able to help you the best I could with others. Got to love having a 24/7 large community with Ubuntu :p . Alright well keep enjoying Ubuntu and don't ever get frustrated! :p

Also in thread tools at top you should mark as SOLVED! Thanks again for bearing with me through the limited help I could offer! :P

---

