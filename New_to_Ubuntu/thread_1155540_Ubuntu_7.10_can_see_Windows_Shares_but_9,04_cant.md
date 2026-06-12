---
title: "Ubuntu 7.10 can see Windows Shares but 9,04 cant?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by RichTJ99 on 2009-05-10
Hi,

I have two Dell M1210 laptops (identical specs).  One is running 7.10 & has no problem seeing my Window's PCs & my DNS-323 NAS.

I access this by going to places, then Network.  It sees "Windows Network", I click on that & it sees my "Home" windows workgroup.

I can then browse to the machines I want, copy the data, etc.  

My recently repaired second Dell M1210 laptop came with a clean hard drive.  I figured I would setup 9.04 & see whats new.  Now, when I go to the Network, it sees "windows network", then it sees the "home" workgroup but I get the error:

Unable to mount location: Failed to retrieve share list from server 

Any ideas whats changed or how to fix it?  I did some research but nothing seems ot work.

Thanks,
Rich

---

### Post by superprash2003 on 2009-05-11
its a common samba nautilus bug , you would have to use the direct link to access like smb://x.x.x.x where x.x.x.x is the ip of the machine you want to access.

---

### Post by Peter09 on 2009-05-11
This can also happen when you already have the share mounted.

---

### Post by RichTJ99 on 2009-05-11
Hi,

So how should I fix the issue?  Just goto the "connect to server"? 

Thanks,
Rich

---

### Post by Peter09 on 2009-05-11
You can try this:

```
sudo apt-get install winbind
```

and
```
gksu gedit /etc/nsswitch.conf
```

make the line which starts with hosts look like this
> hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

then
```
sudo /etc/init.d/winbind restart
```
and
```
sudo /etc/init.d/samba restart
```
might make a difference as it improves name resolution for windows machines.

---

### Post by RichTJ99 on 2009-05-11
Peter,

Thanks!  That did the trick!  

Rich


> **Peter09 said:**
> You can try this:

```
sudo apt-get install winbind
```

and
```
gksu gedit /etc/nsswitch.conf
```

make the line which starts with hosts look like this


then
```
sudo /etc/init.d/winbind restart
```
and
```
sudo /etc/init.d/samba restart
```
might make a difference as it improves name resolution for windows machines.

---

