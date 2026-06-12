---
title: "how to check my server status"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by jimfuture12345 on 2010-01-15
hi i have installed ubuntu server with proftpd and i want to check the status of ftp what is the mathod ?

---

### Post by yeats on 2010-01-15
> hi i have installed ubuntu server with proftpd and i want to check the status of ftp what is the mathod ? 

By "status" do you mean whether the ftp program is running or not?  If so, the command would be:

```
ps aux | grep ftp
```

That lists all of your system's processes and the user running each one, then searches the output of that command for "ftp".

---

