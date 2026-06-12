---
title: "Something filling up the disk"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by P=NP on 2011-06-04
Before I compiled the kernel, there was about 6 gigs used. After about 13 gigs and I can't find where it went.

---

### Post by ohadcn on 2011-06-04
get in the folder /usr and give us another snapshot

---

### Post by P=NP on 2011-06-04
here ya go

---

### Post by Larkspur on 2011-06-04
Do you run nautilus as root a lot?

---

### Post by dFlyer on 2011-06-04
Did you reboot after you install the new kernel?

---

### Post by P=NP on 2011-06-04
Hardly ever. But I did have Nautilus open as root while I was compiling the kernel.

And yes, I rebooted after I installed the kernel.

---

### Post by Larkspur on 2011-06-04
> **P=NP said:**
> Hardly ever. But I did have Nautilus open as root while I was compiling the kernel.

And yes, I rebooted after I installed the kernel.

While using Nautilus, did you delete a lot (and it would be loads) of stuff?  If so, that would explain it: open nautilus as root again, and go to /root/.local/share/Trash and delete everything in it (use shift+del).

---

### Post by drs305 on 2011-06-04
Are you opening DUA as a normal user? If so, some of the system folders are hidden and you might try "gksu baobab".

One place to look is in /root/.local/share/Trash to see if you have accumulated a lot of root trash. Even if it's in root's Trash Bin, it is still occupying space until you empty it.

---

### Post by P=NP on 2011-06-04
> **Larkspur said:**
> While using Nautilus, did you delete a lot (and it would be loads) of stuff?  If so, that would explain it: open nautilus as root again, and go to /root/.local/share/Trash and delete everything in it (use shift+del).

That was it. Thanks guys.

---

