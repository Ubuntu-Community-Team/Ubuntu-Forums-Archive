---
title: "Firefox crashes Ubuntu partition (but fine in Windows)"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by kogray on 2010-11-15
I once had a beautifully running Hardy Heron installation on my Toshiba L505-S5990.

A few months ago  however - out of the blue - opening Firefox (or any other internet program) lead to a worrying clicking sound coming from under the keyboard and my machine would just freeze, windows would go grey, & refuse to close, etc. Etc. 

RIP.

... but then I went into my Windows partition however and it would work just fine. In fact, nothing was wrong in the Windows partition (other than the fact that it was a Windows partition).

I miss my Ubuntu partition and in fact, want to upgrade to 10.10 but I figure I should solve this issue first.

I have no idea what to do though. I have heard that there is something similar to Windows Scandisk called FSCK but I cannot run it while I am in Ubuntu. And I don't even know if that will solve it.

I thought about it because Gparted says I do have some bad sectors.

The other weird thing is that although I can't go online, my Gmail notifier receives updates, Skype seems to be on and working (although I've not tried actually making a call, it receives messages) and Liferea keeps stacking up unread posts.

Can anybody help me?

---

### Post by cariboo on 2010-11-15
Boot from a Live CD to run fsck. Once at the desktop, open a terminal and type:

```
sudo fsck -y /dev/sdaX
```

where /dev/sdaX is your Ubuntu partition.

---

### Post by kogray on 2010-11-21
Hi Cariboo,

Many thanks for the tip. I ran the command and this is what came up:

sudo fsck -y /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
UBUNTU: clean, 399462/8208384 files, 25918543/32804722 blocks

The problem is still there though. The funny thing is that while using the Live CD I could browse with no problem.

What do I do now?

---

### Post by kogray on 2010-11-29
Bump :)

---

