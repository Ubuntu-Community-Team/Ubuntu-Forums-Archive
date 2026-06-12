---
title: "I have a few questions"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by tedygram311 on 2010-09-25
I am not sure if I would consider myself a beginner of not so I just went ahead and will say that I am because I haven't had linux long.  With that said, I tried to install readahead to shorten boot time, and I have also made my windows partition mount automatically through fstab.  I say that because when my computer loads up right before the login screen comes up these show their face, I am not to worried about it I am just curious of whether or not my computer is killing itself. =)

```
init: Failed to spawn ureadahead main process: unable to execute: No such file or directory

[          6.798431] sd 9:0:0:0 [sdc] assuming drive cache:write through
[          6.798702] sd 9:0:0:0 [sdc] assuming drive cache:write through
[          7.342029] shpchp 0000:00:01.0 cannot reserve MIMO region
```there was another one of the assuming drive cache things but I didn't get it all down in time.  Also is there a file that I could have pulled up to bring these errors or whatever they may be up to see in gedit or something like that?

---

### Post by Bucky Ball on 2010-09-25
No killing going on. Readahead just not loading. Unfortunately I have never used it so can't help with that but you could start by investigating why it can't reserve any space to load at boot.

" No such file or directory" suggests to me readahead is either not there or is and your system is looking in the wrong place but obviously not finding.

---

### Post by tedygram311 on 2010-09-25
Do you know anything about the MIMO region, I just reformatted everything because I was getting tired of somethings but long story short, I had linux before the reformatting and it always said the same thing.

---

### Post by sandyd on 2010-09-25
> **tedygram311 said:**
> Do you know anything about the MIMO region, I just reformatted everything because I was getting tired of somethings but long story short, I had linux before the reformatting and it always said the same thing.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577842)

---

### Post by tedygram311 on 2010-09-25
<--- n00b

haha but really I am assuming that it means that they know about it but haven't done anything about it yet.

Also are the numbers before that where it is on my hd?

---

