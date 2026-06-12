---
title: "sshfs in fstab"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-30
from the command line
sshfs user@1.2.3.4:/home/otheruser -p port# /home/you/folder

how would you add this the fstab?

---

### Post by nmaster on 2010-06-30
> **lance bermudez said:**
> from the command line
sshfs user@1.2.3.4:/home/otheruser -p port# /home/you/folder

how would you add this the fstab?

don't add it to the fstab, instead use an init script:
[https://help.ubuntu.com/community/UbuntuBootupHowto#Installing%20custom%20init-scripts]("https://help.ubuntu.com/community/UbuntuBootupHowto")

make a script, remoteFS.sh (call it whatever you want).
```
 
#!/bin/bash
sshfs user@1.2.3.4:/home/otheruser -p port# /home/you/folder

```
then follow the other steps on the link.

one problem you may run into is if ssh asks you for a password.  to use ssh (or sshfs) without a password take a look at this:
[http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/](http://tombuntu.com/index.php/2008/02/20/public-key-authentication-for-ssh-made-easy/)

---

