---
title: "Uninstall HPLIP From Xubuntu LTS"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by fleamour on 2011-02-20
I am having real trouble translating these instructions:

[http://hplipopensource.com/node/188](http://hplipopensource.com/node/188)

Can someone help me out?  I do not know which is the source directory, it's certainly not "Desktop".  Also I did not download source tarball but a file called "hplip-3.11.1.run".  Please excuse my ignorance, but have been going in circles & getting frustrated.

:(:confused::(

---

### Post by sanderd17 on 2011-02-20
what instructions did you follow to install it?

---

### Post by fleamour on 2011-02-20
Download file hplip-3.11.1.run to desktop then:
```
cd Desktop
sh hplip-3.11.1.run
```
From CLI & the script did the rest, asking a few y/n questions along the way.

[http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

---

### Post by sanderd17 on 2011-02-20
when you ran it, it should have created a directory "hplib-3.11.1" in the folder where you were working, enter this directory in the terminal instead of the directory in step A.

If you deleted that direcotry (or can't find it), install hplib again (completely install, not just the first step) and the folder will be generated again.

when you got the directory, just proceed with the steps B, C and D.

---

### Post by fleamour on 2011-02-20
Ahhhh, (dawns) that was what that folder was on the desktop.  OK will reinstall tomorrow.  LXDE has no trash bin at the mo' otherwise restoring said file would come in handy.

Thanks!

---

