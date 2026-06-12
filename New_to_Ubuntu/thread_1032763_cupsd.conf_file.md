---
title: "cupsd.conf file"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by hawkdog on 2009-01-06
I am trying to modify the cupsd.conf file so that I can print from a windows machine.   I get a message saying that I don't have permission to save the file.  The owner of the file is root.  How can I overcome this?

Thanks

---

### Post by kaibob on 2009-01-06
Enter the following in a terminal window:

```
gksudo gedit /etc/cups/cupsd.conf
```

---

### Post by kaibob on 2009-01-06
hawkdog,

The following is an informative discussion of the reason for and use of sudo and gksudo. You may want to have a look when you have the time.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Welcome to the forum. 

kaibob

---

