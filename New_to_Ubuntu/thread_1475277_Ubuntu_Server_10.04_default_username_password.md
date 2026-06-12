---
title: "Ubuntu Server 10.04 default username password?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by BioVirtual on 2010-05-06
I just installed Ubuntu Server. It's asking for username and password which I didn't choose during installation.

---

### Post by Iowan on 2010-05-06
Hmmm... I didn't think you could set up a machine without choosing username/password. You can see if [this]("http://www.psychocats.net/ubuntu/resetpassword") helps...

---

### Post by _0R10N on 2010-05-06
It's pretty weird but, well.. if you don't have any user account created, then drop to the root shell as suggested Iowan. Once you're in the shell, you can change (in this case, set) the password for root user.
```
passwd root
```

Remember that the root user can't login into a gnome session, so you'll have to create, at least, one account.

Kind regards!

---

### Post by Iowan on 2010-05-06
[Here]("https://wiki.ubuntu.com/RootSudo") is a help page you should see before setting up a root password.

---

