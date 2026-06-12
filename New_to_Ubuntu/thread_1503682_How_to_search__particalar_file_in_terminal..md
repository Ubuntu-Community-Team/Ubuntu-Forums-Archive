---
title: "How to search  particalar file in terminal."
date: 2010-06-07
forum: New to Ubuntu
---

### Post by honey_bee on 2010-06-07
Hi,
      As we know that /usr/sbin/vsftpd: The FTP daemon, which is the actual program that runs to provide FTP services.

 
I can see this file in GUI mode but when i go to my terminal I can't see the file "vsftpd" inside sbin. I even use ls -a option but no success. please guide me that how can I view this file using terminal.
 
I also try to use 
 
# grep vsftp to search in the file system but no success.
 
any way to see the file in my terminal...?
 
honey_bee

---

### Post by pastalavista on 2010-06-07
Are you sure it's correctly installed? Try```
sudo apt-get update && sudo apt-get install vsftpd
```

---

### Post by Dayofswords on 2010-06-07
grep searchs within a file, use find to look for a file
```
 find / -name 'programname'
```

---

