---
title: "Jump Drive install."
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Zero++ on 2009-10-14
I want to make an Ubuntu intsall on a 4 gig flash drive and need some advice on a couple of issues. First I will be using both 64 bit and 32 bit computers. Is there a way to do this? I was thinking duelboot both on 2 partitions within the drive. Does anyone have a better suggestions?

---

### Post by coldReactive on 2009-10-14
You'll want to install a 32-bit version of Ubuntu onto the flash drive.

It's no use installing two different arches of the same OS onto a flash drive that small (32 GB I can see though. Yes, there are 32 GB Flash Drives.)

---

### Post by Zero++ on 2009-10-14
how will the 32 bit react to the 64-bit processor and extra ram?

---

### Post by coldReactive on 2009-10-14
It will just normally boot, it just won't see the extra 4+ GB of RAM, etc.

Also, running a 32-bit OS will not work on IA-64 processors.

---

### Post by Zero++ on 2009-10-14
then why install 32 over 64?

---

### Post by coldReactive on 2009-10-14
> **Zero++ said:**
> then why install 32 over 64?

Because 64bit OSes don't work on 32-bit (as shown by the nasty Windows Black Screen of Error when trying to install Windows 7 x64 on a 32-bit computer)

You'll also realize that when you install both Ubuntus, they won't show up as "x64" and "x86", they will both show up as Ubuntu 9.04/9.10.

---

### Post by Paqman on 2009-10-14
> **Zero++ said:**
> then why install 32 over 64?

Because any machine will boot the 32-bit version, but only 64-bit machines can boot the 64-bit. If you want universal compatibility, 32-bit is where it's at.

---

### Post by Zero++ on 2009-10-14
> **coldReactive said:**
> It will just normally boot, it just won't see the extra 4+ GB of RAM, etc.
 
Also, running a 32-bit OS will not work on IA-64 processors.
  ok so 32 bit will run on most 64 bit processors just not this type?

---

### Post by coldReactive on 2009-10-14
> **Zero++ said:**
> ok so 32 bit will run on most 64 bit processors just not this type?

You need to know if your processor is IA-64 (Not the same as x86_64/amd64), if your 64-bit computer is indeed IA-64, then no, 32-bit will not run on it.

---

### Post by Zero++ on 2009-10-14
sweet. thanks for the help. The processor type shouldn't be a problem. I'll install and report how it goes!

---

