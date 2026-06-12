---
title: "problems dual booting"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Monark on 2010-01-09
Hello everyone.

I just installed Ubuntu 9.04 on my gf's laptop to dual boot it with her windows 7.

Now windows 7 won't start it gives me the following error-

D:\windows\system32\drivers\mountmgr.sys is corrupt

I have no idea what to do to correct the issue.

She misses streaming movies from netflix.

So any help would be very appreciated.

---

### Post by aaronp on 2010-01-09
> **Monark said:**
> Hello everyone.

I just installed Ubuntu 9.04 on my gf's laptop to dual boot it with her windows 7.

Now windows 7 won't start it gives me the following error-

D:\windows\system32\drivers\mountmgr.sys is corrupt

I have no idea what to do to correct the issue.

She misses streaming movies from netflix.

So any help would be very appreciated.

She can't stream movies from netflix on Ubuntu? :tongue:

Anyway...have you installed this as a separate partition or did you install it under Windows (i.e. wubi)?

---

### Post by Monark on 2010-01-09
Separate partition.

---

### Post by sandyd on 2010-01-09
ok. your not the first, so at least youve learned something new
Download this [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
run it
select repair

now remember this
DO NOT use the resizing tools on the ubuntu cd.
use the partitioning tools in windows.
windows will have these problems if it is resized by ubuntu.

---

### Post by aaronp on 2010-01-09
> **Monark said:**
> Separate partition.

Resizing the Windows partition using GParted in the Ubuntu installer is very good at creating issues on your Windows partition. Hopefully you can recover it using your Windows system discs or recovery partition.

---

### Post by Monark on 2010-01-09
Thanks a lot guys.

I had watched the videos on youtube on how to do it.

I forgot all about partitioning on windows first.

Thanks a lot.

---

### Post by aaronp on 2010-01-09
> **carlee said:**
> ok. your not the first, so at least youve learned something new
Download this [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
run it
select repair

now remember this
DO NOT use the resizing tools on the ubuntu cd.
use the partitioning tools in windows.
windows will have these problems if it is resized by ubuntu.

Sorry Carlee, started my reply before yours appeared but got distracted and took longer to hit Post (yours was more comprehensive too!). Must learn to stay focused...or wait longer ;-)

---

### Post by Monark on 2010-01-09
Thanks guys. I'm windows 7 again. I thought I would have to do something but I just started the computer with the recovery disc in the cd drive and it worked perfectly.

Thanks a lot guys.

---

### Post by Monark on 2010-01-10
After it fixed now the sound won't work in 7.

I re-installed the driver but the computer doesn't even acknowledge an audio device.](*,)

---

### Post by lidex on 2010-01-11
Laptop? Check your mute button. Or call Bill.

---

### Post by Monark on 2010-01-11
Yes, its a laptop. It's an HP dv6000 if that helps.

The mute button won't work. Its stuck in off mode. Even though sound works in Ubuntu. 

It says no audio device detected in windows.

---

### Post by lidex on 2010-01-11
Haven't used win7 yet but you might want to reset the bios to defaults and re-install chipset and mb drivers after that.

---

### Post by Monark on 2010-01-11
I know this is a very noobish thing to say but I don't know what BIOS is or how to get there.

This is pretty lame since it was working pre-recovery.

---

### Post by ranch hand on 2010-01-11
When you first boot up you get some kind of screen usually with the computer manufacturers logo on it.

Somewhere on that screen will be a couple of things;
1>Setup
2>Menu (or Boot)
They will have some key listed to hit after them.  You want "Setup".  On my Dell desktop it is F2 on an other box it was Esc.  You need to be quick on most of them.

---

