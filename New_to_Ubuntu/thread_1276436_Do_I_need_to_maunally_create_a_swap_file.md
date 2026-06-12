---
title: "Do I need to maunally create a swap file"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by donescamillo on 2009-09-27
Hi,

I read that from kernel 2.6 on there is no big difference between performance when using a swap partition or a swap file. I prefer a file since it can be resized etc. 
Now I created on my hard disk an Ext3 partition to accommodate Ubuntu. Since there is no dedicated swap partition, do I need to create a swap file (there are instructions howto) once I have installed Ubuntu or the installer will create one by itself (with some default parameters like size)

Regards,
donescamillo

---

### Post by Zoot7 on 2009-09-27
Not sure about using a swap file, but I've been using a swap partition of about 2GB for a few years now and my file copy/move operations are still a lot faster than they are in Windows.
I wouldn't imagine it would make a helluva a lot of difference, considering if you've enough RAM anyway, your machine shouldn't need the swap partition all that often.

---

### Post by philinux on 2009-09-27
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[http://en.wikipedia.org/wiki/Paging#Linux](http://en.wikipedia.org/wiki/Paging#Linux)

---

### Post by donescamillo on 2009-09-27
The Swap FAQ does not actually answer my question (unless I missed something). What I would like to know is:
When I install Ubuntu on a system that has no swap partition, will the Ubuntu installer create a swap file or I will have to do it once the installation is over?

Regards,
donescamillo

---

### Post by philinux on 2009-09-27
The automatic install will create a swap partition. I always use manual partitioning as I have /home on it's own partition. I specify 12gig for /. Also I have 2gig ram so I want a 2 gig swap for hibernate.

---

### Post by ~sHyLoCk~ on 2009-09-27
> **philinux said:**
> The automatic install will create a swap partition. I always use manual partitioning as I have /home on it's own partition. I specify 12gig for /. Also I have 2gig ram so I want a 2 gig swap for hibernate.

He is asking about swap **file** and not **partition**.

> **donescamillo said:**
> The Swap FAQ does not actually answer my question (unless I missed something). What I would like to know is:
When I install Ubuntu on a system that has no swap partition, will the Ubuntu installer create a swap file or I will have to do it once the installation is over?

Regards,
donescamillo

You have to manually create the swap file.

---

### Post by donescamillo on 2009-09-27
Thank you very much for your replies
Apparently I will have to create the swap file by myself (gulp)

BTW, I think that the Ubuntu installer should create the swap file by default without user intervention, at most asking what size it should be, otherwise a beginner may not even bother to do it, with all the consequences

Regards
donescamillo

---

### Post by ~sHyLoCk~ on 2009-09-27
> **donescamillo said:**
> Thank you very much for your replies
Apparently I will have to create the swap file by myself (gulp)

BTW, I think that the Ubuntu installer should create the swap file by default without user intervention, at most asking what size it should be, otherwise a beginner may not even bother to do it, with all the consequences

Regards
donescamillo

Ubuntu installer **does** ask you to create a swap partition, and being  beginner, he must follow this **suggestion**.

---

### Post by kevdog on 2009-09-27
Ive used a swap file before.  Partitioning is probably preferrable for performance, however I really noticed no noticeable difference (although I didn't benchmark anything).  This instructions seem very complete:

[http://www.techmetica.com/howto/add-a-swap-file-or-expand-existing-swap-space-in-ubuntu/](http://www.techmetica.com/howto/add-a-swap-file-or-expand-existing-swap-space-in-ubuntu/)
[http://groups.google.com/group/cwelug/browse_thread/thread/2e1aea2b6f298852](http://groups.google.com/group/cwelug/browse_thread/thread/2e1aea2b6f298852)
[http://ubuntuforums.org/showthread.php?t=54307](http://ubuntuforums.org/showthread.php?t=54307)

---

