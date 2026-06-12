---
title: "Starting Hamachi Trouble"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by SoulMazer on 2009-04-04
So, I installed Hamachi correctly with no errors, however I get an error when I attempt to start Hamachi ("hamachi start"): "tap: connect() failed 2 (No such file or directory)".

Yes, I know that section 1.B of [this guide]("http://ubuntuforums.org/showthread.php?t=135036") addresses the same error, however it does not solve my problem. Whenever I try to run "sudo mkdir /dev/net" or "sudo mknod /dev/net/tun c 10 200", I am told that the files already exist.

Does anybody know what my problem is? Thanks in advance.

EDIT: After some tweaking I solved my own problem. Sorry for the wasteful post. Delete if necessary.

---

### Post by kloyde on 2009-04-05
i am having a similar problem (i think). what tweaking did you do?

---

