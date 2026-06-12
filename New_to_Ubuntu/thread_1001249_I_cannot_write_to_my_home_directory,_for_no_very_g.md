---
title: "I cannot write to my home directory, for no very good reason"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by jen_carreg on 2008-12-03
Hi,

I`d be grateful if anyone could help with the following problem.  

I`ve just done a re-installation because my filesystem was in an almighty mess (I still don`t know why, but fsck didn`t fix it).  So everything in / and /var is completely new, but I kept my old /home partition.  (I`m using xubuntu, whatever the most recent version is -- just downloaded the install cd this evening.)

After the re-installation it booted all right and I was able to log in.  But I don`t seem to be able to write to my home directory at all.  I have checked that it is down as my home directory (using Users and Groups).  I have used chmod to change the permission so that _all_ users (not just the owner of the directory) should be able to write to it.  I have used chown to make sure my home directory is actually owned by me.  It`s still coming up with `permission denied`.

The permissions for the directory now look like this:
root@amethyst:/home/jmstone# ls -l /home/
total 60
drwxrwxrwx 63 jmstone jmstone  4096 2008-12-03 23:53 jmstone

I can read files.  I can also write to the directory as root, so there isn`t some fundamental problem with being able to write to that partition.  (Is there?)

Can you tell me what might cause this problem?  I`m flummoxed by the permissions being different from what it says the permissions are...  I hope it`s just something obvious I`ve overlooked.  

Cheers in advance,
Jen

---

### Post by sdowney717 on 2008-12-03
try this!

sudo chown -R test:test /home/test

substitute your user name for test

---

### Post by sdowney717 on 2008-12-03
I used this to restore my /home/username directory to another install of ubuntu. It restored my menu items and all was well.
I simply had created a user named test on the other system, copied my user files over onto the directory (make sure hidden files are selected) i wished to restore onto, ran that command and when I logged in with test, it was all there.

---

### Post by handydan918 on 2008-12-03
Just out of curiosity, try ```
cd /
```and then ```
df -h home
```and give us the output of the second command.

```
ls-l home 
```might be interesting too...

---

### Post by chongzi35 on 2008-12-03
Through conduit **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed for oil & gas pipeline service. Featured with double block and bleed function, the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is suitable for bi-directional flow isolation.

---

### Post by kwilliam on 2008-12-03
> **sdowney717 said:**
> try this!

sudo chown -R test:test /home/test

substitute your user name for test

This is the same as chown, but recursively applies the ownership changes to all directories inside, in case you're wondering what the -R is.

---

### Post by iaculallad on 2008-12-03
Try using symbolic permission:

```
sudo chmod -R u+rwX,og-rwx /home/jmstone
```

---

