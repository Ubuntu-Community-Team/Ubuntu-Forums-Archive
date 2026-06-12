---
title: "auto-run script on login"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by sa125 on 2009-02-25
I've written a small script that mounts drives on my network, and I want it to run when I login. How do I do that? I recall there should be some script in ~/ that does that, but can't remember what.

---

### Post by swoll1980 on 2009-02-25
> **sa125 said:**
> I've written a small script that mounts drives on my network, and I want it to run when I login. How do I do that? I recall there should be some script in ~/ that does that, but can't remember what.

Go to system preferences sessions, and add it to startup programs

---

### Post by sa125 on 2009-02-25
> **swoll1980 said:**
> Go to system preferences sessions, and add it to startup programs

Thanks. This script needs to be run as the superuser - will it do the trick?

---

### Post by swoll1980 on 2009-02-25
> **sa125 said:**
> Thanks. This script needs to be run as the superuser - will it do the trick?

in the box for adding the program tick the run in terminal and use sudo in the command that should work I think

---

### Post by swoll1980 on 2009-02-25
There's a place to run networking scripts on boot it's like
 /etc/init.d/ 



Edit

change the permission of the file as well
sudo chmod +x FOO /path to file

---

### Post by sisco311 on 2009-02-25
Why don't you use the /etc/fstab to mount it at boot time?

---

### Post by swoll1980 on 2009-02-25
> **sisco311 said:**
> Why don't you use the /etc/fstab to mount it at boot time?

Cause he doesn't know about it and neither did I :p

---

### Post by sisco311 on 2009-02-25
oh, okay.

It's a windows(samba/cif) or linux(nfs) share?
Could you post the script?


[uhelp]8.04/serverguide/C/network-file-system.html[/uhelp]
[uhelp]community/MountWindowsSharesPermanently[/uhelp]

---

### Post by sa125 on 2009-02-25
> **sisco311 said:**
> oh, okay.

It's a windows(samba/cif) or linux(nfs) share?
Could you post the script?


[uhelp]8.04/serverguide/C/network-file-system.html[/uhelp]
[uhelp]community/MountWindowsSharesPermanently[/uhelp]

It's a samba share on a local network. I had to do some configuration and installation on the server - [see this post](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html).

The actual mounting once you configure the server is simple:
```

sudo mount <server-name>:/path/to/share/ /path/to/local/mnt/
```

---

### Post by sisco311 on 2009-02-25
from the tutorial:
> 

Mounting at boot using /etc/fstab

If you want to mount using fstab file

sudo vi /etc/fstab

In this example my /etc/fstab was like this

```
server.mydomain.com:/files /files nfs size=8192,wsize=8192,timeo=14,intr
```

Change &#8220;servername.mydomain.com:/files&#8221;, and &#8220;/files&#8221; to match your server name,share name, and the name of the mount point you created.

if you don't like vi, then use gedit to edit the file:
```
gksu gedit /etc/fstab
```

---

### Post by sa125 on 2009-02-26
> **sisco311 said:**
> from the tutorial:


if you don't like vi, then use gedit to edit the file:
```
gksu gedit /etc/fstab
```

Thanks, I'll give it a try.

---

