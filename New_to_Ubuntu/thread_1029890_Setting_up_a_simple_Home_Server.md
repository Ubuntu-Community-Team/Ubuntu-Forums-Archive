---
title: "Setting up a simple Home Server"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Long_Live_Linux on 2009-01-03
I was wondering how I can set up a simple home server using Ubuntu or Ubuntu Server Edition. 

All I really want it to be able to do is automatically back up certain files on my XP machine and Vista machine to it's hard drive. I kind of know how to do this in Windows XP by "mapping network drive", but I'm a noob at linux and am lost. 

Any help is much appreciated! Thanks!

---

### Post by cariboo on 2009-01-03
As with all things Linux there are 3 different ways to do what you need. If you don't nned the windows computers  to mount any shares, rsync and ssh. Rsync is installed by default, and for ssh you need to install openssh-server on the server. Have a look at this [rsync howto]("http:///ubuntuforums.org/showthread.php?t=639979").

The second and most common way is to install Samba on your server, and mount the shares on your Windows computers. For a Samba howto look [here]("http://ubuntuforums.org/showthread.php?t=202605").

The third way is to use NFS, for an NFS howto have a look [here]("http://ubuntuforums.org/showthread.php?t=249889")
.

Jim

---

