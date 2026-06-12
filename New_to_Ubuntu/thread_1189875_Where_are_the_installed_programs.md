---
title: "Where are the installed programs??"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by raziiq on 2009-06-17
Where are all installed programs placed in uBuntu? Like we have installed programs in Windows under Program Files.

---

### Post by Celauran on 2009-06-17
That's not how it works in Linux. Installed programs don't occupy one directory. For instance, /etc/ contains the configuration files for all programs, while the executables themselves may be installed to /usr/bin

---

### Post by raziiq on 2009-06-17
/usr/bin thats what i was asking, thanks for the info man :)

---

### Post by Mark Phelps on 2009-06-17
> **raziiq said:**
> /usr/bin thats what i was asking, thanks for the info man :)

He said "may" be installed to /usr/bin.  

There's also /usr/local/bin, and /usr/sbin -- and others I don't recall at the moment.  Also, it's fairly typical for apps to created hidden directories under your /home directory and store files and settings there. 

Basically, there's no one directory where ALL the application programs get saved in Linux.

---

### Post by m_duck on 2009-06-17
If you want to find the location of a specific executable, you can use the **which** command.```
which firefox
```for example, will return```
/usr/bin/firefox
```

---

### Post by Paqman on 2009-06-17
It's also worth pointing out that in Linux you don't need to know the path to the executable to launch it.

For example, Firefox may be at /usr/bin/firefox, but to launch it you only need to use the command ```
firefox
```

Linux is a lot smarter than Windows that way.

---

