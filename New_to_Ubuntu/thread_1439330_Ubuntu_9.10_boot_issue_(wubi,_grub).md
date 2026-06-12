---
title: "Ubuntu 9.10 boot issue (wubi, grub)"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by anitemp on 2010-03-26
Hi All,

I have Ubuntu 9.10 installed from inside Windows Vista (using Wubi) as a virtual disk. I was running three VMWare instances on Ubuntu when the system shutdown due to overheating. After booting I chose Ubuntu 9.10 for boot and it showed grub> prompt. 

'ls' command shows the following output (couldn't take a screen shot of it, so typing here manually):
(hd0) (hd0,0) (hd0,1)

I tried some commands (e.g. 'boot', 'linux') but all of them show 'kernel must be loaded first' message). I tried 'kernel' command but I don't exactly know what to pass to it.

Is there a way I can get the booting fixed? Also, is there a way I can at least recover the data in the virtual disk? (something like 'FUSE for Windows'??) 

Sorry if this is a repost, I found a few posts on same setup but describing a different problem.

Appreciate your help!

-anitemp

---

### Post by Paqman on 2010-03-26
Unfortunately one of the limitations of Wubi's virtual partition system is that it isn't tolerant of hard shutdowns. I'm not sure if it's possible to recover the data, but if you have a backup you may want to skip straight to reinstalling.

---

### Post by Dead Pixel on 2010-03-26
May I link you to [this]("http://ubuntuforums.org/showthread.php?t=1339203#10") and [this]("http://ubuntuforums.org/showthread.php?t=1339203&page=3#30") one? ;)

---

### Post by anitemp on 2010-03-26
> **Dead Pixel said:**
> May I link you to [this]("http://ubuntuforums.org/showthread.php?t=1339203#10") and [this]("http://ubuntuforums.org/showthread.php?t=1339203&page=3#30") one? ;)


Thanks Dead Pixel! Looks like my post IS a repost, sorry for that (just didn't find this with Windows Vista + Ubuntu 9.10 when I searched :duh:). 

Also thanks Paqman for looking into this!

---

