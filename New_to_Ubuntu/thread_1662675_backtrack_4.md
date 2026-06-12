---
title: "backtrack 4"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by hell_fiend on 2011-01-08
i have a dual boot of Linux Backtrack 4 and Windows Vista.for a year i used Linux BackTrack4 and today i planned to remove it and install BackTrack4 R2, so i copied any data i needed from the Linux partitions to Windows, after that, i formatted the Linux Partitions directly from Windows. after this i restarted the system to see if there was any problem with it due to the formatting. and on the startup, the GRUB loader had some issues, it foes like this: ------------------------------------------------------------------------    GRUB Loading Stage1.5.    GRUB loading Please Wait....      Error 17 ________________________________________________________________________ and it stays there like that, so i cannot boot any OS. i know its caused by the formatting of the Linux partitions and i don't know how to fix the GRUB loader since I'm not familiar with Linux that well, any help with fixing this error? thnx

---

### Post by gamepoint on 2011-01-08
try booting using windows cd and enter command prompt
type ```
bootrec.exe /fixmbr
```

or 

```
bootrec /fixmbr 
```and try to restart..

this problem happens because grub which backtrack installed is missing after u formatted the partition

---

