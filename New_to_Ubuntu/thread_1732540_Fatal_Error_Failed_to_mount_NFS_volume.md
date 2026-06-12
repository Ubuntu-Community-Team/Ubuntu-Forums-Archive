---
title: "Fatal Error: Failed to mount NFS volume"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by umar00o on 2011-04-18
Hello guys,
This is my first post to this site and i am newly registered. Currently i am having a problem with my FOG image server. When i try to upload a windows 7 machine image to it its give me error' Fatal error : Failed to mount NFS volume'' . I am not really good in linux as i am windows person. Could you please help me with this as a biggner please. thanks for your help.
 
My server and operating system details.
 
Server: Dell Poweredge 840
OS: Ubuntu 9.10
 
Thanks waiting for your help...
 
I have checked and .mntcheck does exsists in image and dev folder.

---

### Post by umar00o on 2011-04-21
Hello any body help please...

---

### Post by th3fjong on 2011-10-06
Hi ;) im having the same error,

i tried this no luck though :/ 

In the folder on your server, check for the **.mntcheck files**. If these are not there then perform the following commands [Linux Systems Only] 
**touch /images/dev/.mntcheck ** 
**touch /images/.mntcheck ** 

If still receiving the same error message after perfroming the above  commands, you may need to edit /etc/exports to include your new mount  point, i.e. /data/images and /data/images/dev with corresponding  permissions. 
See following example of /etc/exports: 

/images *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure) 
/images/dev *(rw,sync,no_wdelay,no_root_squash,insecure) 
**/data/images *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)** 
**/data/images/dev *(rw,sync,no_wdelay,no_root_squash,insecure)**

---

