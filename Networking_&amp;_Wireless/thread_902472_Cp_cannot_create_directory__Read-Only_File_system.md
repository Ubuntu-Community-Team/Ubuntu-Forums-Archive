---
title: "Cp: cannot create directory : Read-Only File system"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by prats84 on 2008-08-27
I have mounted a nfs using

 ```
sudo mount -tnfs -onolock 192.168.11.13:/nfsroot /mnt
```

 192.168.11.13 is my ip for the nfsserver

in my /etc/exports

```
 /nfsroot         192.168.11.0/24 (rw,no_root_squash,async)
```




Now, 
 the issue is when i try to copy the file system to /mnt i get Read-only filesystem

Copy command

      ```
  sudo cp -ax /. /mnt/.
``` 
     
Output:
```
 Cp: cannot create directory '<directory Names>': Read-Only File system
```



Please help me ... how can i sort this out... its urgent

Thanks all in advance


Thank You
Pratik

---

### Post by prats84 on 2008-08-28
can some1 plz help me out with dis.... 
 i tried to search stuff but all i get is to change the permission of the nfsroot directory .. i hve done tht.. but still not able to copy ... 



Thank You

---

### Post by prats84 on 2008-08-28
Problem solved Guys thnx... 
 there was a issue with /etc/exports

and i was... not able to do ...
  sudo exportfs -rv

---

