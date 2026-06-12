---
title: "External HD I boot from renames itself regularly"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by kevin.bogle on 2010-07-04
I have Lucid installed on an external HD that I boot to from GRUB 2.

Problem I am experiencing is that the HD keeps renaming itself during boot from SDC1 -> SDB1 -> SDC2, causing a drop to busybox.  I then have to reboot, edit grub launcher and change the name of the external to the opposite of what it was. Once in Lucid, I sudo update-grub alas, next time I boot...I have the same issue.  

This is making my boot time jump from 55 -> 109 seconds and is very very frustrating.

I'm a little experienced with Lucid and would appreciate all assistance offered. 

TIA

---

### Post by cariboo on 2010-07-04
Try using UUID in grub, this way it doesn't matter what the device label is. To find the UUID type:

```
sudo blkid
```

The output should look something like this:

```
sudo blkid
/dev/sda1: UUID="cbdde71e-13ce-4445-8dad-964c1443ebd1" TYPE="ext4" 
/dev/sda3: UUID="178a305c-b7c5-4850-b4a4-0ef43ae6b92c" TYPE="ext4" 
```

Then use a boot line similar to this:

```
inux	/boot/vmlinuz-2.6.35-6-generic root=UUID=cbdde71e-13ce-4445-8dad-964c1443ebd1 ro   quiet splash
```

In grub.

---

### Post by kevin.bogle on 2010-07-04
Thanks for the reply.  I did as you suggested and tried 

```
sudo blkid
```The output looked like this:

```
sudo blkid
/dev/loop0: UUID="06949d3c-4ddb-43a3-b6da-8b163a29893a" TYPE="ext4" 
/dev/sda2: UUID="1AC81A64C81A3F07" TYPE="ntfs" 
/dev/sdb1: LABEL="Elements" UUID="8CC432DDC432C96A" TYPE="ntfs" 


```Elements is the name of the external drive, so I used a boot code like this:

```
**L**inux    /boot/vmlinuz-2.6.35-6-generic root=UUID=8CC432DDC432C96A ro   quiet splash
```In grub.[/QUOTE]

As you see, I added a 'L' to the beginning of the GRUB code (you had typed inux, I assumed it was a mistake.

During boot-up, I got an awful error message...really made me feel bad inside.

```
2.211016 Kernel Panic--Not synching.  Attempted to kill init!
```

So...what other information can I provide?

TIA

---

