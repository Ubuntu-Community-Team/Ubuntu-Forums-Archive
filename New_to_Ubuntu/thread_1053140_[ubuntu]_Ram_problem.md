---
title: "[ubuntu] Ram problem?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by unitedwefall on 2009-01-28
Hi

Im a total beginner; i took a look through the first few pages and couldnt see this problem being discussed. Ive got the 32-bit build and i read thats suppost to support up to 4gb of ram; in my system moniter though its only picking up 3Gb (i have four) any ideas? 

thanks xx

---

### Post by overdrank on 2009-01-28
Moved to Absolute Beginner Talk :)

---

### Post by MockY on 2009-01-29
> **unitedwefall said:**
> Hi

Im a total beginner; i took a look through the first few pages and couldnt see this problem being discussed. Ive got the 32-bit build and i read thats suppost to support up to 4gb of ram; in my system moniter though its only picking up 3Gb (i have four) any ideas? 

thanks xx

This normal for a 32-bit OS unless you use specific flags to bypass this limitation. Or you could go with a 64-bit version.

---

### Post by kavon89 on 2009-01-29
Does it say 3.9GiB? Data is advertised by manufacturers as being "4GB", which means 4,000MB. In reality four gigabytes = 40**96**MB. This causes problems as sizes increase to where you're loosing gigabytes of storage.

If it doesn't say 3.9GiB in the System Monitor, run this command in the Terminal, then copy the section on memory (to copy from the terminal, highlight, then you must right-click the highlighted text and hit Copy).

```
sudo lshw -class memory -sanitize
```

---

### Post by jerome1232 on 2009-01-29
That's actually about right, a 32 bit system can address up to 4 GB's but some of that address space is used for devices. Usually devices are given the upper limits of address space so as not to impose on ram but you've got to much for that. To compound on that integrated graphics (if you have one) borrow from system ram further reducing the amount of available ram.

---

### Post by mcduck on 2009-01-29
> **kavon89 said:**
> Does it say 3.9GiB? Data is advertised by manufacturers as being "4GB", which means 4,000MB. In reality four gigabytes = 40**96**MB. This causes problems as sizes increase to where you're loosing gigabytes of storage.

If it doesn't say 3.9GiB in the System Monitor, run this command in the Terminal, then copy the section on memory (to copy from the terminal, highlight, then you must right-click the highlighted text and hit Copy).

```
sudo lshw -class memory -sanitize
```

Actually RAM is always counted as powers of two (because that's how it's used.) 1GB of RAM is *always* 1024MB. I'd say hard disk space is the only place where powers of ten are used.. (stupid way started by hard disk manufacturers. :/)

But Jerome1232 is right, you'll usually get something between 3.2GB ad 3.5GB of usable RAM on a 32-bit system (without using PAE). This is because the CPU is only able to handle 32 bits of memory addresses (4GB) but part of that address space is needed for other things than your RAM.

---

