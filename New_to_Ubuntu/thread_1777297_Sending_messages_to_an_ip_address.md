---
title: "Sending messages to an ip address"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-06-07
Is there any command to send message to an ip address in linux like the windows commands **net send**?

---

### Post by Toz on 2011-06-07
```
smbclient -M <targetmachine>
```

[http://www.examplenow.com/smbclient/man1]("http://www.examplenow.com/smbclient/man1")

---

### Post by 1991sudarshan on 2011-08-16
> **Toz said:**
> ```
smbclient -M <targetmachine>
```[http://www.examplenow.com/smbclient/man1](http://www.examplenow.com/smbclient/man1)


 If do not know the target machine name then how shall id send it? Do i have replace the target machine name with the target ip address?

---

