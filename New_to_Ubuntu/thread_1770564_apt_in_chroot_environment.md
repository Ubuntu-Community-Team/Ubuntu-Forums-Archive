---
title: "apt in chroot environment"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by fremantle on 2011-05-29
i set up a chroot environment where i am working with an ubuntu system, but i am not being able to work with apt. its showing network errors when i try to apt-get something. although in my real system its working fine. how can i enable apt-get in a chroot?

---

### Post by sisco311 on 2011-05-29
You have to copy or bind the resolv.conf file.

From outside the chroot environment:
```
sudo mount --bind /etc/resolv.conf /path/to/chroot/etc/resolv.conf
```

Here is the script I use start a chroot env.:
```
#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="/dev/disk/by-uuid/43388d8b-de97-4fb4-b4ba-2bd5085f590f"

# mount point of the new root partition
MOUNT="/mnt/oneiric"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf /var/run/"

# list of additional devices and their mount pont.
# device names must be separated by the mount point with a colon (:)
# e.g. /dev/sda2:/home 
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

# start chroot 
chroot $MOUNT sudo -i -u $UNAME


```

---

### Post by fremantle on 2011-05-29
what if i follow this?
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

but i fear its outdated

---

### Post by Joe of loath on 2011-05-29
You need to set a DNS server in /etc/resolv.conf. Run:
```
echo nameserver 8.8.8.8 >> /etc/resolv.conf
```

---

### Post by fremantle on 2011-05-29
> **Joe of loath said:**
> You need to set a DNS server in /etc/resolv.conf. Run:
```
echo nameserver 8.8.8.8 >> /etc/resolv.conf
```

alright im trying that

---

