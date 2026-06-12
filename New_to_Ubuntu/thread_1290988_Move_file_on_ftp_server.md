---
title: "Move file on ftp server"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by deltat on 2009-10-14
I'm a bit at a loss. I'm on an ftp server. I try to move a file into another directory, yet the commands mv or cp give invalid results. Here's the screenshot: 

[IMG]http://img63.imageshack.us/img63/4583/screenshot4h.png[/IMG]

Who can help?

---

### Post by mike1821 on 2009-10-14
In FTP you need to use this command:

```
rename filename directory/filename
```

---

### Post by deltat on 2009-10-14
Of course, you're on a server level! it worked thanks.

---

### Post by Sarmacid on 2009-10-14
You can also go on ftp sites through graphical interface with nautilus. Just open it up and click the location bar, then type in [ftp://address](ftp://address) and it will probably be easier.

---

### Post by deltat on 2009-10-14
Thanks a mil

---

