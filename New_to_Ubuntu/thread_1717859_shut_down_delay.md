---
title: "shut down delay"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by aam-aadmi on 2011-03-30
Hi All,

I am running Ubuntu 10.04 on a HP Pavillion dv2500 laptop. Over the last few days I have noticed that it takes a long time (5-10 minutes, say) for the machine to shut down. Are there are suggestions as to what I might do to correct this problem?

Thanks.
Aam-aadmi

---

### Post by ajgreeny on 2011-03-30
To find out what is causing the delay you could try booting next time without t5he normal graphic boot.  At the grub menu, which you can see if it is not normally shown by holding shift at power-on, hit "E" on the normal boot line, scroll down using cursor keys to the kernel line with "quiet splash" in it and delete just those two words.  Ctrl+X to boot and you will see a full text boot scroll instead of the usual plymouth display.

This will also happen at shutdown and you may get some idea where the hold up is happening, so come back again if so, and ask what to do next.

---

### Post by aam-aadmi on 2011-03-31
Okay, thanks. I will try that and get back with more questions.

Aam-aadmi

---

### Post by Ocxic on 2011-03-31
I used to have this problem with portmap after installing nfs-kernel-server portmap would take forever to stop/shutdown. I narrowed the delay to portmap but never found out why it was doing that as the problem when away after an upgrade to a new Ubuntu release.. might not help, but might give you a direction to go in.

---

