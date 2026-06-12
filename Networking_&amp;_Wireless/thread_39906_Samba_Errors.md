---
title: "Samba Errors"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by paulie on 2005-06-07
Hello and thanks in advance if anyone can help me here. I'm having Samba problems to share files and printer. This is the error


root@ubuntu-box:/home/paul # testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.
root@ubuntu-box:/home/paul # /usr/share/doc/samba-doc
bash: /usr/share/doc/samba-doc: is a directory
root@ubuntu-box:/home/paul #
 
Have searched for a soluition for hours now and I am very new to Linux so please be kind asI'm not the sharpest knife in the draw

---

### Post by localzuk on 2005-06-08
Can you post your smb.conf file.

The error message leads me to believe that you have a section set like this:

```

[xyz]
[abc]

```

Without anything in one of the sections? If you have you need to solve it by giving it a path ie.
```

path = /xy/z/

```

---

