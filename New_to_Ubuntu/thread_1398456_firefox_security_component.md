---
title: "firefox security component"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by warpaint on 2010-02-04
i am new to xubuntu still and when i open firefox 3.5

i get this message in a pop-up 

"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

if anyone could help i would appreciate it

---

### Post by cariboo on 2010-02-05
The easiest thing to check, is if your hard drive full. Open a terminal and type:

```
df -h
```

The results will look something like this:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             110G   66G   40G  63% /
none                 1001M  308K 1001M   1% /dev
none                 1005M  1.5M 1004M   1% /dev/shm
none                 1005M  108K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
none                  110G   66G   40G  63% /var/lib/ureadahead/debugfs
```

note the first line that ends with a /. the percentage should be lower than 90%. If it isn't you'll have to create some free space on your hard drive.

---

### Post by drzoo2 on 2010-02-05
> **warpaint said:**
> i am new to xubuntu still and when i open firefox 3.5

i get this message in a pop-up 

"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

if anyone could help i would appreciate it

Check and make sure your the owner of all the files and folders in your home directory.
Open a terminal and type the following
```

cd ~
ls -la   <------you should be the owner and group of all the files except ..

```

---

### Post by warpaint on 2010-02-05
thank you for reply i have tried both methods on the first 

it says that 14% of hddrv used

on second reply i am owner of all folders 

is it possible that secure server for firefox has been disabled i got a message that said ssl_secure_server disabled how i did this i do not know or how to fix perhaps this is the the error that needs fixed??

---

