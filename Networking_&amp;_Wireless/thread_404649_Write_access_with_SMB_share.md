---
title: "Write access with SMB share"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by TidySi on 2007-04-08
Pulling my hair out again, probably not much left!

For some reason my SMB share to my Windows Media Centre has stopped allowing me write access and I cannot figure out why?

I successfully mount my share as follows:
//192.168.1.101/data /media/mce smbfs username=xxx,password=xxx 0 0

However I can no longer write to the Windows share. Tried many different things but got no where. I did ask this question before and resolved the issue but know its stopped working.

---

### Post by Roland of Gilead on 2007-04-08
I assume this mount is defined in your fstab file.

For grins, unmount the share, then mount it again manually from the command line.  If it's forcing a read-only mount for some reason, it should spit an error message.

---

### Post by woo2the2 on 2008-05-18
This worked for me, but YMMV...try changing the permissions on your linux mount directory.

```
sudo chmod 777 /pathto/mountdir
```

Might want to chown to whatever linux user you log under, as well.

```
sudo chown username /pathto/mountdir
```

---

