---
title: "Validate fulldisk encryption"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by X181 on 2009-05-21
Hello...

I have installed ubuntu 9.04 with VLM and disk encryption (dm-crypt). Everything works fine and fast :p.

'dmsetup status' displays linear for two partitions and crypt only for one partition.

Q: But how can i verify that the hole drive (except the boot-loader-partition) is encrypted?

Thanks in advance

Additional informations:
user@nb123:~$ sudo dmsetup status
nb123-swap_1: 0 12754944 linear 
sda1_crypt: 0 312076571 crypt 
nb123-root: 0 299319296 linear 

user@nb123:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/nb123-root
                     147311096   2344172 137483944   2% /
tmpfs                  1547976         0   1547976   0% /lib/init/rw
varrun                 1547976       104   1547872   1% /var/run
varlock                1547976         0   1547976   0% /var/lock
udev                   1547976       172   1547804   1% /dev
tmpfs                  1547976       484   1547492   1% /dev/shm
lrm                    1547976      2392   1545584   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5               233335     13949    206938   7% /boot

---

### Post by scorp123 on 2009-05-21
> **X181 said:**
> how can i verify that the hole drive (except the boot-loader-partition) is encrypted?

Thanks in advance

Additional informations:
user@nb123:~$ sudo dmsetup status
nb123-swap_1: 0 12754944 linear 
**[COLOR="Red"]sda1_crypt: 0 312076571 crypt [/COLOR]**
nb123-root: 0 299319296 linear  According to the output you gave everything is encrypted. "sda1_crypt" is the container that holds all your logical volumes.

If you really really want to be sure: Just boot any Linux Live CD and then try to access the hard drives .... You should only see /boot. Accessing the rest should either fail or --in the case of newer Linux distros-- cause a password dialogue to pop up. Without knowing the password it should therefore be impossible to access the hard drive.

---

### Post by X181 on 2009-05-22
Everything fine. Nothing visible except boot-partition.

Thx

---

