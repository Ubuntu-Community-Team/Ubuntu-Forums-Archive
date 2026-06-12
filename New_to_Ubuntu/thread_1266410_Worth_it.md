---
title: "Worth it?"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by krisarnold on 2009-09-14
Hi all!
I am the owner of a new toshiba satellite l305. It came with vista home basic(32bit). I adjusted partitions and installed jaunty on it. It came to my attention today that my CPU supports 64 bit. I've just got my ubuntu to look like vista to convert a friend or two. Is it possible to upgrade to 64 bit jaunty from the 32? Do I have to wipe out ubuntu and start over? Is it worth it? 
I'll be acquiring a copy of windows 7 tomorrow to replace my vista and would like to take advantage of my 64 bit. I will be upgrading from 2gb to 4 gb of ram. 
 
Also, just a thought. Evidently my laptop maxes out at 4 gb of ram 2 in each slot. Is this because of windows or the mother board? Inquiring minds would like to know what would happen if I put more than that in there...
 
Any and all help appreciated.

---

### Post by Nburnes on 2009-09-14
If your CPU can run 64bit then you should always choose it. You get more bang for your buck persay with your applications. I run 64bit Karmic on my laptop and I only have 4 GB of RAM.

---

### Post by NoaHall on 2009-09-14
You have to do a complete reinstall. It could be either. With 64 bit, you can use more than 3.4 Gb, without it you can't.
I would say yes on the 64 bit move to Ubuntu, but no as far as Windows is concerned. Windows 64 bit sucks.

---

### Post by zo3adams on 2009-09-14
The 4GB max is very likely due to the 32 bit OS, there's isn't enough address space in 32 bits to map out more then 3.5 GB or RAM.

There's no way to upgrade from 32 to 64 bit without a re-install, but you can make the re-install painless by preserving you're home directory at least (file system won't care what processor width is.)

I'd say go for it, but "worth it" is hard to answer, as you won't see an immediate obvious performance benefit, but you'll be using the same builds most people are and might get a benefit from quicker bug fixes and wider support in that sense...

---

### Post by juancarlospaco on 2009-09-14
Please use descriptive titles...

---

### Post by katakaio on 2009-09-14
> **zo3adams said:**
> 
There's no way to upgrade from 32 to 64 bit without a re-install, but you can make the re-install painless by preserving you're home directory at least (file system won't care what processor width is.)

Absolutely. If you move your /home directory to its own partition, the re-install will be a cinch. Plus, it's just plain wise to have /home on its own partition for a hundred reasons. This happens to be one of them :)

I also recommend going for 64-bit - just be sure to peruse the [64-bit forum ]("http://ubuntuforums.org/forumdisplay.php?f=343") and scout for any problems that might be a dealbreaker for you. I solved all of my 32-bit/64-bit issues by installing the **ia32-libs** package.

---

### Post by misfitpierce on 2009-09-14
I mean i've heard you could recompile a 64 bit linux kernel to switch it or whatever... Honestly i've never done it. When I switched to 64 bit I just reinstalled as it seems as a much simpler option. Just reinstall and 64 bit has noticeable speed differences. Much faster on many things and well worth it.

---

### Post by gordintoronto on 2009-09-14
> **krisarnold said:**
> 
Also, just a thought. Evidently my laptop maxes out at 4 gb of ram 2 in each slot. Is this because of windows or the mother board? Inquiring minds would like to know what would happen if I put more than that in there...
 


It is a motherboard limitation.

---

