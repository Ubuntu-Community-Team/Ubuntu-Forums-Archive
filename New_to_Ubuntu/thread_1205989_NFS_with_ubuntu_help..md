---
title: "NFS with ubuntu help."
date: 2009-07-06
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-07-06
I have 8.04 desktop and 8.04 server on two different machines on the same cable box.

1 is a static ip address 1 is dynamic (server static desktop dynamic)

I get this error, while trying to mount the server file system to my desktop computer.

mount.nfs: access denied by server while mounting

I made the export file, and I restarted I believe, maybe its port issues? can anyone help me with this(?), much appreciated in advance.

All in the same building and connected to the same box.

---

### Post by Celauran on 2009-07-06
Can you post your exports file?

---

### Post by ericeclifford on 2009-07-07
well my exports on my server computer is

/ 192.168.1.45(rw,async)

---

### Post by Iowan on 2009-07-07
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is an NFS How-To, and [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is a help page.

---

