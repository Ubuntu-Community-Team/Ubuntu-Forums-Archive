---
title: "Unistalling from command line"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by OllieGab on 2010-01-17
I installed RealPlayer (from a .bin file) following some instructions from a forum.
I now need to unistall it...how do I do it?
I use Ubunty 9.10.

Any pointers appreciated!

Cheers

---

### Post by zeroseven0183 on 2010-01-17
Here's what it's said in the [RealPlayerInstallationMethods Ubuntu Help page]("https://help.ubuntu.com/community/RealPlayerInstallationMethods?action=show&redirect=RealplayerInstallationMethods") 

```
sudo /opt/real/RealPlayer/postinst/postuninst.sh
```

> 
- Once this script has been run it is safe to remove the /opt/real folder and subfolders.
- If the package was installed in another folder, run the postuninst.sh script from that folder. 

---

### Post by OllieGab on 2010-01-17
That worked fine.
It had (or perhaps I did!) been installed from/on the desktop but anyways, it's gone!
Thanks a lot!

---

### Post by arnab_das on 2010-01-17
could u kindly mark this thread as solved for the benefit of users. its in the thread tools.

---

