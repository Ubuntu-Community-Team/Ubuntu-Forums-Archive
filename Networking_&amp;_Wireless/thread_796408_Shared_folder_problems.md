---
title: "Shared folder problems"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by sxen on 2008-05-16
Right, I have two Ubuntu computers one running 8.04 the other on 7.10. I want to make a shared folder between the two computers so that I don't need to make two copies of photos and stuff. (Fairly easy right?) 

I first made a folder on Feisty and then tried to access it from Hardy, getting the message "unable to mount location, invalid reply."

I then tried making a folder on Hardy and got the same error message on the computer that was hosting the folder. (Though I could access it from Feisty which is odd).

Have I done something stupid here or does Hardy not like shared folders?

Thanks :)

---

### Post by Iowan on 2008-05-16
[Here]("http://ubuntuforums.org/showthread.php?t=793308") is a quick HowTo for sharing via SSH.

---

### Post by sxen on 2008-05-16
Thanks, this seems to have done the job. Though I'm still not sure why I can't access the shared files on my Hardy computer... Though it doesn't really matter now. :)

Thanks.

---

### Post by Iowan on 2008-05-16
I can't say I'm really intimate with the "why", but you seem to need to install an additional filesystem to share between machines - either NFS, SSH, or Samba (to name a few).  There are procedures to mount those file systems... details are around here somewhere.  If You'd prefer another way to share files, you can research the aforementioned filesystems. (Search button :) )

---

### Post by sxen on 2008-05-17
> **Iowan said:**
> I can't say I'm really intimate with the "why", but you seem to need to install an additional filesystem to share between machines - either NFS, SSH, or Samba (to name a few).  There are procedures to mount those file systems... details are around here somewhere.  If You'd prefer another way to share files, you can research the aforementioned filesystems. (Search button :) )

Yeah, well I just find it odd how one machine works fine when the other can't even mount the shared folder on it's computer! I'll see if I can fix it though I feel there is little point since SSH is working just as well as a shared folder would.

---

