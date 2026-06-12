---
title: "Eth issues"
date: 2018-07-30
forum: Networking &amp; Wireless
---

### Post by jroehr on 2018-07-30
I cannot get my networking to start. NetworkManager fails each boot.
Also, I cannot edit /etc/resolv.conf. When I do "ls /etc/resolv.conf" it says it exists, but when i try to edit or echo into it it says "-bash: /etc/resolv.conf: No such file or directory" (as root and as sudo). Please let me know what other information I can give to help. Thank you.

---

### Post by steeldriver on 2018-07-30
Hello and welcome to the forums

What does the "long" output from ls say?

```

ls -l /etc/resolv.conf

```

Perhaps it is a broken symbolic link?

BTW editing the file should only be regarded as a short-term step to restoring the network - in modern distributions it's a symbolic link that is created / managed on the fly

---

### Post by jroehr on 2018-07-30
lrwxrwxrwx 1 root root 29 Jun 10 17:02 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
Appears to be a broken symlink (no such file/dir as listed), but what should it link to?
EDIT: Still failing. Output of "systemctl start NetworkManager" : NetworkManager.service: Failed at step EXEC spawning /usr/sbin/NetworkManager: No such file or directory
It seems the installation of networkmanager is beyond screwed up, but I don't know how to reinstall w/o internet. Please help if possible. Thank you.

---

