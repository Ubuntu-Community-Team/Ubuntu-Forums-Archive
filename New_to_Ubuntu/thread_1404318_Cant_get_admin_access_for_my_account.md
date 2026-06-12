---
title: "Cant get admin access for my account"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Bnosidda on 2010-02-11
It says I'm not in the sudoers file, how do i fix this, i cant download anything off of the package manager, and cant use sudo, how do i get into the file?

---

### Post by skymera on 2010-02-11
During install you create an account and a password.
This always has sudo access, always has done on Ubuntu.

Have you created this account yourself after install?

---

### Post by Iowan on 2010-02-11
[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by Satoru-san on 2010-02-11
basically somehow your user got out of the wheel/admin group. This is a problem as you cant just "fix" it by being logged in as your user, you have to be root.

Here is how to do that.

boot your live cd and choose try
open a term and do this.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
```

This will give you root access. you need to switch sda1 with your correct ubuntu / root partition.

then you can make your self a sudoer

```
gpasswd -a <user> wheel
gksudo gedit /etc/sudoers
```

and add your user

reboot.

---

