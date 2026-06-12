---
title: "Boot (Grub?) problem..."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by AndrewS on 2010-04-30
Hi

I have several OS installed on the same hard drive on my PC - XP, Ubuntu 10.04 (as Wubi), Ubuntu 9.04, 8.10, 7.10 (all in their own partitions).  Since installing 9.10/10.04 with Wubi, all I get at startup is a choice between XP and 10.04; if I hit Esc I get to a Grub menu, but none of the installations seem to be available.  If I run grub-install -v in a terminal, I get:

[INDENT]error: cannot open `/dev/sdb' while attempting to get disk size.
grub-install (GNU GRUB 0.97)[/INDENT]

I think this means I am running Grub 1?  This would make sense as I never installed 9.10 from scratch, always by upgrade.

How do I get back to a conventional Grub-style startup, so I can choose the OS I want?

Note: On thinking about this some more, I think the "standalone" OSs disappeared when I installed 9.04 under Wubi.

TIA

Andrew

---

### Post by zvacet on 2010-04-30
>  This would make sense as I never installed 9.10 from scratch, always by upgrade.

When you upgrade to Karmic you probably upgraded grub to grub2.To revert to legacy grub read [this.]("https://help.ubuntu.com/community/Grub2#Reverting to GRUB Legacy")

---

### Post by AndrewS on 2010-04-30
Zvacet

That link refers to Grub legacy as 0.97, which is what grub-install -v returns, so do I need to do this?

Andrew

---

