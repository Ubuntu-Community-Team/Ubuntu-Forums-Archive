---
title: "token ring auto login"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by lagerratrobe on 2007-06-09
Hi,

Can someone point me to the how-to that describes how to setup the network manager/token ring in Dapper so that I don't get prompted for a token ring login everytime I boot up?  I'm the only user of this machine, and I'm sick of having to enter my password multiple times.  I remember "fixing" this on an older machine, but I can't find the thread anymore.

Thanks.

---

### Post by lcg on 2007-06-09
> **lagerratrobe said:**
> 
Can someone point me to the how-to that describes how to setup the network manager/token ring in Dapper so that I don't get prompted for a token ring login everytime I boot up?  I'm the only user of this machine, and I'm sick of having to enter my password multiple times.  I remember "fixing" this on an older machine, but I can't find the thread anymore.

Well, while Token Ring is indeed a network technology, it does not have any kind of login mechanism (OK, there is 802.1X, however this normally wouldn't prompt you for a password). I'm guessing you mean the Gnome Keyring, which has nothing to do with Token Ring.

You can use PAM and your usual login password to unlock your keyring. To enable this, you have to install pam_keyring:
```
sudo apt-get install libpam-keyring
```
After that, you need to edit the file /etc/pam.d/gdm:
```
sudo nano /etc/pam.d/gdm
```
Add the following line to the end of the file (**if you are using Feisty**):
```
@include common-pamkeyring
```

If you are using an older version, you need to add these two lines at the end instead:
```
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```

The next time you log in, your login password is automatically used to unlock the Gnome keyring. Obviously, this will only work if the two passwords are the same.

HTH,
Lars

---

