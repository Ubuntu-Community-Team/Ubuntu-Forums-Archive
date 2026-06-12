---
title: "Cannot log in after restoring &quot;home&quot;"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by flutti-tutti on 2009-01-26
After the "home" directory was restored from a backup file, I cannot log in.  It does not recognize the "home", due to a permission problem with "home/.dmrc".   From Terminal, i used chmod 644 home, but it did not work. 
My system is Ubuntu 8.10.   Please help!!!!

---

### Post by utnubuuser on 2009-01-26
It didn't work... as in it denied permission, or it did nothing to change the situation?

does it help to sudo chown first, so you're the actual owner, then chmod-ing?

---

### Post by flutti-tutti on 2009-01-26
Thanks for your response.

I used "sudo su", and then chmod 644 home as root.
It did not work.  I still have "Your home directory is listed as: '/home/User' but it does not appear to exist."

In Terminal, I have checked that '/home/User' exists with "ls".

---

### Post by snova on 2009-01-27
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

