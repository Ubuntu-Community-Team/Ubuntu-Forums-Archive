---
title: "Usb hdd"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by gdeeble on 2011-03-15
So I have a USB hard drive that mounts and works fine, but every now and then it will unmount without, what seems like, any warning. I use this for my back up drive and have it set to do an incremental update, but the system doesn't realize the "EHD" is not connected and puts the back up right on my OS drive. Is there any way to create a shell script that will detect that the drive is connected and mount it to this place so that the system can't create a folder and put it on the OS drive? I'm using Zentyal for the server management which works wonderfully, except the external hard drive unmounts and remounts to a backup_ instead of backup.

Can anyone give any suggestions on their solutions? Thanks -Gary

---

### Post by sandyd on 2011-03-15
> **gdeeble said:**
> So I have a USB hard drive that mounts and works fine, but every now and then it will unmount without, what seems like, any warning. I use this for my back up drive and have it set to do an incremental update, but the system doesn't realize the "EHD" is not connected and puts the back up right on my OS drive. Is there any way to create a shell script that will detect that the drive is connected and mount it to this place so that the system can't create a folder and put it on the OS drive? I'm using Zentyal for the server management which works wonderfully, except the external hard drive unmounts and remounts to a backup_ instead of backup.

Can anyone give any suggestions on their solutions? Thanks -Gary
lets have some fun with this.

I guess a bash script will be sufficient.

mount -l lists mounted devices. However, partition names change. So, we use blkid instead.

so lets put it into action.
blkid will return something like this.

Find which one is your external disk. I don't have any USB ports left on my laptop, so I can't demonstrate it, just pretend /dev/sda1 is the drive. 
```

sandy@sandyd-laptop ~/Downloads $ sudo blkid
/dev/sda2: UUID="bcb2f8a7-ea68-429b-a3b2-e7356f31f1bb" TYPE="ext4" 
/dev/sda3: UUID="5ad0dd0c-59dc-416b-8c25-c0d6e9ca5b6a" TYPE="swap" 
/dev/sda1: UUID="bb4289c7-3b36-4cfd-a7b0-b904501fa770" UUID_SUB="f166c11a-56f2-4691-9f78-d85642d4c01b" TYPE="btrfs"

```We now know the UUID of the drive is "bb4289c7-3b36-4cfd-a7b0-b904501fa770" (ignore UUID_SUB, thats just because im using btrfs).

So, we find what the drive is listed as by using blkid, grep and awk. We then umount it
```

sudo blkid | grep bb4289c7-3b36-4cfd-a7b0-b904501fa770 > log
sudo umount $(awk -F':' '{ print $1 }' log) 

```We create a place for it to mount (do this only once)

```

sudo mkdir /mnt/disk

```and we mount it.
```

sudo mount $(awk -F':' '{ print $1 }' log) /mnt/disk
```Putting it all together.
```

sudo blkid | grep **your-uuid-here** > log
sudo umount $(awk -F':' '{ print $1 }' log) 
sudo mount $(awk -F':' '{ print $1 }' log) /mnt/disk

```

impressed? ;)

---

