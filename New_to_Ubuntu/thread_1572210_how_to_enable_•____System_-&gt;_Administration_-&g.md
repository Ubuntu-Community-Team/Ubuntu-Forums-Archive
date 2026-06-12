---
title: "how to enable •    System -&gt; Administration -&gt; Services"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by uwm_res on 2010-09-10
I have tried UBUNTU 10.04 and 9.04 and still have not seen   
[LIST]
[*]System -> Administration      -> Services:
[/LIST]
i have come across several of the commands for UBUNTU talk about using this and i would like to know, how to enable this or is this a bug...

Thanks for reading this and would appreciate a reply  :o

---

### Post by jtarin on 2010-09-10
Could you be a little more explicit? What exactly are you looking for at Services? Do you have a link to these commands used?

---

### Post by 3rdalbum on 2010-09-10
The Services program does not work with Ubuntu 9.10 and later because Ubuntu now uses the Upstart daemon instead of init scripts.

If you see HOWTOs for earlier versions of Ubuntu, you should not follow them because they get outdated very quickly and may cause problems on the later system.

---

### Post by uwm_res on 2010-09-12
Thanks for the response:
There were various scripts that require me to use services, one of them is 
" Enable the Samba and NFS services  
[LIST]
[*]System -> Administration -> Services
[*]Enable the services by browsing through the list on the left and locating nfs and smb.  If they are not already enabled, enable them by clicking the "Enable" button"
[/LIST]
And when i see System -> Administration -> Services, i have to look around for commands that i have to write in terminal, and certain times, those command donot work. 
There i was looking i there was a terminal command which would enable it, if it was disabled..


> **uwm_res said:**
> I have tried UBUNTU 10.04 and 9.04 and still have not seen   
[LIST]
[*]System -> Administration      -> Services:
[/LIST]
i have come across several of the commands for UBUNTU talk about using this and i would like to know, how to enable this or is this a bug...

Thanks for reading this and would appreciate a reply  :o

---

### Post by uwm_res on 2010-09-12
I am using older version, UBUNTU 9.04, as some of the commands i was using in 10.04, didnot work, still i see services  disabled here in UBUNTU 9.04

> **3rdalbum said:**
> The Services program does not work with Ubuntu 9.10 and later because Ubuntu now uses the Upstart daemon instead of init scripts.

If you see HOWTOs for earlier versions of Ubuntu, you should not follow them because they get outdated very quickly and may cause problems on the later system.

---

### Post by JustinR on 2010-09-12
Hi, if you want to modify Ubuntu services, 

Applications > Accessories > Terminal
```

sudo apt-get install rcconf

```

Then run:
```

sudo rcconf

```

And disable/enable any services you like. There are plenty of other service managers also besides rcconf, you can browse Synaptic.

---

### Post by 3rdalbum on 2010-09-13
You need to install the Samba server. When you do, it will start immediately and run on boot.

---

