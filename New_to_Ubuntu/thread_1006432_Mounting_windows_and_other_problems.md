---
title: "Mounting windows and other problems"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by cocodave on 2008-12-09
Hello all.

I have just installed Ubuntu through Wubi, so I am currently duel booting windows aswell.

My first question is how do I 'mount' windows. I followed some instructions I read elsewhere, and managed to mount my windows recovery drive which is of no use to me. I cannot repeat this method for my actual windows drive, as ubuntu does not seem to be able to see it. 

Secondly, I am unable to remove the mounted recovery drive. When i try it gives a message saying: I am unprivileged to unmount the device, and only the root user can do it. I have attempted to change my user rights, but to no affect. How do I remove it?

Thirdly, my host name is 'Daves ubuntu'. Every time I use the terminal I get the message 'sudo: unable to resolve host Daves ubuntu'. I do not know if this is affecting anything, but how can i 'resolve' myself. I read somewhere it may be because i have a space in my host name, but I do not know how to change this.

Thankyou for your help.
David

---

### Post by taurus on 2008-12-09
1.  Post the output of this command from a terminal
```
sudo fdisk -l
```

2.  Unmount it from a terminal using sudo for root privilege.
```
sudo umount /dev/XXXX
```
Replace the XXXX with a device name.
```
df -h
```

3.  Make sure the name in /etc/hosts and /etc/hostname are the same.
```
cat /etc/hosts
cat /etc/hostname
```

---

### Post by cocodave on 2008-12-09
Sorry to post so soon after, but coincidently, whilst trying out F-spot i noticed my windows drive named 'host' in the import list. Do I mount it, or access it as I would any other folder? 

All my other problems remain though.
Thankyou

---

### Post by cocodave on 2008-12-09
1/ david@Daves ubuntu:~$ sudo fdisk -l
sudo: unable to resolve host Daves ubuntu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2              15        1320    10485760    7  HPFS/NTFS
/dev/sda3   *        1320       14594   106620928    7  HPFS/NTFS

2/ My drive is named 'RECOVERY'
david@Daves ubuntu:~$ sudo umount /dev/RECOVERY
sudo: unable to resolve host Daves ubuntu
umount: /dev/RECOVERY: not found

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      6.0G  3.5G  2.3G  61% /
tmpfs                 941M     0  941M   0% /lib/init/rw
varrun                941M  336K  941M   1% /var/run
varlock               941M     0  941M   0% /var/lock
udev                  941M  2.8M  939M   1% /dev
tmpfs                 941M   24K  941M   1% /dev/shm
/dev/sda3             102G  100G  2.7G  98% /host
lrm                   941M  2.4M  939M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2              10G  9.0G  1.1G  90% /media/RECOVERY


3/ david@Daves ubuntu:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Daves_ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

david@Daves ubuntu:~$ cat /etc/hostname
Daves ubuntu

I believe I changed this myself in a naive way to self fix the problem. Again thankyou.

---

