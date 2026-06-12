---
title: "Conversion confusion"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by d1sc0rd on 2009-01-16
Hi,

relatively new to ubuntu

my PC has 4GB of RAM and im 99% sure im running the 64 bit version of ubuntu

system monitor, though, shows only 3.8 GiB available

is 3.8 GiB equal to 4GB?

Thanks in advance.

---

### Post by beastrace91 on 2009-01-16
3.8 Gigs is not the same 4 gigs, be sure your GFX card is not sharing memory maybe? And then check to be sure you did in fact install the 64bit OS

~Jeff

---

### Post by d1sc0rd on 2009-01-16
2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux


is x86_64 64 bit?

EDIT: 512 MB on graphics card

---

### Post by wilbbe01 on 2009-01-16
> is x86_64 64 bit?

Yes, that is 64 bit.

---

### Post by d1sc0rd on 2009-01-16
so whats up with system monitor telling me that i have 3.8 GiB ram?

---

### Post by wilbbe01 on 2009-01-16
I'm wondering if your hardware cannot actually physically support a full 4GB.  Does the full 4 show up in your BIOS?  If it does not show up correctly there you might try updating that if you think it should support 4.  Also, I don't know what you are running in Ubuntu, but I think the loss of .2 GB is very minimal.  I have 2 GB in my main box and I can have quite a lot of applications open and still have very little in use (like around 1 to 1.5).  I have 5 applications open right now and am only using 34.2%.  If it is working, and you don't notice you are regularly needing that last .2 I wouldn't worry about it.

---

### Post by wilbbe01 on 2009-01-16
Also, as someone else mentioned, your graphics may be shared.  Is this on a laptop or a desktop?  If it is a laptop that is very likely the case.  If in your BIOS you see mention of amount of memory to be used for shared video/graphics/or something, that is likely where your memory is going.  I assume you used Windows in the past, do you recall Windows showing 4GB of memory?

---

### Post by d1sc0rd on 2009-01-16
Thanks for replies

Im using a laptop, and yes when i ran windows it showed all 4GB

how do i get to BIOS to check?

---

### Post by wilbbe01 on 2009-01-16
When you first turn on your computer it says something about pressing a key to enter bios.  Depending on your manufacturer this might be the delete key, F2, or something else.  Dell is generally F2, while everything I have ever had is delete.  Once in there you can browse around and look at a lot of different settings.  However, you probably don't want to screw with anything in there as without things in there being right you don't have much of a computer.  

Maybe try this first......
What type of graphics card is advertised on your laptop?  Is there a sticker advertising?  If you don't see a sticker you might try typing the following command and looking posting it and we can tell you if your card is a shared memory card.

```
lspci
```

---

### Post by d1sc0rd on 2009-01-16
Thanks! F10 was BIOS

4092 MB of RAM if i remember right

---

### Post by 73ckn797 on 2009-01-16
It is normal in 64bit. I also have 4Gib memory but system shows 3.9.

Look around in the forums, it has been addressed before.

---

### Post by Old_Grey_Wolf on 2009-01-16
> **d1sc0rd said:**
> Hi,

relatively new to ubuntu

my PC has 4GB of RAM and im 99% sure im running the 64 bit version of ubuntu

system monitor, though, shows only 3.8 GiB available

is 3.8 GiB equal to 4GB?

Thanks in advance.

A GiB is not equal to a GB.

Storage devices like HDDs, DVDs, flash drives, and so forth use the definition of KB, MB, and GB, as 1 KB = 1000 bytes, 1 MB = 1000 KB, and 1 GB = 1000 MB. 

Therefore, when a device reports that it has 4 GB, it has 4,000,000,000 bytes available on it. 

Computer OS's don't use the same definition of KB, MB, and GB. They use the binary definition for KB, MB, and GB, as 1 KB = 1024 bytes, 1 MB = 1024 KB, and 1 GB = 1024 MB. 

Linux/Ubuntu tries to prevent confusion, by using KiB, MiB, and GiB notation for the binary definitions.

Therefore, a GiB = GB*(1000/1024). A GiB will always seem smaller than a GB.

---

### Post by 73ckn797 on 2009-01-16
> **Old_Gray_Wolf said:**
> A GiB is not equal to a GB.

Storage devices like HDDs, DVDs, flash drives, and so forth use the definition of KB, MB, and GB, as 1 KB = 1000 bytes, 1 MB = 1000 KB, and 1 GB = 1000 MB. 

Therefore, when a device reports that it has 4 GB, it has 4,000,000,000 bytes available on it. 

Computer OS's don't use the same definition of KB, MB, and GB. They use the binary definition for KB, MB, and GB, as 1 KB = 1024 bytes, 1 MB = 1024 KB, and 1 GB = 1024 MB. 

Linux/Ubuntu tries to prevent confusion, by using KiB, MiB, and GiB notation for the binary definitions.

Therefore, a GiB = GB*(1000/1024). A GiB will always seem smaller than a GB.


This is true. I have seen that info before.

---

### Post by yghannam7388 on 2009-03-16
Hello everyone, I have been wondering about the same thing. What I found once I used "top" was that some ram is stored as a "buffer". I don't know why but it adds up that way. For example, in top there are four values for RAM: total, used, free, and buffers. 

Used + free = total

That leaves the buffers. I hope this makes sense. If anyone knows what the buffers are for and how we can free it up please let us know. It's not really a big deal though because it's only like 200mb.;)

---

