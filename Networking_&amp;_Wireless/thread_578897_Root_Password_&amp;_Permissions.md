---
title: "Root Password &amp; Permissions?"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by smuggly on 2007-10-17
Im running Kubuntu Gutsy i believe i have a sys with 2 hd,s on it one with kubuntu & 1 With ntfs Music Files And 2 Partitions 1 sdb1& sdb5 I Can mount with sudo mount but cant access because of permissions in my user acct,I found a few threads with fstab edit inst.but i cant edit the file either? Please Help I hate Mr Gates And Cant Go Back:) Please Remember Im New To All This But Very Willing.

                                                                      Thank You
                                                                                             Tom:guitar:

---

### Post by Hero of Time on 2007-10-18
Go to the package manager and look for NTFS-3g and NTFS-Config. When done, open the NTFS-Config Tool and enable read/write for all users. That should do it. Mount still needs root privileges.

---

### Post by smuggly on 2007-10-20
Thanks That Did It.....................Tom:guitar:

---

### Post by Hero of Time on 2007-10-20
Glad it works now. Next time, put your topic in the right place. Asking why your filesystem won't mount isn't a part of networking and wireless.

---

