---
title: "Cannot find drive"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by Metalbot on 2011-08-28
I've installed ubuntu alongside Windows Xp. I installed Ubuntu in drive F: (as in Windows - which is not my system directory). When I start Ubuntu, I cannot see this drive. I can see all the other logical partitions. What do I do to settle this issue?

Thank you.

---

### Post by TeoBigusGeekus on 2011-08-28
If you've installed ubuntu in f:, then the f: drive has become your file system (/) and your home folder (/home).

---

### Post by Metalbot on 2011-08-28
I see. But i still don't see the same directories in "File System" that i have on Windows Xp. I have many other documents in that drive (in windows) that i cannot see in Ubuntu. What do i do?

Thank you.

---

### Post by Mark Phelps on 2011-08-28
The only way you can install Ubuntu to a Windows "drive" is to install via Wubi.  In that case, your Windows filesystem is mounted under "/host".

---

### Post by Metalbot on 2011-08-28
you're right. I found what i was looking for. Thank you. :)

---

### Post by Wim Sturkenboom on 2011-08-28
If it's solved, please mark your thread as soloved using the thread tools just above the first post on this page.

You should be able to find your windows drives in the places menu (like 120GB filesystem or the label of the partition) if you made a dual boot (which is basically how I interprete 'alongside').
If you used wubi, you installed installed 'inside' windows.

---

