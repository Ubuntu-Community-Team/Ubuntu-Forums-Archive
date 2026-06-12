---
title: "NFS Files in mounted directory are missing"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by wilbur.harvey on 2005-11-16
I have two different Breezy boxes mounting a share from an FC4 machine. Both mount the FC4 share fine and I can read/write files. The problem is that about 30% of the files are missing. If I mount the other way, mount the breezy directory on the FC4 machine, everything works fine. If I mount the FC4 directory on another FC4 machine everything is fine.
Very strange
Any ideas?

---

### Post by MrNamjama on 2005-11-16
that sounds vaguely like fc4 is configured to use larger maximum transmission units than breezy.

I read a howto on setting up nfs servers and clients just the other day, that's the sort of symptom they described for when you set the MTU to a value that's too large...

I could be completely off

---

