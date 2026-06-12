---
title: "[SOLVED] free space on mounted storage drive"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-17
How can I see what the free space is on a mounted storage drive from the cli? When I try: df sdb1 it only shows me the free space for sda1.

---

### Post by drs305 on 2008-12-17
This will give you the free space on all your devices:
```
df -h
```

If you aren't seeing sdb1 it may not be mounted. You can tell by running:
```

mount | grep "/dev/"

```

---

### Post by pshootr on 2008-12-17
> **drs305 said:**
> This will give you the free space on all your devices:
```
df -h
```

If you aren't seeing sdb1 it may not be mounted. You can tell by running:
```

mount

```

I mounted my storage drives on a directory called /mnt I guess may be tis was a mistake. I take it if I had mounted them on /dev then df -h would have worked. Should I mount these drives on /dev instead?

---

### Post by drs305 on 2008-12-17
> **pshootr said:**
> I mounted my storage drives on a directory called /mnt I guess may be tis was a mistake. I take it if I had mounted them on /dev then df -h would have worked. Should I mount these drives on /dev instead?

No, you don't want to do that. If you are referencing the "/dev/" in the command I suggested, it only filters the output of the command to lines containing "/dev/", making it easier to read.

Do you now get results from the 'df' command?  Did the 'mount' command show that sdb1 was mounted?

If you still aren't getting an entry for sdb1, you can run the following command to make sure the partition is even recognized, whether it is mounted or not:
```

sudo blkid

```

---

### Post by pshootr on 2008-12-17
> **drs305 said:**
> No, you don't want to do that. If you are referencing the "/dev/" in the command I suggested, it only filters the output of the command to lines containing "/dev/", making it easier to read.

I just did df -h without te /dev

---

### Post by pshootr on 2008-12-17
> **drs305 said:**
> No, you don't want to do that. If you are referencing the "/dev/" in the command I suggested, it only filters the output of the command to lines containing "/dev/", making it easier to read.

Do you now get results from the 'df' command?  Did the 'mount' command show that sdb1 was mounted?

If you still aren't getting an entry for sdb1, you can run the following command to make sure the partition is even recognized, whether it is mounted or not:
```

sudo blkid

```

/dev/sda1: UUID="77f2e095-20b5-44a1-9bdd-a6830cb8c3f0" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="ba12429d-218c-4f45-bb80-90594c29f597"
/dev/sdb1: UUID="ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a" SEC_TYPE="ext2" TYPE="ext3"

I wonder why only sdb1 and sdc1 show this at the end: " SEC_TYPE="ext2" TYPE="ext3"   instead of just TYPE="ext3"

Where does the " SEC_TYPE="ext2" come from?

---

### Post by drs305 on 2008-12-17
I take it you are still not able to see the size of sdb1. Since it shows up with 'blkid', the partition exists. It is probably not mounted. To mount the partition, use the following command. Change the red type to the actual mountpoint you created in /mnt:
```

sudo mount /dev/sdb1 /mnt/[COLOR="Red"]test[/COLOR] 

```

---

### Post by pshootr on 2008-12-17
> **drs305 said:**
> I take it you are still not able to see the size of sdb1. Since it shows up with 'blkid', the partition exists. It is probably not mounted. To mount the partition, use the following command. Change the red type to the actual mountpoint you created in /mnt:
```

sudo mount /dev/sdb1 /mnt/[COLOR="Red"]test[/COLOR] -t ntfs -o uid=1000

```

:confused: I can see inside sdb1 and even create files. Dosn't this mean it is mounted? What does the ntfs portion of that mount command do?

---

### Post by drs305 on 2008-12-17
Yes, it means it is mounted so the df command should work. 

The "  SEC_TYPE="ext2" TYPE="ext3"  " is the normal output.

The 'ntfs' was a cut/paste error since you have ext3 partitions. I've changed it.

---

### Post by pshootr on 2008-12-17
/dev/sda1: UUID="77f2e095-20b5-44a1-9bdd-a6830cb8c3f0" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="ba12429d-218c-4f45-bb80-90594c29f597"
/dev/sdb1: UUID="ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a" SEC_TYPE="ext2" TYPE="ext3"

I wonder why only sdb1 and sdc1 show this at the end: " SEC_TYPE="ext2" TYPE="ext3" instead of just TYPE="ext3"

Where does the " SEC_TYPE="ext2" come from? Could this be a problem?

---

### Post by Hospadar on 2008-12-17
> **pshootr said:**
> I mounted my storage drives on a directory called /mnt I guess may be tis was a mistake. I take it if I had mounted them on /dev then df -h would have worked. Should I mount these drives on /dev instead?

/dev is not for mounting, /dev holds the files that represent the device itself (i.e. before it gets mounted).  Generally in ubuntu things are mounted to /media

You should never really add anything to /dev, not that it would hurt, it's just linux convention.

---

### Post by pshootr on 2008-12-17
> **Hospadar said:**
> /dev is not for mounting, /dev holds the files that represent the device itself (i.e. before it gets mounted).  Generally in ubuntu things are mounted to /media

You should never really add anything to /dev, not that it would hurt, it's just linux convention.

ok, thanks for that info.

---

### Post by pshootr on 2008-12-17
> **pshootr said:**
> /dev/sda1: UUID="77f2e095-20b5-44a1-9bdd-a6830cb8c3f0" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="ba12429d-218c-4f45-bb80-90594c29f597"
/dev/sdb1: UUID="ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a" SEC_TYPE="ext2" TYPE="ext3"

I wonder why only sdb1 and sdc1 show this at the end: " SEC_TYPE="ext2" TYPE="ext3" instead of just TYPE="ext3"

Where does the " SEC_TYPE="ext2" come from? Could this be a problem?

Thanks for your help guys. I still wonder about the above.

---

