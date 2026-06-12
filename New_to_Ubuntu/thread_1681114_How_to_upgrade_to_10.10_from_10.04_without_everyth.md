---
title: "How to upgrade to 10.10 from 10.04 without everything exploding?"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by ClaudeFleming on 2011-02-03
I know this question has been asked many times. But I recently tried to upgrade from 10.04 to 10.10 and of course it stopped in the middle of doing it's thing. So everything seemed fine until I rebooted and chose Ubuntu as my OS (I installed it using wubi), but some strange message popped up for a split-second and I was directed to the lovely grub terminal. I tried typing in some root commands on every listed device sda1, 2, 3, etc, and every time I did this it said that no kernel could be found. 

Does this mean that some upgrade script automatically deleted all of my linux kernels without checking to see if I had successfully upgraded to 10.10? If so, then it must have activated after I restarted my computer. I clearly don't know what I'm doing, but that hasn't stopped me so far!

Thanks,

Claude

---

### Post by sydbat on 2011-02-03
> **ClaudeFleming said:**
> (I installed it using wubi)This is your problem. Wubi is great for ***testing*** Ubuntu, not for use as a full time OS.

I have not had a problem upgrading from one version to the next with a normal install (Ubuntu in its own partition).

---

### Post by ClaudeFleming on 2011-02-03
Thanks, sydbat. I was beginning to think that Ubuntu was worse than Windows!

---

### Post by sydbat on 2011-02-03
> **ClaudeFleming said:**
> Thanks, sydbat. I was beginning to think that Ubuntu was worse than Windows!lol

The good thing about wubi is, as I stated, that you can install it like a program in Windows and test how well you like it, if it works for you, etc.

The bad thing about wubi is that it is subject to the Windows file system (because it is a virtual OS) and when NTFS fragments, it can (and always does in my experience) corrupt the Ubuntu image file. Defragging NTFS just destroys the wubi install.

I suggest that, after testing Ubuntu via wubi AND if you want to permanently install Ubuntu, search the forum for the "how to's" on creating partitions, dual booting etc.

---

### Post by bcbc on 2011-02-03
If you want to recover what you've got, see the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

If you haven't done much with Wubi and don't have data/settings you care about, reinstalling is easiest. But the upgrade fix is actually fairly simple.

---

