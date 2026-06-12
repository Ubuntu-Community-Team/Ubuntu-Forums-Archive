---
title: "How to clean up after Archive Manager crash"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by marktebbutt on 2011-07-16
Hi all, I have seen a closed thread on this subject, but unfortunately there was no solution included in the thread.

(Out of interest I am running Xubuntu, but I don't know if this is a specific Xubuntu problem.)

I mistakenly tried to open a rar file with VLC, rather than extracting it first, and then VLC/archive manger between them managed to crash (I can't remember if I tried to stop the process while it said it was extracting the file?). I have now lost around 1GB of disk space
I see there is a file /proc/kcore that is taking up around 1GB. Could this be related, and if so can I just delete this file or is there a "neater" way of tidying this up?

Or if it is not the kcore problem, does anyone know where my 1GB might have gone? (It definitely disappeared at the time VLC and archive manager crashed.)

Thanks!

---

### Post by marktebbutt on 2011-07-17
Ok, sorted.

For completeness, I used the following:

sudo find / -type f -size  +500M -ls

Which led me to a file in my cache (it was the file  Itried to open with VLC).

Disk space back now, so all good.

---

