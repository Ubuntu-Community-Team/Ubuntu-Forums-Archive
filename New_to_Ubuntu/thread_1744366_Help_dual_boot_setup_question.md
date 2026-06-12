---
title: "Help dual boot setup question"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by riggs51 on 2011-04-30
Hi all,  I am an absolute beginner with linux,  I am wanting to dual boot my win 7 notebook

I done some reading and in v 10 it appears there is a guided setup however the new v 11 just takes me to a partition manager which is fine except i am now stuck.

I have worked out how to select the windows partition I need to resize,  the next question is what to set it as do I choose EXT4 ? and it then asks for a directory to mount it to do I mount this to /boot ??

I would appreciate the assitance to get past this little problem so I can start to explore.

Thanks

---

### Post by drklunk on 2011-04-30
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html")

That should answer your questions. Basically you need at minimal three partitions: Win7, /, and swap. I chose not to have a separate home partition but it is a good idea to have one. The tutorial will explain all that though ;)

---

### Post by riggs51 on 2011-04-30
Thanks I think that just sorted me out.

---

### Post by drklunk on 2011-04-30
No problem man, good luck

---

