---
title: "amarok installation problem"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by chieltje92 on 2010-05-25
hello everybody,

a couple of days ago I tried to install amarok musicplayer, but during the installation, my laptop shut down. when I tried to resume/restart the installation, I got an error that the installation failed due to an incorrect abortion of the installation. I had to recover this error, so I thought I had to delete all amarok files. I searched my laptop for any amarok files so I could delete them and restart the installation, but when I found some files, I couldn't delete them. my question is: how do I have to undo this aborted installation. oh, and I cannot install any other apps, I always get the same error

---

### Post by isaacj87 on 2010-05-25
> **chieltje92 said:**
> hello everybody,

a couple of days ago I tried to install amarok musicplayer, but during the installation, my laptop shut down. when I tried to resume/restart the installation, I got an error that the installation failed due to an incorrect abortion of the installation. I had to recover this error, so I thought I had to delete all amarok files. I searched my laptop for any amarok files so I could delete them and restart the installation, but when I found some files, I couldn't delete them. my question is: how do I have to undo this aborted installation. oh, and I cannot install any other apps, I always get the same error

Hey there,

Try running this to see if it fixes the problem:

```
sudo dpkg --configure -a
```

---

### Post by chieltje92 on 2010-05-25
thanks a lot, it worked

---

