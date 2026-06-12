---
title: "Mounting smb shares on boot doesn't work"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Helmi on 2007-10-19
Hi,

i setup several smb shares with smbfs and cifs to mount via fstab. Everything works great so far when mounting with 'sudo mount -a' but they don't mount anymore on boot time. They did since a few days ago but now they don't. The mount well when mounting them manually right after boot with 'sudo mount -a' again.

Any hint where to look for the problem?

Thanks!

P.S: I'm using gutsy for a few months already.

---

### Post by Helmi on 2007-10-28
really no one has this problem, too or even a solution?

---

### Post by ericdegen on 2007-11-01
I've been having the same problem since loading gutsy... its off and on, some boots are fine, others just hang for about ten minutes and it never mounts the SMB mount points.

Frustrating as hell!

---

### Post by Helmi on 2007-11-02
it's kinda different here. there's just ONE smb mount out of 12 that get's mounted automatically - the others are NOT beeing mounted on EVERY boot, unfortunately.

---

### Post by bayvista on 2007-11-04
could u post your fstab entries please. I'm playing with this one too.

---

### Post by ericdegen on 2007-11-10
Sure... like I say sometimes it works, others it hangs...

//10.1.10.4/fs /tera smbfs dmask=777,username=XXXXXX,passwd=XXXXXXXX,lfs 0 0
//10.1.42.8/fs /p smbfs dmask=777,username=XXXXXX,passwd=XXXXXXXX,lfs 0 0

---

