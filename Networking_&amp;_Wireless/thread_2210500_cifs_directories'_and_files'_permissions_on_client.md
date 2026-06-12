---
title: "cifs directories' and files' permissions on client"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by domenico4 on 2014-03-11
I have this in my fstab:

//192.168.0.240/domenico     /mnt/samba/domenico  cifs username=domenico,password=pippo,auto,gid=1000,uid=1000,file_mode=0755,dir_mode=0755    0 0

but if I do: ls -l /mnt/samba/ 
I get:

drwxrwxrwx 2 domenico domenico 0 Mar 11 10:06 domenico

but I'd like to get something like:

drwxr-xr-x 2 domenico domenico 0 Mar 11 10:06 domenico

what's wrong?

Thanks and Best Regards

---

### Post by Morbius1 on 2014-03-11
>  //192.168.0.240/domenico     /mnt/samba/domenico  cifs  username=domenico,password=pippo,auto,gid=1000,uid   =1000,file_mode=0755,dir_mode=0755[COLOR=#0000cd]**,nounix**[/COLOR]    0 0
If you do a "man mount.cifs" you'll see that it disables "stuff" coming from the server.

---

### Post by domenico4 on 2014-03-11
Ok Thanks, it works

---

