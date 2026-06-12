---
title: "Problems with Memory"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by dmaxel on 2010-12-24
Hi everyone,

I got some memory for a Christmas present, and I immediately put it in. It's 4GB (2 x 2GB) of RAM. I know that all of it works because my BIOS detects 4096MB. However, when I'm in Ubuntu it says I only have 3.2GB. So I went into memtest, and it says 3320 ish, so about 3.2GB. Thinking I've gone crazy, I went into Windows, and it says I have 4GB install, but only 3.25 GB is usable.

Could anyone please help me with this??? I would really like to use all 4GB of my RAM. Also, Ubuntu and Windows are both 64-bit, so running a 32-bit OS is definitely not the problem.

Thanks!

---

### Post by sandyd on 2010-12-24
> **dmaxel said:**
> Hi everyone,

I got some memory for a Christmas present, and I immediately put it in. It's 4GB (2 x 2GB) of RAM. I know that all of it works because my BIOS detects 4096MB. However, when I'm in Ubuntu it says I only have 3.2GB. So I went into memtest, and it says 3320 ish, so about 3.2GB. Thinking I've gone crazy, I went into Windows, and it says I have 4GB install, but only 3.25 GB is usable.

Could anyone please help me with this??? I would really like to use all 4GB of my RAM. Also, Ubuntu and Windows are both 64-bit, so running a 32-bit OS is definitely not the problem.

Thanks!
post output of
```

uname -a
```

and check the motherboard. The BIOS sometimes reports *what is in the computer* but not  whats usable. This was one of the issues in the Gigabyte (was it?) motherboards where it was advertised as 10 GB, but only 8 GB would ever work.

---

### Post by ebasa on 2010-12-24
I believe you need to install the PAE kernel to fix that problem. It is in Synaptic.

---

### Post by zeroseven0183 on 2010-12-24
Hope this thread helps [http://ubuntuforums.org/showthread.php?t=977915](http://ubuntuforums.org/showthread.php?t=977915)

---

### Post by dmaxel on 2010-12-24
> **sandyd said:**
> post output of
```

uname -a
```and check the motherboard. The BIOS sometimes reports *what is in the computer* but not  whats usable. This was one of the issues in the Gigabyte (was it?) motherboards where it was advertised as 10 GB, but only 8 GB would ever work.
uname -a says: ```
Linux lucid-test 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
```
lucid-test is the hostname. Also, the BIOS says "4096MB OK" so I would presume that it is fully functioning. Plus I know from what is advertised that it supports up to only 4GB.> **ebasa said:**
> I believe you need to install the PAE kernel to fix that problem. It is in Synaptic.
Considering I run (as I said) 64-bit, that shouldn't be necessary. Only for 32-bit.
> **zeroseven0183 said:**
> Hope this thread helps [http://ubuntuforums.org/showthread.php?t=977915](http://ubuntuforums.org/showthread.php?t=977915)
This thread recommends I install 64-bit, which I already said that I have. No help.

---

### Post by 73ckn797 on 2010-12-24
> **ebasa said:**
> I believe you need to install the PAE kernel to fix that problem. It is in Synaptic.
This will work if you have a 32 bit Ubuntu. I have 6GiB and with PAE kernel it shows 5.9GiB.

---

### Post by Rabhak on 2010-12-24
It's just normal. . it doesn't mean that if you put 4 GB of memory it will appear exactly as 4 GB, 

Your lucky you got a high memory dude. . . I only got 1 GB running in my ubuntu. .and it works really good

---

### Post by dmaxel on 2010-12-24
I just find it strange that a whole .75GB is simply not being used. It's not like any memory is going to a graphics card, because I have one that has its own memory.

---

### Post by sandyd on 2010-12-24
sigh....
Does your BIOS have a function called "memory remapping"?

If not, your going to be stuck with the amount of RAM that you have right now.

Its due to a architectual change that created something called "memory mapped IO reservations". The memory from about ~3.2 GB (that is what it is on your system, other systems may have from ~2.5) onwards are mapped so that only the hardware (i.e. cdrom drives, PCI, PCI express (at least 256mb for this)) can use the memory. Its OS independent.

For more info, check this out -> [http://support.microsoft.com/kb/929605/en-us](http://support.microsoft.com/kb/929605/en-us)

---

### Post by dmaxel on 2010-12-24
> **sandyd said:**
> sigh....
Does your BIOS have a function called "memory remapping"?

If not, your going to be stuck with the amount of RAM that you have right now.

Its due to a architectual change that created something called "memory mapped IO reservations". The memory from about ~3.2 GB (that is what it is on your system, other systems may have from ~2.5) onwards are mapped so that the hardware (i.e. cdrom drives, PCI, PCI express (at least 256mb for this)) can use the memory. Its OS independent
Ah, I see. No, my BIOS does not have that function. In fact, the only place it ever mentions the RAM is when it counts it and says "4096MB OK"...there's nothing about RAM in the BIOS settings at all (aside from changing the voltage). I can go look if I can update the BIOS, but knowing ECS that probably won't help much.

Thanks a bunch for your help. At least I understand what's going on now.

---

