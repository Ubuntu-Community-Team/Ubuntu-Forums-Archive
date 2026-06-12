---
title: "Connecting to Windows Share"
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by Christopher_Stayne on 2016-01-21
Hello all,

Im what you could refer to as a total lubuntu/linux newbie.  Well, okay maybe I wouldnt go that far.  Ive been playing with it in VMs for a while running under VMWare.  Recently though I installed Lubuntu 15.10 on my Dell laptop as I want to make it my OS on my laptop as I dont have a Windows key for it.  

I have a desktop computer with Windows 10 Pro installed on it and have it set up as a file server for my residence.  One thing I am having trouble figuring out is how to mount my Windows share on my Lubuntu laptop.

Any ideas on how this is done?

---

### Post by Christopher_Stayne on 2016-01-23
Its kind of amazing that I have yet to get a reply to this.  

Anyway, I figured out how to mount the share.  However, as it is on a NTFS formatted drive I am having issues writing to the share.  Reading works just fine.  Any ideas?

---

### Post by bab1 on 2016-01-23
> **Christopher_Stayne said:**
> Its kind of amazing that I have yet to get a reply to this.  

It's probably not a good idea to chide the folks you are asking help from.  ;-)
> 

Anyway, I figured out how to mount the share.  However, as it is on a NTFS formatted drive I am having issues writing to the share.  Reading works just fine.  Any ideas?
More information is needed for anything more than a guess.  The format of the remote share partition is not relevant.  The share is mounted using SMB/CIFS formating.  The file system ownership and permissions must be declared at "mount" time.  The can't be changed after that.  With the share mounted post the output of this terminal command```
mount
```
Post the text between [noparse]```

```[/noparse] blocks to preserve the fixed width formatting.  This is easily do by clicking on the [SIZE=5]**#**[/SIZE] icon located at the top of the advanced reply editor.

My guess is you mounted the share as the root user and now the owner is root rather than your user login.

---

### Post by Christopher_Stayne on 2016-01-23
Thank you or your reply.  I think that is what is going on now that you mention it.  Im pretty sure I mounted it as root using the sudo command.  Ill look into it, may have to try unmounting it and remounting as my user.

---

### Post by bab1 on 2016-01-23
> **Christopher_Stayne said:**
> Thank you or your reply.  I think that is what is going on now that you mention it.  Im pretty sure I mounted it as root using the sudo command.  Ill look into it, may have to try unmounting it and remounting as my user.
Under normal conditions only root is able to mount the share.

---

### Post by Christopher_Stayne on 2016-01-23
> **bab1 said:**
> Under normal conditions only root is able to mount the share.
Yes, that is what I was just reading.  I found out how to set the owner as my user account though.  All it took was a simple addition of a single command.  Now I can both read and write.  Thank you very much for your input.

And before I was not trying to be snide, I was just stating that I was surprised it was taking so long to get a reply.  I guess I need to be more patient.  ;)

---

### Post by bab1 on 2016-01-23
> **Christopher_Stayne said:**
> Yes, that is what I was just reading.  I found out how to set the owner as my user account though.  All it took was a simple addition of a single command.  Now I can both read and write.  Thank you very much for your input.

And before I was not trying to be snide, I was just stating that I was surprised it was taking so long to get a reply.  I guess I need to be more patient.  ;)
You could have "bumped" the thread back to the top every 24 hours.  Sometimes your schedule is not other the same as others.

At this point the problem is solved.  Please mark this thread [**solved**]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

