---
title: "Update Error Message Origin?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by mikodo on 2009-10-06
Is this update error message a problem from my end or from the Update server?

Thanks.

---

### Post by kanikilu on 2009-10-06
> **mikodo said:**
> Is this error update error message a problem from my end or from the Update server? That should be on your end. Make sure there are no other instances of Synaptic, Add/Remove software, Update Manager, or apt-get/aptitude from the command line, running at the same time. If it's not immediately obvious what it is, you could just try killing all processes with "apt" in the name: ```
sudo pkill apt
```

If you are keen to figure out *exactly* what's locking it, open a terminal and run the following command: ```
lsof /var/cache/apt/archives/lock
``` That should give you the name and process ID of whatever is tying it up. Then it's just a matter of killing it: ```
sudo kill -9 <pid>
```

---

### Post by mikodo on 2009-10-06
[QUOTE=kanikilu;8062193]That should be on your end. Make sure there are no other instances of Synaptic, Add/Remove software, Update Manager, or apt-get/aptitude from the command line, running at the same time. If it's not immediately obvious what it is, you could just try killing all processes with "apt" in the name: ```
sudo pkill apt
```

If you are keen to figure out *exactly* what's locking it, open a terminal and run the following command: ```
lsof /var/cache/apt/archives/lock
``` That should give you the name and process ID of whatever is tying it up. Then it's just a matter of killing it: ```
sudo kill -9 <pid>
```[/QUOTE

Duh..., I think I had two Update Manager processes running at the same time initially. Thanks for the reply! The updates have successfully been configured.

---

