---
title: "System log viewer can't open some log files"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by occams_beard on 2009-11-12
When I open the log viewer there's this error message at the top that says


Could not open the following files:
```

/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/btmp: You don't have enough permissions to read the file.
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory

```

Wonder why I can't view these, or why these logs don't exist?

---

### Post by coldReactive on 2009-11-12
Did you run sudo or gksudo to run the log viewer? IE: sudo <command> OR gksudo <command>

```
/var/log/btmp: You don't have enough permissions to read the file.
```

is saying you didn't.

---

### Post by occams_beard on 2009-11-12
Ah, if i run 

```
sudo gnome-system-log
```

There are indeed no error messages... Although when I launch it from the System > Administration > Log Viewer it shows those errors.

Odd that it doesn't popup a gksudo when launching it from there, eh? Oh well, no biggie.

---

### Post by whoop on 2009-11-12
I have the same issue. Posted a thread about it a while back:
[http://ubuntuforums.org/showthread.php?t=1315549](http://ubuntuforums.org/showthread.php?t=1315549)

Didn't really solve it.

On my machines the files aren't there. On some machines the log viewer does complain on others it doesn't (in all occasions it was launched from System > Administration > Log Viewer).

Did you do an upgrade?

---

### Post by occams_beard on 2009-11-12
Yes, did a distro upgrade from jaunty to karmic. I do not remember seeing the error message in Jaunty.

---

### Post by whoop on 2009-11-12
Oh, well it's not a big issue. But nonetheless:
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/481706](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/481706)

---

### Post by Squideshi on 2010-05-02
> **occams_beard said:**
> 
/var/log/btmp: You don't have enough permissions to read the file.


[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

