---
title: "update manager error"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by HunkieChan on 2008-12-12
hello guys. i get this error every time i try update my system

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Invalid record in the preferences file, no Package header'

thanks in adavance

---

### Post by iponeverything on 2008-12-12
This should fix you up. Just get rid preferences:

```
mv /etc/apt/preferences /root/apt.preferences.bkup

```

---

### Post by cariboo on 2008-12-12
You can report bugs [here,]("http:///bugs.launchpad.net/")

Have you tried in a Applications-->Accessories--Terminal:

```
sudo apt-get reinstall update-manager
```

Jim

---

### Post by HunkieChan on 2008-12-12
> **iponeverything said:**
> This should fix you up. Just get rid preferences:

```
mv /etc/apt/preferences /root/apt.preferences.bkup

```

thanks alot bro, that worked

---

### Post by clarke_j on 2008-12-17
Hello - brand new to Ubuntu and Lynux here.

I've got the same problem as described above however when I put

 "mv /etc/apt/preferences /root/apt.preferences.bkup"

into the terminal I get is:

"mv: cannot stat `/etc/apt/preferences': No such file or directory"

I seem to get the same type of error with update manager and synaptic package manager. I believe this problem started when I downloaded Adobe Flash 10.

PS - running the latest ubuntu of a usb drive - if that makes ant difference!

Any Ideas?

---

