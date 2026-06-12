---
title: "compiz visual effects extra"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by whalescreams on 2009-08-25
having all sorts of problems... now when i go to choose extra under visual effects it gives me the option of installing a driver for nvidia.... I do that and get the message

unable to write mmap-msync  (28 no space left on device) e: the package lists or status file could not be parsed or opened

and now when i go to add/remove it says 

Failed to Check for Installed and available applications

this is a major failure of your software management system. please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with 'sudo apt-get update' and 'sudo apt-get install -f'

and when i do that i get the same response as earlier.. unable to write mmap-msync..........

---

### Post by inobe on 2009-08-25
open synaptic package manager and click edit, click fix broken packages.

---

### Post by inobe on 2009-08-25
wait, your root partition may be full.

```
df -h
sudo fdisk -l
```

run that in terminal and copy and paste the output

you should see

```
blah@disk-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             110G  2.7G  102G   3% /
tmpfs                 119M     0  119M   0% /lib/init/rw
varrun                119M  104K  119M   1% /var/run
varlock               119M     0  119M   0% /var/lock
udev                  119M  148K  119M   1% /dev
tmpfs                 119M   84K  119M   1% /dev/shm
lrm                   119M  2.2M  117M   2% /lib/modules/2.6.28-15-generic/volatile
blah@disk-laptop:~$ sudo fdisk -l
[sudo] password for disk: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86a886a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14505   116511381   83  Linux
/dev/sda2           14506       14593      706860    5  Extended
/dev/sda5           14506       14593      706828+  82  Linux swap / Solaris

```

this will clean some packages from synaptic

```
sudo apt-get clean
```

this will search for large files in /

```
sudo find / -type f -size +100000k
```

---

### Post by whalescreams on 2009-08-28
i ended up installing kubuntu and set the partition correctly... everything is fine now.. thanks for the help

---

