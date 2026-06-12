---
title: "Question on tidying up the Grub (hope that's right)"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Mike1962 on 2011-04-02
Hi,
Is there a way of clearing up the number of files on the screen where I choose which OS I boot from. Win XP doesn't even show on the list anymore till I scroll down. I presume they are all updates to the kernal?

Mike

---

### Post by fabricator4 on 2011-04-02
> **Mike1962 said:**
> Hi,
Is there a way of clearing up the number of files on the screen where I choose which OS I boot from. Win XP doesn't even show on the list anymore till I scroll down. I presume they are all updates to the kernal?

Mike

In synaptic package manager delete the older kernals and headers. When you execute the changes those entries will be removed from grub.

If you search the installed packages based on the release (eg 2.6.3x-xx etc) you should see all the relevant files (three, I think linux-image, linux-header, and linux header generic) for each release.

Do NOT remove your current kernel. Most people recommend that you also keep the previous kernel on the system as a backup.

If you forget which is the current release you are currently booting open a terminal and type 
```

uname -r

```

Chris

---

