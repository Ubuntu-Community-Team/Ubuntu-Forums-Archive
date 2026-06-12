---
title: "Triple boot &amp; isolate both windows OS's"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by pleurastic on 2009-05-21
I need to triple boot XP, VISTA and Ubuntu with the stipulation that Ubuntu cannot mount any windows partition.  Is it doable?  I'm not in charge of the equipment and the IT guy is adamant Ubuntu may not access files in either XP or VISTA.  USB mounts are OK.  Virtual is not OK.

---

### Post by oOarthurOo on 2009-05-21
Yes. When installing choose manual setup of partitions, and don't create a mountpoint for the windows partitions. If you already have a working setup, just comment out the lines for the Windows mounts in /etc/fstab.

---

