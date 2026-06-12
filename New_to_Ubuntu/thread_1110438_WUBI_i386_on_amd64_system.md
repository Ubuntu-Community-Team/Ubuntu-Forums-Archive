---
title: "WUBI: i386 on amd64 system"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by jackmackenzie on 2009-03-29
Hi all, a strange question which I can't find an answer for anywhere:

I'm trying to install Ubuntu using Wubi on my system. I installed it previously and it detected that my system had amd64 architecture. I had allocated a small amount of space as it was purely experimental - however I like Linux and Ubuntu so much that I wanted a larger share of my hard drive to be dedicated to Ubuntu, so uninstalled Ubuntu with the intention of re-installing with a larger hard disk allocation.

However, on attempting to re-install, Wubi would not download the ISO again (I shouldn't have deleted it in the first place, or should have made some kind of backup, or something, but I didn't), so I manually downloaded the amd64 version.

This didn't work, so I tried all sorts of things, eventually trying the 1386 version, which this time worked! Ubuntu is now installed as the i386 version.

Why is this? And also - does it matter? I heard there's not actually that much difference in the capabilities of each version. Is this true?

I haven't yet booted into it so I'm not sure if it works (writing this from a slowly dying WinXP), I'll post a reply once I've tried it.

Thanks

Jack

---

### Post by Dejai on 2009-03-29
You can run the x86 architecture on an x86_64 machine with no problems. I am not sure what the deal is with WUBI maybe it just does not have support for 64 bit ubuntu and is only known to recognize the file name of the i386 ISO image. Another possible issue is your only running a 32 bit version of Windows, I am not sure if this would effect Wubi but then again I haven't looked into it. 

On the issue of how big a difference it makes it depends on the CPU, usually it won't make a very noticeable difference and i386 is the most widely supported architecture for Linux systems and sometimes it is even recommended to install i386 instead of x86_64 for beginners anyway as you don't have to deal with the range of issue that arise in x86_64 systems e.g Flash support. 

The only time I can imagine it really mattering is if you were doing very CPU intensive operations all the time e.g Video Rendering. 

I hope that answers your question.

---

### Post by jackmackenzie on 2009-03-29
Thanks for the info Dejai

I booted into Ubuntu perfectly successfully, I think I'll just leave it in that case. It's strange though that it worked with x86_64 first time but not second time... I'll just put it down to being 'one of those things'

Cheers

Jack

---

