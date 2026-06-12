---
title: "Cannot write to Drobo"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by sunseeker888 on 2009-03-27
Hello Guys


I have a little problem. I have a drobo extrenal drive 2TB and NAS WD 1TB. My Nas is full now, that's why I got the Drobo, as it's expandable to 16TB in the future.


I formatted the Drobo to XFS, as most the files I need to transfer from the NAS are above 4GB in size.


I attached the drobo via USB (I do not have the Droboshare yet, to make the drobo work as a NAS). The computer mounts the drobo, and I can see it on the desktop. When I try to copy files from the WD nas, it won't allow me it's saying permission deny.


The drbo usb HDD is label drobo


I tried those 2 commands to make the drobo writable and it's not working, it's says I have no permission to do those 2 command, I even did sudo

chmod 777 /dev/sdb1
chmod 777 /media/drobo




what am I doing wrong here?

---

### Post by cariboo on 2009-03-27
I would suggest trying:

```
sudo chmod -R 777 /media/drorbo
```

Jim

---

### Post by sunseeker888 on 2009-03-27
> **cariboo907 said:**
> I would suggest trying:

```
sudo chmod -R 777 /media/drorbo
```

Jim



Thanks a lot JIm, already started copying 1TB. I was not putting that -R command. 


Really appreciate
Oh dear it will take 104 hours to back up that 1TB

Cheers


S888

---

