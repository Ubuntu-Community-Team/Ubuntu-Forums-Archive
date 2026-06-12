---
title: "[SOLVED] Does ubuntu server 32bit use more then 2gb ram?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by niiklas on 2008-12-23
thread name says it all

---

### Post by taurus on 2008-12-23
Yes.

---

### Post by niiklas on 2008-12-23
> **taurus said:**
> Yes.

okey, is there any downsides on ubuntu 64bit as there is with windows less drivers program compability?

---

### Post by ken22 on 2008-12-23
It depends.

I run Ubuntu server 32bit and it only uses 200mb running apache and mysql. That said I only use it locally.

It can use up to 4Gb as far as I know if needed.

---

### Post by niiklas on 2008-12-23
> **ken22 said:**
> It depends.

I run Ubuntu server 32bit and it only uses 200mb running apache and mysql. That said I only use it locally.

i meant if it could take advantage of more ram, in windows 32bit there is 3,2gb max :S

---

### Post by balaknair on 2008-12-23
> **niiklas said:**
> i meant if it could take advantage of more ram, in windows 32bit there is 3,2gb max :S

Yes, AFAIK it(Ubuntu Server 32-bit) can use up to 3 GB RAM.

That limitation(unable to utilize more than 4 GB RAM) is shared by all 32-bit OSes, since a 32-bit processor uses 32 bits to refer to the location of each byte of memory. 

2^32 = 4200000000, which means a memory address that's 32 bits long can only refer to 4.2 billion unique locations (i.e. 4 GB).

The reason only 3 GB of this ends being utilized in RAM is because the x86 hardware typically reserves some of the possible 4 GB address space for other devices such as the BIOS ROMS and the GPU. This, AFAIK, is independent of OS, being a hardware thing.

For 64-bit OSes, the limit becomes 2^64 = 17640000000000000000 (16 exabytes or 16.8 million terabytes). 

Most current CPUs however have artificial caps that limit the address space to 40-48 bits.

---

### Post by Steveway on 2008-12-23
While those calculations may be correct, the answer isn't correct.
The server-edition of Ubuntu can use more than 4GB of RAM due to PAE.
Google it for more information.
> **balaknair said:**
> Yes, AFAIK it(Ubuntu Server 32-bit) can use up to 3 GB RAM.

That limitation(unable to utilize more than 4 GB RAM) is shared by all 32-bit OSes, since a 32-bit processor uses 32 bits to refer to the location of each byte of memory. 

2^32 = 4200000000, which means a memory address that's 32 bits long can only refer to 4.2 billion unique locations (i.e. 4 GB).

The reason only 3 GB of this ends being utilized in RAM is because the x86 hardware typically reserves some of the possible 4 GB address space for other devices such as the BIOS ROMS and the GPU. This AFAIK is independent of OS, being a hardware thing.

For 64-bit OSes, the limit becomes 2^64 = 17640000000000000000 (16 exabytes or 16.8 million terabytes). 

Most current CPUs however have artificial caps that limit the address space to 40-48 bits.

---

### Post by Titan8990 on 2008-12-23
You can only use PAE if your motherboard supports it.

---

### Post by Elfy on 2008-12-23
[http://ubuntuforums.org/showpost.php?p=5359004&postcount=1](http://ubuntuforums.org/showpost.php?p=5359004&postcount=1)

might be worth reading

---

### Post by Bölvaður on 2008-12-23
linux can be tweaked to use more than 3.2 GiB of RAM, of the cost of lower response time I think. look it up.

But there are no reason for a server not to use 64 bit version, as the driver problems are from manufacturers (mainly graphical and wireless cards).. which are not big problems for servers.

---

