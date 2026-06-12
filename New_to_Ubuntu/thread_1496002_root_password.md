---
title: "root password"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by redesigner on 2010-05-28
I need to access root, but I don't have a password.
I have tried to change it with sudo, but it keeps telling me "Sudo must be setuid root". When I searched how to fix sudo, all that I have found tells me to root to fix sudo, and I can't do that.
Version: 9.10 (Installed on 9.04)

---

### Post by bapoumba on 2010-05-28
[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)

Do you remember what you were doing before getting this error ?

Edit: please also see [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by sidzen on 2010-05-28
[PHP]sudo passwd root[/PHP]enter login password, then new UNIX password twice
[PHP]su -l[/PHP]enter password just created, and you're /

---

### Post by aysiu on 2010-05-28
> **redesigner said:**
> I need to access root Why do you need to access root?

If you want a persistent root prompt, you can use the command ```
sudo -i
``` If you want a graphical root file browser, you can use the command ```
gksudo nautilus
``` If *sudo* itself isn't working, refer to the fixsudo link posted above. You can fix it through either recovery mode (more details in the link) or by booting a live CD and then mounting your Ubuntu drive.

Please let us know if you get stumped at any step.

---

### Post by lisati on 2010-05-28
Please also read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

