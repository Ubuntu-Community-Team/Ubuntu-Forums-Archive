---
title: "Software Sources list issue"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by deancasino on 2009-12-13
Hey guys, I added the Akirad Repository to my software sources a week ago to try out some program, anyway, I hated it so I deleted the software source entry, but every time I reboot it comes back, how do I remove it permanently?

---

### Post by Physical Hook on 2009-12-13
```
gksudo gedit /etc/apt/sources.list

```

Remove it, save the file and reboot. Still there ?

---

### Post by govt_cheese on 2009-12-13
Where did you remove it? Sources.list, synaptic?

---

### Post by deancasino on 2009-12-13
Yes, Thought that may be the issue, but the entries weren't there, as soon as I posted I discovered the problem; the '.list" and '.list.save' files were still in /etc/apt/sources.list.d for some reason. I deleted the rouge files, and it was fixed.

Update: Turns out just deleting those two files didn't do the trick, I had to search the whole computer for "Akirad" and delete each individual file to remove the god forsaken software sources. What a pain!

---

