---
title: "Can't share home folder in hardy HELP PLEASE"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by DexterLB on 2008-06-04
In gutsy I had shared my home folder in samba and it was seable by other windows computers, username & password worked fine (I set the pass with smbpasswd). But now on hardy I did the same thing and it says:

```
The folder "main" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically?
```
(my user is called 'main'

If I add the permissions a dialog starts to pop up at logon which warns me of the wrong permissions. That's OK, but when I try to access this home folder from a windows machine, **_it doesn't ask for an user name and password_**, and so it doesn't have permissions. How can I share my home folder under hardy?

---

### Post by linux6994 on 2008-06-04
I have sharing working just fine in hardy with XP and Vista machines. My Ubuntu is actually the file and print server. I have all of the samba files installed via synaptic. Once all is installed you should be able to share under folder properties.

---

### Post by DexterLB on 2008-06-04
I saw that you've installed system-config-samba, I also installed it, set the shares from there and... voila! it works! Thanks a looot! :popcorn::popcorn::popcorn:

---

