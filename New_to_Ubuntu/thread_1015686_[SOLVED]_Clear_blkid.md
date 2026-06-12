---
title: "[SOLVED] Clear blkid"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by expatCM on 2008-12-19
I have just changed my system around a bit setting the os up on another drive.

The old drive was 500GB and partitioned into the os, swap and space for other things.  I have just deleted those partitions and formatted the full volume.

I commented out the old settings in fstab and rebooted.

Then I ran blkid to find the UUID for the new partition.  The output confuses me ....  the old partitions are still identified (sdc as below).

> /dev/sda1: UUID="7c8f5044-8715-47d4-9991-3f31172f8915" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="8278af53-15ba-4ba6-9093-49286012d988" 
/dev/sdb1: UUID="5da58b53-3947-43fc-9628-a4f6d5354afd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="40a2fda9-443a-46de-9b00-c695d6d4b372" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="a5e9b86e-ac97-4aa8-801b-798e7c079620" TYPE="swap" 
/dev/sdc3: UUID="ea718670-885a-46a7-96f5-2e681a85445b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 


How do I clear out the old UUID settings so that I can use a single reference for the now single partition?

---

### Post by Michael.Godawski on 2008-12-19
hey

try
```
sudo fdisk /dev/name
```

then press m for help
and I would suggest d for delete partition

Correct me if I am wrong :D

---

### Post by Elfy on 2008-12-19
I can't remember how to remove the old cache, but to get the updated UUID's try this

```
ls -la /dev/disk/by-uuid
```

---

### Post by Liviu-Theodor on 2008-12-19
> /dev/sda1: UUID="7c8f5044-8715-47d4-9991-3f31172f8915" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="8278af53-15ba-4ba6-9093-49286012d988" 
/dev/sdb1: UUID="5da58b53-3947-43fc-9628-a4f6d5354afd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="40a2fda9-443a-46de-9b00-c695d6d4b372" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="a5e9b86e-ac97-4aa8-801b-798e7c079620" TYPE="swap" 
/dev/sdc3: UUID="ea718670-885a-46a7-96f5-2e681a85445b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 

Honestly, I don't understand the last line either. But from the rest, I can think you have three SATA or SCSI hard-drives, with sda having two partitions, sdb one and sdc three. For both sda and sdc, the second partition is declared swap. Unfortunately, I don't know how to clear blkid, but for me it never happened like you described.

---

### Post by Elfy on 2008-12-19
What is confusing the op is that sdc2 and sdc3 have been deleted :)

---

### Post by expatCM on 2008-12-19
Thanks forestpixie ....  that command gave me a single UUID, dropped it into the fstab and the volume mounts .....

Now I wonder if I should have any concern about the cached entries .....  hope they do not come back to bite ....

---

### Post by Elfy on 2008-12-19
I obvioulsy didn't post my second post - man blkid suggests -g to remove old entires

```
blkid -g
```

---

### Post by expatCM on 2008-12-19
Perfect :)

needs to be run with sudo or changes are not made ...

---

