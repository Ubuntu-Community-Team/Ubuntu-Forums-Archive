---
title: "Web Directory Permissions"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by cphillips on 2010-10-29
Used "sudo chmod 777 -R /home/*user*/Public" on the directory used in a newly created Virtual Host. Every file/folder in the directory changed the permissions accordingly, but any new file that I FTP into that folder still leaves "None" in the Group and Others permission status. I certainly don't want to be running the chmod command every time I FTP a new file into that folder.    Ubuntu 10.4 
 
Much appreciated.

---

### Post by bioterror on 2010-10-29
> **cphillips said:**
> Used "sudo chmod 777 -R /home/*user*/Public" on the directory used in a newly created Virtual Host. Every file/folder in the directory changed the permissions accordingly, but any new file that I FTP into that folder still leaves "None" in the Group and Others permission status. I certainly don't want to be running the chmod command every time I FTP a new file into that folder.    Ubuntu 10.4 
 
Much appreciated.

You didnt tell us what kind of ftp client you're using.
So I am assuming you're using gftp and there's already a tap for "preserve file permissions".

If you have set chmod 777 for a file, it will keep it at the ftp server side too.

---

