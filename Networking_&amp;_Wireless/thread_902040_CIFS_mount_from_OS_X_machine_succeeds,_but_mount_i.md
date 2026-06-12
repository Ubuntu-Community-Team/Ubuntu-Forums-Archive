---
title: "CIFS mount from OS X machine succeeds, but mount inaccessible?"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by jlongstreet on 2008-08-26
I'm on Mythbuntu 8.04 trying to mount directories on my external drive on my iMac running Leopard.

Here's my fstab line:

```
//192.168.1.100/toaster/test          /mnt/test     cifs    auto,credentials=/root/.credentials
```

```

/mnt# mount /mnt/test
/mnt# ls
test
/mnt# cd test
/mnt/test# ls
ls: cannot open directory .: No such file or directory
# cd ..
# ls
ls: cannot access test: No such file or directory
test
/mnt# ls -al
ls: cannot access test: No such file or directory
total 8
drwxr-xr-x  4 root root 4096 2008-08-26 22:25 .
drwxr-xr-x 21 root root 4096 2008-07-02 02:08 ..
d?????????  ? ?    ?       ?                ? test

```

This worked before I changed the server it mounted from.

What do the question marks in the ls -l listing even mean?

---

### Post by TaTaE on 2011-11-13
I have a similar problem. I couldnt find any answer yet.

I have a lot of files inaccessible for root.

---

