---
title: "[SOLVED] network filesystem"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by grahambo2005 on 2008-01-06
hey all

just a very simple question

in a windows network I have 2 pc's pc1 and pc2
I am on pc1 and i need to access C:\myfolder\myfile on pc2

to do this I go \\pc2\C$\myfolder\myfile

How do I do this on Linux?

IE I am on LinuxPC1 and I need acces to /etc/myfile on LinuxPC2. 
Whats the syntax?

Cheers

Graham

---

### Post by samosamo on 2008-01-06
Use nautilus or from the command line smbclient

```
man smbclient
```

---

### Post by grahambo2005 on 2008-01-12
thanks dude!

---

