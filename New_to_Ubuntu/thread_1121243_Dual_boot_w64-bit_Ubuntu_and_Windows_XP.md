---
title: "Dual boot w/64-bit Ubuntu and Windows XP"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by eddski on 2009-04-09
I was thinking of reinstalling Ubuntu in 64-bit and wanted if it would or would not work with my current install of XP 32-bit. I have not given up on windows as I have not figured out my audio problem yet(that's for another thread). I wanted to try out a 64-bit OS and wanted to know if I would have any problems with it. I would appreciate any suggestions, opinions, tips etc. thanks in advance.

---

### Post by ddnev45 on 2009-04-09
I dual boot WinXp 32-bit and Ubuntu 64-bit without any problems. My method is to:

1. Each OS is on it's own harddrive
2. Install WinXp first
3. Intall Ubuntu and install grub on the MDR so it controls the boot options.

Take a look at the "Tips and Tutorials" thread for more details on dual bootting.

---

### Post by bodhi.zazen on 2009-04-09
64 bit Ubuntu is as easy or hard to use as 32 bit Ubuntu.

In general , if you have the hardware, go for 64 bit.

---

### Post by Lazy-buntu on 2009-04-10
I don't mean to hijack his thread, but I've been curious about 32 bit ubuntu vs. 64 bit too. I've heard that the increase in performance of 64 bit over 32 bit may not be worth the trouble of tracking down 64 bit apps, etc.

Is 64 bit support growing? I wouldn't mind trying it out with 9.04, but that means I'd have to start from scratch, and if it isn't a stellar improvement from 32 bit I don't think I'd go for it.

---

### Post by Son of William on 2009-04-10
> **eddski said:**
> I have not given up on windows as I have not figured out my audio problem yet(that's for another thread).

That's a bit cryptic but you may want to search this site for a discussion on a pulse audio bug in Intrepid.  I solved my problem just a few days ago so it is fixable.

As to your question:  having both 32 bit and 64 bit OSes installed on your system should not be a problem (so long as you can run the 64 bit OS).  The OSes do not (except in very rare circumstances) physically alter your hardware. So, go ahead with the plan of action outlined by ddnev45 above and enjoy!

---

### Post by Kareeser on 2009-04-10
> **Lazy-buntu said:**
> I don't mean to hijack his thread, but I've been curious about 32 bit ubuntu vs. 64 bit too. I've heard that the increase in performance of 64 bit over 32 bit may not be worth the trouble of tracking down 64 bit apps, etc.

Is 64 bit support growing? I wouldn't mind trying it out with 9.04, but that means I'd have to start from scratch, and if it isn't a stellar improvement from 32 bit I don't think I'd go for it.

Short of Flash in 64-bit, I haven't had to chase down a single 64-bit program. The repositories handled everything perfectly.

---

### Post by bodhi.zazen on 2009-04-10
> **Lazy-buntu said:**
> I don't mean to hijack his thread, but I've been curious about 32 bit ubuntu vs. 64 bit too. I've heard that the increase in performance of 64 bit over 32 bit may not be worth the trouble of tracking down 64 bit apps, etc.

Is 64 bit support growing? I wouldn't mind trying it out with 9.04, but that means I'd have to start from scratch, and if it isn't a stellar improvement from 32 bit I don't think I'd go for it.

Support for 64 bit not a problem and as I said 64 bit is on par with 32 bit.

In general you are not going to see a huge boot in performance unless you are doing something that is CPU intense.

---

### Post by Paqman on 2009-04-10
> **Lazy-buntu said:**
> 
Is 64 bit support growing?

I'm a massive 64-bit evangelist, and can confirm that most of the rumours of dodgy 64-bit support are false.

The only things i've ever bumped into that were 32-bit only was Google Gears (technically 32-bit only, but there is a simple fix available on the net) and the Amazon MP3 downloader.

---

