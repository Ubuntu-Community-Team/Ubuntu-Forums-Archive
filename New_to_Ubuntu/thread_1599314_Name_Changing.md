---
title: "Name Changing"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by jreiley on 2010-10-17
When my development server was built, it was name JimsBox.  That won't fly.  All our software I support is looking for a different server name.  Can I change the existing name to the correct name and how?
Thanks.
Jim

---

### Post by Verbeck on 2010-10-17
sudo gedit /etc/hostname
sudo gedit /etc/hosts

change the computer name in both files to the new one and restart. Remember to open them both before saving one of them after making a change, _or you might break your system_.

further reading:
[http://ubuntuforums.org/showthread.php?t=1089673](http://ubuntuforums.org/showthread.php?t=1089673)
[http://ubuntuforums.org/showthread.php?t=224722](http://ubuntuforums.org/showthread.php?t=224722)

---

### Post by jreiley on 2010-10-18
I don't have gedit on my server.  There are no graphics on it at all.  What other editor can I use?    Thanks.

---

### Post by diablo75 on 2010-10-18
Try nano

---

