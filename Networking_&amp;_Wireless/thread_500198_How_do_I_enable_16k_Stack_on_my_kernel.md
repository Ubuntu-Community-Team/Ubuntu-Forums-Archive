---
title: "How do I enable 16k Stack on my kernel?"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by kchandler on 2007-07-13
Hey guys,

I am trying to use ndiswrapper to enable my wireless card:
Intel(R) Wireless WiFi Link 4965AGN 

I've got ndiswrapper installed and working, however, it only works for about 2 minutes at a time before the connection seems to just hang and stop responding until I reboot my computer.

After reading through numerous posts and articles I believe its due to my kernel using a 4k stack size.

The question I have is, can anybody help me or point me towards a guide that will help me change my kernel so that it has a 16k stack size. I am using Feisty.

Thanks. :)

---

### Post by geraldm on 2007-07-13
The config option  CONFIG_4KSTACKS is removed from the linux kernel 
as of version 2.6.21.1, so you need to get a kernel version 2.6.21 or OLDER.
Other than that, it should be just a normal kernel install, no other special
considerations.
I do not have any information on why that option was removed, or how to 
manipulate the stack to use 16k chunks.  The kernel mailing list archives
or commentaries may provide an explanation.
Gerald

---

### Post by kchandler on 2007-07-15
Well then does this mean anybody who uses ndiswrapper in future version of the kernel will not be able to use drivers that require more than a 4k stack size? 

Does anybody knwo if there is any way to get around this problem using the latest kernel?

Thanks.

---

