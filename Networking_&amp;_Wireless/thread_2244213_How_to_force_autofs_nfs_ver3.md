---
title: "How to force autofs nfs ver3"
date: 2014-09-14
forum: Networking &amp; Wireless
---

### Post by bioapt on 2014-09-14
my ubuntu 12 works well to recognize the version
my suse worked well when I force nfs version 3 in config
however, I can not manage it in ubuntu 14.04.1

I am using a server, autofs home and one special directory called /scratch,
it mounted very slow and eventually it showed with (nfs, vers=4) if I checked it with "mount".
all the owner and groups information were missing...

my nfs server is actually nfs 3, which I am not allowed to change. 

please help... how can I force autofs with nfsvers=3 in ubuntu 14.04.1? I tried some many methods, auto.master, auto.misc, and default/nfs-common, but all of them failed, the system insisted to mount it as nfsvers=4 as default....

thank you very much in advance.

---

### Post by bioapt on 2014-09-15
up

---

### Post by LewisTM on 2014-09-28
Use the parameter -vers=3 in your config file.
For example, I have /etc/auto.nfs containing
```
directory  -vers=3,rsize=8192,wsize=8192,intr   server:/share 
```
Cheers!

---

### Post by vasa1 on 2014-09-28
@LewisTM, great to see you posting again!

---

### Post by LewisTM on 2014-09-28
Hehe yeah I'm sill alive xD
Just have less free time to monitor the forums...

---

### Post by vasa1 on 2014-09-28
> **LewisTM said:**
> Hehe yeah I'm sill alive xD
Just have less free time to monitor the forums...I always wonder when people disappear. I read "Atlas Shrugged" years ago but remember John Galt taking *some* people away ;)

---

