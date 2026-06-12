---
title: "Ubuntu can't see Vista Shares"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by whistlerspa on 2008-07-04
I've tried everything that I can find recommended in these forums but still can't get better than 0 files in my Vista shares when viewing on Hardy.

My Vista box can see my Ubuntu and XP shares as can my XP laptop. Samba is correctly installed and all passwords configured correctly. Can anyone suggest what else may need to be done?

---

### Post by kornhead127 on 2008-07-04
I have this same problem, try this.

```
$ sudo apt-get install pyneighborhood
```

It'll show up in your Application -> Internet menu.

---

### Post by Alnz on 2008-07-04
I have Same problem, can access shares if i type address but nothing will show up in the gui.

I have windows network, workgroup, and my windows pc is then listed, but no shares under that.
All shared files on my ubuntu laptop are accessable from windows comp.

PS using Wireless will this make a differance?

---

### Post by whistlerspa on 2008-07-04
Tried PYNeighbourhood but same result - thanks for showing me that though it looks interesting.

Also tried the Dreamlinux 3 LiveCD and can read Vista shares with that but not open shared files properly. Am using a wireless connection to this box  - should that make any difference?

---

