---
title: "Pentium 1 w/ 32MB RAM in Lubuntu?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by willz06jw on 2010-10-26
Hi,

I have a few very low spec PCs I would like to load Lubuntu on.  I know that the Lubuntu system requirements are above the hardware I want to put it on.  What is the best way to suggest to the Lubuntu team/help the Lubuntu team lower the systems requirements for their OS?  

Tiny core even wants more RAM than I have!  Puppy and Puppy Arcade look fine, but they don't have the fantastic Ubuntu Repositories.

Thanks,
Willz06jw

---

### Post by LiamWilson on 2010-10-26
If you're saying that you have multiple PC's, why not take the ram out of some of them, and then put them in 1 pc. You might be able to do a minimal install of lubuntu then:

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal) Install and 64 Bit

If this isn't to your tastes, you can always contact the lubuntu team for more information:
[https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)

---

### Post by NightwishFan on 2010-10-26
You likely will not find a solution with awesome repositories for such a low spec machine. Even puppy and dsl might have trouble running. I doubt you could get a minimal debian running well at those specs either unless you are very apt.. with apt. :)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)
[http://www.debian.org/](http://www.debian.org/)

---

### Post by snowpine on 2010-10-26
A minimal text-only server install of Ubuntu requires 128mb of RAM, therefore it is unlikely Lubuntu (minimal Ubuntu *plus* the LXDE desktop environment) will run well with only 32mb.

There are some good articles about Linux on very, very old hardware at this blog: [http://kmandla.wordpress.com/](http://kmandla.wordpress.com/) For example, you may be able to get the old machine working as a torrent slave, music jukebox, etc.

---

### Post by willz06jw on 2010-10-26
Well crap, I just hated to think that Windiws 98 running the newest Firefox (with the help of KernelEX) would be a more capable system than Linux for my old spec PC. (Note: This only has been tried with a Celeron 64MB RAM computer and not the Pentium 32MB one).

Crud.

Thanks anyway for your help,
Will

---

### Post by snowpine on 2010-10-26
> **willz06jw said:**
> Well crap, I just hated to think that Windiws 98 running the newest Firefox (with the help of KernelEX) would be a more capable system than Linux for my old spec PC. (Note: This only has been tried with a Celeron 64MB RAM computer and not the Pentium 32MB one).

Crud.

Thanks anyway for your help,
Will

You're comparing apples and oranges. Windows 98 is 12 years old and obsolete (totally unsupported by Microsoft at this point) though of course it will run well on older hardware. Ubuntu (including its derivatives) is a modern, full-featured, bells-and-whistles operating system for 2010 hardware. There are many other Linux distributions that are better-suited for older hardware; please do read that blog I linked to in my previous post, as it has some excellent suggestions. :)

---

### Post by mcduck on 2010-10-26
> **snowpine said:**
> A minimal text-only server install of Ubuntu requires 128mb of RAM, therefore it is unlikely Lubuntu (minimal Ubuntu *plus* the LXDE desktop environment) will run well with only 32mb.

There are some good articles about Linux on very, very old hardware at this blog: [http://kmandla.wordpress.com/](http://kmandla.wordpress.com/) For example, you may be able to get the old machine working as a torrent slave, music jukebox, etc.

Minimal, Openbox-based setup of Ubuntu actually works just fine with less than 128MB, I have my lightweight system running with a decent 40MB memory usage. And that system even has extra stuff like xcompmgr runing for real transparency & drop shadows. :D

But that's still more than the 32MB the OP has, and if he actually wants to *do* anything useful with the machine 32MB just isn't going to do it these days. Simple web browsing would these days require more than that. The world just isn't the same as it was when such machines were sold..

If there's no way to add more RAM to the machine, it's not going to be useful as any kind of desktop machine. Maybe a music/file server or a computer for learning those CLI skills...

---

### Post by lavinog on 2010-10-26
I was under the impression that ubuntu kernels were compiled for i686 and would not work on pentium 1 anyway.

---

### Post by willz06jw on 2010-10-26
You are right.  Comparing Ubuntu to Win 98 isn't smart, but I was trying to focus on comparing Lubuntu to Windows 98 (it can run on Pentium IIs).  

I was just trying to see if there was a chance to get the requirments down on Lubuntu to fit my crappy old computer.

I haven't read the blog yet, I'll take a look.

Thanks for the help,
Willz06jw

---

### Post by NightwishFan on 2010-10-26
Lubuntu is the same core as Ubuntu. It does not matter which version you use. Lxde is probably too heavy for such a machine anyway.

---

### Post by TBABill on 2010-10-26
Way late to the discussion, but I just had to say this made me chuckle. I saw Pentium 1, 32MB RAM and just started to reminisce...Windows 95 just released, copying a bazillion floppy 3 1/2 disks to try it out before I spent money on my own copy, still needing DOS, and on and on. And to see the question about today's Lubuntu with that machine....just humored me a bit like trying to run Win 95 on an old 286 or something. We never had enough power, never had enough memory, never had enough storage and if you connected with a modem at 28.8kbps you were rocketing over the phone line.

---

### Post by willz06jw on 2010-10-26
You rich Yankees with your new-fangled eletric-brains :)

My machine may be 13 years old, but it's running strong!  

Lubuntu runs on a Pentium II, wouldn't you think a Pentium 1 isn't that much of a stretch?  I bet Tie-Fighter runs like a dream!

---

### Post by ST3ALTHPSYCH0 on 2010-10-26
This honestly sounds like a good opportunity to get much more intimate with Linux, and use Linux from Scratch to build EXACTLY what you need. I can tell you that even as far back as 8.04 will kernel panic during even a minimal install on 64 MB of RAM.

---

