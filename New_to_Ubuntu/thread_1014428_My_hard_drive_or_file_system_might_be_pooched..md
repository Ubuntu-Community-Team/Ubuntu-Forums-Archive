---
title: "My hard drive or file system might be pooched."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by BlocknBleed on 2008-12-17
Is there any way to check? I tried to install 8.10 and later Fedora and they both failed saying either the hard drive might be broke. 
Is there a way to check it from the live cd?
I'm not getting any luck with fsck.

---

### Post by taurus on 2008-12-17
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by bumanie on 2008-12-17
Try > sudo badblocks -s -v -c 1024 /dev/sdxfrom a live cd, replacing the x with your hard drive letter eg /dev/sda It should output results in terminal

---

### Post by RJARRRPCGP on 2008-12-17
> **BlocknBleed said:**
> Is there any way to check? I tried to install 8.10 and later Fedora and they both failed saying either the hard drive might be broke. 
Is there a way to check it from the live cd?
I'm not getting any luck with fsck.


Is Ubuntu hanging with the text, "Buffer I/O error" being scrolled. 
Then likely loops that message? (And likely locks up).

That's a symptom I look for when the HDD has been unstable.

 Wouldn't be majorly surprised if the HDD is bad if you get the dreaded "Buffer I/O error" error message. 

I gotten that error message before when I had a hard disk drive that looked like it was going to be unstable.

---

