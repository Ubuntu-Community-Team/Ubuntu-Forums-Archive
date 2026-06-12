---
title: "getting root access"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Somiac on 2009-03-04
I just installed ubuntu last night, and I accidentally set my user as just a...user

Is there anyway to set myself as the root user inside of ubuntu?! When you list all the users in shell it doesn't have any root user...

---

### Post by albandy on 2009-03-04
your  have to use sudo.
to act as root type sudo command_to_run

root is disabled by default, it's not secure to use it.

---

### Post by Titan8990 on 2009-03-04
In Linux users are not "set" as the root user. Root is the name of the user. You are by default, in the admin group which allows you to use sudo to run things as root. In Ubuntu, the root account is locked by default for security purposes. Unlocking the root account is neither recommended or supported here on the forums.

For more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2009-03-04
Maybe this would explain a little better.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Nepherte on 2009-03-04
If you somehow lost your admin privileges, you can reboot using the recovery mode. Then you can add yourself back to the admin group with:
```
gpasswd -a youruser admin
```

---

### Post by Somiac on 2009-03-04
Okay, thanks for the quick replies/tips :)

---

### Post by Titan8990 on 2009-03-04
> **Nepherte said:**
> If you somehow lost your admin privileges, you can reboot using the recovery mode. Then you can add yourself back to the admin group with:
```
gpasswd -a youruser admin
```


That would be the correct method for my distro but I think debian users should use adduser:


sudo adduser youruser admin

---

### Post by Nepherte on 2009-03-04
If you use adduser, it's
```
sudo adduser -a -G admin youruser
```

---

### Post by tracerbullet on 2009-03-04
> **Nepherte said:**
> If you use adduser, it's
```
sudo adduser -a -G admin youruser
```
Just for the record, I typed this in Debian and apparently there is no 'admin' group. Does it have another name in Debian?

---

