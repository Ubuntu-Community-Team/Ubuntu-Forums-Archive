---
title: "Samba Problem With Ubuntu Linux"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by dmizer on 2008-04-02
okay ...

let's try this.
run the command (without sudo):
```
chmod u+s /user/bin/smbmnt
```
you'll see that ubuntu will not like it much.

now some information about sudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28root%29](https://help.ubuntu.com/community/RootSudo?highlight=%28root%29)

so ... when something needs to be run suid root, just prefix the command (just as you did with chmod) with sudo.  further, if you want to temporarily enter into a root prompt, you can use the command:
```
sudo su
```

also, instead of using smbmnt, use "mount -t cifs" or "mount -t smbfs"

---

