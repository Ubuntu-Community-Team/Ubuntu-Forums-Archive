---
title: "How Do I Wipe the Hard Drive?"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by elraymundo on 2009-08-23
Hi everyone,

I have 9.04 running on a machine as the sole OS. I'd like to compeletly wipe the hard drive and re-install from an ISO. I have the ISO image burned ot disk. How do I wipe the hard drive clean?

Thanks!

---

### Post by NinjaNumberNine on 2009-08-23
I am the MASTER at wiping hard drives (lots of experience, to be sure)
For one, why do you need to wipe out hard drive before reinstalling? Just run the Live CD and choose "use entire disc" and the installer will reformat the hard drive. 
BTW, people call me R.I. ("reinstall" for my lack of ability to keep my system stable) :lolflag:
Any questions, keep posting!

---

### Post by celthunder on 2009-08-23
> **elraymundo said:**
> Hi everyone,

I have 9.04 running on a machine as the sole OS. I'd like to compeletly wipe the hard drive and re-install from an ISO. I have the ISO image burned ot disk. How do I wipe the hard drive clean?

Thanks!

You could just delete the partitions and then recreate them, it pretends the old data isn't there, otherwise you could zerofill it with dd.

---

### Post by jerrrys on 2009-08-23
really don't need to for a reinstall, but you can use one of the built in programs or

[http://www.dban.org/](http://www.dban.org/)

---

### Post by elraymundo on 2009-08-23
Thanks for the great post. I needed a laugh after the furstration I'm having. :)

I did a reinstall in the same way you mentioned, but it seems to have "remembered" some old settings from the previous install. Perhaps I chose a wrong option? Anyway, I want to re-install in hopes that my machine will stop locking up and that Flash will work in Firefox again.

So teach me, sensai, how to obliterate this hard drive so I can start fresh. :)

---

### Post by elraymundo on 2009-08-23
What's DD? Sorry, noob here. :)

---

### Post by porchrat on 2009-08-23
> **elraymundo said:**
> Hi everyone,

I have 9.04 running on a machine as the sole OS. I'd like to compeletly wipe the hard drive and re-install from an ISO. I have the ISO image burned ot disk. How do I wipe the hard drive clean?

Thanks!

You need to be a little more specific about what you mean by "wipe the hard drive clean".

Assuming you mean that you just want to start fresh, but that there is no particularly sensitive information on the drive that you wouldn't want someone else being able to recover then I suggest you merely format the drive before installing the next OS.

The problem with simply doing that is that all it does is reorganise the parts of the drive that tell it where all the original information is. That information is not gone, you just can't see it and as you use the drive the old information is slowly overwritten. A person experienced in data retrieval would be able to get that information back again if he/she had access to the drive.

An alternative is to boot the machine with a liveCD, mount the drive and then write over it with random characters or the number '0' (there is a script that generates random numbers that people normally use for this called "random", though I forget where it is located). Writing over all the old info with '0' is called zeroing the disk, but there are conflicting theories as to whether or not that actually wipes all the info off the disk.

I have tried using the random script to write over a disk before, but in my opinion if there is nothing sensitive on the disk then it is just easier to format the disk again before you install. If there is no important information on the disk, or you are positive that no one will ever get ahold of the disk to get information off it then it really is the easiest thing to do and that information is then beyond the reach of the average computer user as only those with knowledge of data retrieval would be able to access the old data.

---

### Post by porchrat on 2009-08-23
> **elraymundo said:**
> Thanks for the great post. I needed a laugh after the furstration I'm having. :)

I did a reinstall in the same way you mentioned, but it seems to have "remembered" some old settings from the previous install. Perhaps I chose a wrong option? Anyway, I want to re-install in hopes that my machine will stop locking up and that Flash will work in Firefox again.

So teach me, sensai, how to obliterate this hard drive so I can start fresh. :)

That happened to me once.

I'm guessing that you didn't select the checkboxes in the "format" column. If you want a truly fresh install then select that checkbox for each new partition.

---

### Post by elraymundo on 2009-08-23
I would be happy with formatting the drive and then re-installing from the 9.04 ISO. If I boot from the 9.04 ISO is there an option to format the HD before I install the OS?

---

### Post by celthunder on 2009-08-23
> **elraymundo said:**
> What's DD? Sorry, noob here. :)

Lets you copy information from 1 sector to another EXACTLY as is.  Example would be (taken from linuxquestions.org btw to make sure I got it right).

dd if=/dev/zero of=/dev/<drive> bs=1M

---

### Post by jerrrys on 2009-08-23
**DD   **[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by elraymundo on 2009-08-23
So what happens if I run *dd if=/dev/zero of=/dev/<drive> bs=1M* on my Linux partition? (There is only one partition on the drive.)

---

### Post by jerrrys on 2009-08-23
post #2

[http://ubuntuforums.org/showthread.php?t=1219025](http://ubuntuforums.org/showthread.php?t=1219025)

---

### Post by elraymundo on 2009-08-23
Thanks! I'll give it a shot in just a little bit. Hopefully I come back here with happiness and joy.

---

