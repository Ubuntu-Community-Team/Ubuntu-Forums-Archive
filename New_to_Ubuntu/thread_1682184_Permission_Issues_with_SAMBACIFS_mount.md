---
title: "Permission Issues with SAMBA/CIFS mount"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by freelancer1995 on 2011-02-05
Hi

ok, i have an all-in-one server, i have a cifs share called "freelancer", when i mount the share using; 

```
sudo mount -t cifs //192.168.1.1/freelancer /home/freelancer/cifs -o user=freelancer,password=mysecretpassword
```

i have read-only access, because the owner of the mount is seen as "root"

if i run the command with; 

```
mount -t cifs //192.168.1.1/freelancer /home/freelancer/cifs -o user=freelancer,password=mysecretpassword
```

it obviously fails as i do not have permission to mount drives.  how do i mount the drive, so mr normal user can write to it without mounting it via the fstab?

thanks in advance

free

---

### Post by Morbius1 on 2011-02-05
Take possession of the mount point by adding uid=1000 to the list of options in the sudo mount command:
```
 sudo mount -t cifs //192.168.1.1/freelancer /home/freelancer/cifs -o user=freelancer,password=mysecretpassword,uid=1000
```

---

### Post by freelancer1995 on 2011-02-05
thanks Morbius1, i just found a similar solution of adding to the -o ```
uid=freelancer,password=mysecretpassword
```

but your solution is tidied thanks free :)

---

