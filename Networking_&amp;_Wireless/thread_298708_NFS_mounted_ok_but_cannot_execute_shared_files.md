---
title: "NFS mounted ok but cannot execute shared files"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by jlanza on 2006-11-13
Hi all.

I have successfully mounted a nfs share. I managed to read and write on the files. However I cannot run or execute any file that is in the shared folder.

On server:
```
/etc/exports:
/home/user/directory 128.0.0.0/24(rw,no_root_squash)
```


On client:
```
/etc/fstab
128.0.0.4:/home/user/directory localdir nfs rw,noauto 0 0
```

Then:
```
user$ mount localdir
user$ cd localdir
user$ ./program
bash: ./program : Permission denied
```

"program" is executable and if I copy it to a local directory it runs, but this is not the way of doing this :( ](*,) 

What do I have to do to get executable permissions?

TA

---

### Post by jamesshuang on 2007-03-22
Have you found a solution to this yet? I'm having the same issue!

---

### Post by jlanza on 2007-03-22
I think I did, but cannot remember how.

I think the problem is was something like doing sudo mount whatever.

This way it worked... but I don't remember sorry :(

I forgot to post here the solution

---

