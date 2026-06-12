---
title: "update issue"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by metzy85 on 2009-02-07
linux-image Version 2.6.27-7.16:. It wont install the update it says 

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

---

### Post by avtolle on 2009-02-07
This may be due to the partition being (almost) full. From the terminal (Applications>Accessories>Terminal) input```
df -h
```to see if this is possibly a reason. If it is, you will need to make some room by deleting prior versions of the kernel, using Synaptic. It is advised to keep not only the current kernel but the one right before it to ensure you have a working kernel.

---

### Post by metzy85 on 2009-02-07
How do i remove the old versions because that command does nothing for me in terminal. But i also forgot how to become root so that may  be the problem

---

### Post by avtolle on 2009-02-07
```
df -h
```should give you output listing the amount of space free, in human terms, on your HDD, by partition within the system. Note that I asked you to run this solely to determine whether you have a space problem. If you aren't (almost) out of space then removal of old kernels to make more room won't solve your problem.

---

### Post by avtolle on 2009-02-07
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             5.8G  4.1G  1.6G  73% /
varrun                410M  232K  409M   1% /var/run
varlock               410M     0  410M   0% /var/lock
udev                  410M   64K  410M   1% /dev
devshm                410M   44K  410M   1% /dev/shm
lrm                   410M  268K  409M   1% /lib/modules/2.6.24-23-powerpc/volatile
/dev/hda5              13G  830M   11G   8% /home
is what is returned when I use the command. Do you see something resembling this when you run the command?

---

### Post by metzy85 on 2009-02-16
Ok i got that output but what do i do now. How does that fix the Kernal update issue

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.5G  2.7G  713M  79% /
tmpfs                1009M     0 1009M   0% /lib/init/rw
varrun               1009M  108K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M  2.8M 1006M   1% /dev
tmpfs                1009M  136K 1008M   1% /dev/shm
/dev/sda5              35G  4.5G   31G  13% /host
lrm                  1009M  2.0M 1007M   1% /lib/modules/2.6.27-11-generic/volatile

---

