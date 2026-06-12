---
title: "Cannot get UUID from sdc2..?!"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by hopelessone on 2009-03-23
Hi,

sdc2 is a swap file at the end of the drive...and i can't get the UUID of it..??

I followed this tutorial: [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p4](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p4)

I Tried
> some@one:~$ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 260 2009-03-23 21:19 .
drwxr-xr-x 5 root root 100 2009-03-23 21:18 ..
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 06314d36-19f9-4d21-86fc-331c74d7c713 -> ../../sde1
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 073794d4-c95d-40c7-b7d4-6990e5636daa -> ../../sdd1
lrwxrwxrwx 1 root root  24 2009-03-23 21:19 0782aa5e-ee31-4c5a-8136-c2f0f3c343cf -> ../../mapper/hdd_1_crypt
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 1af537e5-f049-4130-bee5-c504ef7e2ebc -> ../../sdc3
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 3411509d-99d1-4ac5-9d25-22e0563d0946 -> ../../sdc4
lrwxrwxrwx 1 root root  23 2009-03-23 21:19 3b36502c-9ec9-46ac-9c16-d05a3d24e008 -> ../../mapper/sda3_crypt
lrwxrwxrwx 1 root root  23 2009-03-23 21:19 4dfb1180-0d7f-4f04-b67a-13a34de36712 -> ../../mapper/home_crypt
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 7c6b8506-f9e2-4fbf-a318-211f7eab4da0 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 e16ce70d-0098-4252-8122-400eb4b8cf59 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-03-23 21:18 e73f0332-8bfa-4446-8534-4f8c553298f1 -> ../../sdc1
lrwxrwxrwx 1 root root  24 2009-03-23 21:19 eb15c3ea-c598-4719-9c8b-fbd5cd10fc45 -> ../../mapper/hdd_2_crypt


and:
> some@one:~$ sudo vol_id --uuid /dev/sdc2
[sudo] password for some: 
/dev/sdc2: unknown volume type


How can i get it? all the others are there..

Thanks...

---

### Post by drs305 on 2009-03-23
You can also try "sudo blkid" but since your other commands didn't work this one may not either.

You could also open gparted and see if it finds your swap partition: System, Administration, Parition Editor; or "gksudo gparted".

---

### Post by hopelessone on 2009-03-23
Hi,

> some@one:~$ sudo blkid
[sudo] password for some: 
/dev/sda1: UUID="7c6b8506-f9e2-4fbf-a318-211f7eab4da0" TYPE="ext3" SEC_TYPE="ext2" 
/dev/mapper/sda3_crypt: UUID="3b36502c-9ec9-46ac-9c16-d05a3d24e008" TYPE="ext3" 
/dev/sdb1: UUID="e16ce70d-0098-4252-8122-400eb4b8cf59" TYPE="crypt_LUKS" 
/dev/sdc1: UUID="e73f0332-8bfa-4446-8534-4f8c553298f1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="073794d4-c95d-40c7-b7d4-6990e5636daa" TYPE="crypt_LUKS" 
/dev/sdc3: UUID="1af537e5-f049-4130-bee5-c504ef7e2ebc" TYPE="crypt_LUKS" 
/dev/sdc4: UUID="3411509d-99d1-4ac5-9d25-22e0563d0946" TYPE="crypt_LUKS" 
/dev/sde1: UUID="06314d36-19f9-4d21-86fc-331c74d7c713" TYPE="crypt_LUKS" 
/dev/mapper/home_crypt: UUID="4dfb1180-0d7f-4f04-b67a-13a34de36712" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/hdd_1_crypt: UUID="0782aa5e-ee31-4c5a-8136-c2f0f3c343cf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/hdd_2_crypt: UUID="eb15c3ea-c598-4719-9c8b-fbd5cd10fc45" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/hdd_3_crypt: UUID="d2788822-5432-49ca-bfd7-165f4b781742" TYPE="ext3"

Gparted shows it as an unknown filesystem same as all the rest..

iirc there is no filesystem on sdc2 but it creates it
crypttab> 
swap_crypt /dev/sdc2 /dev/urandom  swap

---

### Post by hopelessone on 2009-03-23
/dev/disk/by-id/ shows up

is it ok to use?

---

### Post by hopelessone on 2009-03-23
yes you can use it in /etc/fstab or /etc/crypttab...
> 
ls -al /dev/disk/by-uuid

UUID returns a Unique ID based on the file-system...No file-system No UUID

> ls -al /dev/disk/by-id
returns a Unique ID based on hard drives connected to the local system

i *think* thats the right info..;)

---

