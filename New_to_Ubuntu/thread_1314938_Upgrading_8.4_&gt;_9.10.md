---
title: "Upgrading 8.4 &gt; 9.10"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by avaralom on 2009-11-04
Hi guys. 

I  want to make sure that I'm doing this properly, before I break something. My laptop currently dual boots Windows and Ubuntu 8.4. I'm looking to install 9.10 over top of my current Ubuntu install, but keep Windows (it comes in handy sometimes!). As far as I'm aware, doing a simple upgrade isn't an option for me, so I'd rather just go the clean install route.

The partitioner is confusing me. I can tell the Windows partition from the Linux one (NTFS and ext3, yes?), but when I select the ext3 partition that I already have, what next? I have the options of changing the file system, to format it and pick the mount point. Am I on the right track for what I want to do, even? D:

---

### Post by socool274 on 2009-11-04
Well, the way I understand it, upgrading through the update manager only modifies system files, it shouldn't mess with partitions at all. So, I think you are safe updating it through the package manager. But, I am not absolutely sure, so wait until someone else tells you the same or otherwise.

---

### Post by kansasnoob on 2009-11-04
You would have to use the manual partition option from the Live CD.

Or do a clean install.

Why do you want to upgrade right now?

(I assume you mean 8.04)

---

### Post by synicalx on 2009-11-04
For your Ubuntu partition; Yes it's ext3 (Ubuntu dislikes NTFS for some reason) and you won't need to reformat it or anything. One of the options should be "Mount Point", from memory you change that to "/" (minus the ") if it isn't already. I can't remember all the details from memory so check out [this link]("https://help.ubuntu.com/community/LiveCD?action=show&redirect=LiveCd") for tips. ;)

---

### Post by avaralom on 2009-11-04
Ah, that's great. Thank you :D

And shame on me for not checking the wiki first! 

@kansasnoob - Change of scenery!

---

### Post by snowpine on 2009-11-04
Manual partition is your friend. I would recommend ext4 filesystem, "YES" to format (this will wipe all current data), and / as the mount point.

Before you do any of that, however, I would recommend logging some serious time with a 9.10 Live CD to make sure you really want to upgrade. 8.04 is relatively stable and bug-free at this point; whereas if you read through these forums, a lot of users (including me :)) are having trouble with the brand-new 9.10 release.

---

### Post by avaralom on 2009-11-04
> **snowpine said:**
> Manual partition is your friend. I would recommend ext4 filesystem, "YES" to format (this will wipe all current data), and / as the mount point.

Before you do any of that, however, I would recommend logging some serious time with a 9.10 Live CD to make sure you really want to upgrade. 8.04 is relatively stable and bug-free at this point; whereas if you read through these forums, a lot of users (including me :)) are having trouble with the brand-new 9.10 release.

Thanks. ^^

I will certainly take that into consideration. I wasn't planning on installing it right away, I'll take some time to play around first.

---

