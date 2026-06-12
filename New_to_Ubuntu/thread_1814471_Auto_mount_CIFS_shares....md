---
title: "Auto mount CIFS shares..."
date: 2011-07-29
forum: New to Ubuntu
---

### Post by desperado665 on 2011-07-29
I have been able to locally mount my media folder from a Windows Home Server using CIFS and mount -t cifs //192.168.X.X/Music /home/Music -o user=XXX,password=YYY but each reboot I need to re enter for each streaming media folder I have. Is there a way to have them all mounted each time I boot?

Thanks

---

### Post by Paqman on 2011-07-29
[Yep!](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

It's actually a lot less involved than that page makes it seem, it's just covering a lot of different use cases. In brief all you need to do is:
[list]
[*]Set up some security
[*]Create some mount points (if you haven't already)
[*]Edit fstab
[/list]

---

### Post by desperado665 on 2011-07-29
Thanks Paqman.

---

