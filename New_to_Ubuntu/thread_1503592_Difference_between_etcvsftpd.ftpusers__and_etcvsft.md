---
title: "Difference between /etc/vsftpd.ftpusers  and /etc/vsftpd.user_list  file"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by honey_bee on 2010-06-07
hi
    In Linux for ftp server  there are two files 
 
/etc/vsftpd.ftpusers   and
/etc/vsftpd.user_list

well i know that the file **/etc/vsftpd.ftpusers** is the list of users those are not allowed to login via ftp but for **/etc/vsftpd.user_list **why this file is user. Almost both files have same users list .Please guide me the main purpose of these two files

thanks in advance
honey

---

### Post by Bachstelze on 2010-06-07
Why did you create those files in the first place? Generally there is only one (with whatever name you want, vsftpd.user_list being the default).

---

### Post by honey_bee on 2010-06-07
thanks for the reply. well these files are already built in Linux.I does't know the main purpose of these two files ?

---

### Post by Bachstelze on 2010-06-07
> **honey_bee said:**
> thanks for the reply. well these files are already built in Linux.I does't know the main purpose of these two files ?

Define "Linux" (i.e. which distro?). They definitely aren't there by default in Ubuntu.

---

### Post by honey_bee on 2010-06-07
In red hat linux 9

---

### Post by Bachstelze on 2010-06-07
Paste the contents of your vsftpd.conf, then.

---

