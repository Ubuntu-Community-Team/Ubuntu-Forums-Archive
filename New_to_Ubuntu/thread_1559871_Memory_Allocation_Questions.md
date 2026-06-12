---
title: "Memory Allocation Questions"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Steveplanetary on 2010-08-24
[SIZE=2]When I executed the *free* command in a terminal window the information provided raised several questions.

1) The reported total RAM=896,036 is correct, but as a former MS Windows user I find it strange that 864,152 is being used, leaving only 31,884 free.  I find it especially strange because of the 1,952,760 byte total swap only 72,040 is used, leaving 1,880,720 bytes free.  I think linux is superior to Windows, but if this one of the reasons I would appreciate it if somebody would explain it to me.  I always thought it was a good idea to have some scratch pad space in memory.

[/SIZE][SIZE=2]2) On the same line as the physical memory data are entries for buffers and cache.  The former had a value of 52,588, while the latter had a value of 174,112.  The only cache I know about is the on die L1 and L2.  My CPU has 512 KB L2 and 128 KB L1 that is split into 64 KB for data and 64 KB for instructions.  So where are the 174,112 bytes and the 52,588 bytes?  If they are in the L2 and L1 caches, respectively, I would say that both are being underutilized.  Would somebody kindly explain this to me, and tell me how linux memory management differs from that of Windows?

3) Simple question: What does -/+ buffers/cache mean?

Thanks in advance.
[/SIZE]

---

### Post by yeats on 2010-08-24
This might help:

[http://www.linuxjournal.com/magazine/hack-and-linux-troubleshooting-part-i-high-load?page=0,2](http://www.linuxjournal.com/magazine/hack-and-linux-troubleshooting-part-i-high-load?page=0,2)

it's a good article overall about troubleshooting high system load and the section I'm pointing you to will let you know how memory works.

---

