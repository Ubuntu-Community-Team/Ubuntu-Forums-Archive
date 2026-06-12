---
title: "[SOLVED] stuff stuck in trash, cant remove even as root"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by earthpigg on 2008-12-14
i think it was left over from when i deleted something on a thumb drive i no longer have access to.

the only thing i've tried is 'sudo nautilus' and emptying the trash that way, but when im root it says 

> The folder contents could not be displayed.
Sorry, could not display all the contents of "trash": Operation not supported

8.10, fresh install a few months back.

---

### Post by drs305 on 2008-12-14
You can look at my tutorial for deleting root trash for possible solutions:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

Also, when you use graphical apps you should use 'gksudo' rather than 'sudo'. This would take you to root's trash bin:
```

gksudo nautilus /root/.local/share/Trash

```


Here's why: [graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

