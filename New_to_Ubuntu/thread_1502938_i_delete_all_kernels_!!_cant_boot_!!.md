---
title: "i delete all kernels !! cant boot !!"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by alz3abi on 2010-06-06
Hello, i delete all kernels by mistake  now i cant boot, 

i booted from Live cd. and tried how to fix this ..


Please Please help.. i have an exam tomorrow  !! i cant study without my system !!


thanks in advance

edit: problem solved, for more details please read this thread posts

---

### Post by elliotn on 2010-06-06
Hug thats the first, backup and reinstall

---

### Post by alz3abi on 2010-06-06
there is no way to install kernel from Live CD ?

my /boot  is in dev/sda6 and / on dev/sda2

---

### Post by wojox on 2010-06-06
Good, for Extra Credit you can write about why you shouldn't become root and delete stuff. :P

See here [Installing packages using the Ubuntu installation CD]("https://help.ubuntu.com/9.10/add-applications/C/offline.html")

---

### Post by Barrucadu on 2010-06-06
If you mount all of your HDD partitions you can chroot in and reinstall the kernel (or any package) that way:

```

mkdir /mnt/root
mount /dev/sda2 /mnt/root
mount /dev/sda6 /mnt/root/boot
mount --bind /dev /mnt/root/dev
mount --bind /proc /mnt/root/proc
mount --bind /sys /mnt/root/sys
chroot /mnt/root
apt-get install [whatever]

```

---

### Post by alz3abi on 2010-06-06
> **Barrucadu said:**
> If you mount all of your HDD partitions you can chroot in and reinstall the kernel (or any package) that way:

```

mkdir /mnt/root
mount /dev/sda2 /mnt/root
mount /dev/sda6 /mnt/root/boot
mount --bind /dev /mnt/root/dev
mount --bind /proc /mnt/root/proc
mount --bind /sys /mnt/root/sys
chroot /mnt/root
apt-get install [whatever]

```

```
root@ubuntu:/# apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-tools-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.32-22-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image linux-image-2.6.32-22-generic linux-image-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.9MB of archives.
After this operation, 97.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-image-2.6.32-22-generic linux-image-generic linux-image
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-22-generic 2.6.32-22.36
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/main linux-image-2.6.32-22-generic 2.6.32-22.36
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/main linux-image-generic 2.6.32.22.23
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/main linux-image 2.6.32.22.23
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-22-generic_2.6.32-22.36_i386.deb  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.22.23_i386.deb  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image_2.6.32.22.23_i386.deb  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# 
```

---

### Post by Barrucadu on 2010-06-06
Hmm, weird, never had networking fail in a chroot before. Download the debs and install them manually.

**edit:** aha! I guess you use DHCP, and so your /etc/resolv.conf file in the chroot is empty. If it is, just stick the entries for OpenDNS in there so you can resolve hostnames:

/etc/resolv.conf
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Or just download the debs manually, both should work.

---

### Post by sisco311 on 2010-06-06
> **Barrucadu said:**
> Hmm, weird, never had networking fail in a chroot before. Download the debs and install them manually.

**edit:** aha! I guess you use DHCP, and so your /etc/resolv.conf file in the chroot is empty. If it is, just stick the entries for OpenDNS in there so you can resolve hostnames:

/etc/resolv.conf
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Or just download the debs manually, both should work.

I usually just bind the resolv.conf file. e.g. ```
mount --bind /etc/resolv.conf /mnt/root/etc/resolv.conf
```

Here is the script I use to chroot into Ubuntu:
```
#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="/dev/sda1"

# mount point of the new root partition
MOUNT="/mnt/maverick"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf"

# list of additional devices and their mount pont. 
# device names must be separated by the mount point with a colon (:)
# e.g. /dev/sda2:/home or /dev/sda5:/boot
 
AMOUNT=""

# user name
UNAME="sisco"

############################################################################
# start the chroot environment                                             #
############################################################################

# add user to the list of allowed users to make connections to the X server.
sudo -u $USER xhost SI:localuser:$UNAME

# create the mount point & mount the root partition
mkdir -p $MOUNT
mount $ROOT $MOUNT

# mount the virtual filesystems & resolv.conf to enable the network
for i in $ARGS; do
  mount --bind /$i $MOUNT/$i
done 

# mount additional partitions:
for i in $AMOUNT; do
  mkdir -p ${MOUNT}${i//*:/}
  mount ${i//:*/} ${MOUNT}${i//*:/}
done

# chroot into the linux installation
chroot $MOUNT su - $UNAME 

```

---

### Post by alz3abi on 2010-06-06
@Barrucadu, thnaks alot !! 

@sisco311, thanks your script is very useful ;)

thnaks every body .. now every thing playing as well

---

### Post by RJ12 on 2010-06-06
Good luck on your exam!

---

### Post by sisco311 on 2010-06-06
> **alz3abi said:**
> @Barrucadu, thnaks alot !! 

@sisco311, thanks your script is very useful ;)

thnaks every body .. now every thing playing as well

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

Oh, and best of luck in your exam!

---

### Post by alz3abi on 2010-06-06
@RJ12, thanks

@sisco311, thanks, thread allready marked as SOLVED thanks

---

