---
title: "how to get the user name of the person who called the sudo command?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by outleradam on 2010-02-13
I have a script which is called with sudo ./script.sh. script.sh creates files and sets permissions.  When I try to get the user name it returns root.    

How can I get the username of the person who called the sudo command so that the user read and write to the files without having to chmod it?

---

### Post by wallaroo on 2010-02-14
The environment variable $SUDO_USER holds the name of the account running the sudo command.
So if you want them to have ownership of a file, you could include in the script something like ..
```
chown $SUDO_USER.$SUDO_USER filename
```

---

