---
title: "System logging is not happening"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-08-18
Today while doing an infrequent check, I found a rather unwanted situation. /var/log/messages is empty. And the last line in /var/log/messages.1 says,
```
Apr  9 09:52:14 Dell-Home 20microsoft: debug: /dev/sdb1 is not a MS partition: exiting
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Apr  9 09:52:14 Dell-Home 30utility: debug: /dev/sdb1 is not a FAT partition: exiting
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
Apr  9 09:52:14 Dell-Home 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Apr  9 09:52:14 Dell-Home os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Apr  9 09:52:41 Dell-Home kernel: Kernel logging (proc) stopped.

```

Why is this happening? 

/dev/sdb1 is there and is usable.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              18G  2.9G   14G  18% /
none                  1.5G  672K  1.5G   1% /dev
none                  1.5G  1.1M  1.5G   1% /dev/shm
none                  1.5G  140K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda1              23G   18G  3.7G  83% /home
/dev/sdb1             147G   82G   58G  59% /home/masroor/Videos
/dev/sda2              31G   13G   16G  45% /usr

```

I am using natty updated to latest.

Any suggestion will be appreciated.

---

