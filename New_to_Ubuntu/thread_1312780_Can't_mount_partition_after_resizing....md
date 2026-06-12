---
title: "Can't mount partition after resizing..."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by akelsall on 2009-11-03
I had a somewhat small partition that was unused and decided I could use that space in the partition immediately after it (meaning the partition that was listed after it when viewing the partitions in gparted). So, I unmounted the small partition and deleted it, then unmounted the partition I wanted to grow and resized it with no problem. 

Now, when I boot, I get an error message saying "File system check failed.  A log is being saved to /var/log/fsck/checkfs". Here's the output of that log:

[INDENT]> 
Log of fsck -C3 -R -A -a 
Tue Nov  3 10:25:53 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Unable to resolve 'UUID=42263a90-7f66-4f68-8018-06d417c254d9'
fsck.ext3: Unable to resolve 'UUID=128cc547-52b5-469b-8305-770641a1f0a6'
FREE: clean, 11/9281536 files, 630544/37118174 blocks
dynamips: clean, 501/612000 files, 646957/2441872 blocks
email: clean, 20/306432 files, 173008/1220932 blocks
/dev/sda2: clean, 21846/1925120 files, 3071048/7679070 blocks (check in 4 mounts)
music has been mounted 10 times without being checked, check forced.
music: 3635/3055616 files (4.3% non-contiguous), 10253872/12207384 blocks
networking_PC: clean, 4468/2138112 files, 1137555/8544564 blocks
personal: clean, 4867/935424 files, 1203201/3785307 blocks
windows: clean, 55/1525920 files, 2567253/6102684 blocks (check after next mount)
work: clean, 6195/612000 files, 895911/2441872 blocks (check in 3 mounts)
fsck died with exit status 8
[/INDENT]

Here's a snapshot of gpartetd:

[[IMG]http://img18.imageshack.us/img18/263/gparted.th.png[/IMG]](http://img18.imageshack.us/i/gparted.png/)

As you can see, the logical volume is there, and there's data in it. But, Ubuntu won't mount it.

Here's the volume ID:

$ sudo vol_id /dev/sda12 | grep UUID
ID_FS_UUID=759c02e2-fdb4-46fe-a9c6-76163a086f69
ID_FS_UUID_ENC=759c02e2-fdb4-46fe-a9c6-76163a086f69

Any ideas why Ubuntu won't mount this partition now?

Thanks,

Andy

---

### Post by drs305 on 2009-11-03
Do you still have the old UUID(s) listed in fstab? It could be that fsck is looking for UUIDs that no longer exist. You can open /etc/fstab for editing with this command:
```

gksu gedit /etc/fstab

```

You will need to either delete the old partition listing and/or change it to reflect the new UUID/mountpoint.

If you aren't sure what to do, please post your fstab contents.

---

### Post by akelsall on 2009-11-03
drs305, Here's the output of my old fstab. As you can see, I "did" have my photos under /dev/sda14, but after resizing things, it's now under /dev/sda12. What needs to happen in order for Ubuntu to know that it's now under /dev/sda12 (and why didn't it detect this automatcially)?

Thanks, 
Andy
==============================================

> [INDENT]# / was on /dev/sda1 during installation
UUID=09a669e0-8237-4198-8f8b-bbe14472e43c /               ext3    relatime,errors=remount-ro 0       1
# /FREE1 was on /dev/sda11 during installation
UUID=42263a90-7f66-4f68-8018-06d417c254d9 /FREE1          ext3    relatime        0       2
# /FREE2 was on /dev/sda13 during installation
UUID=128cc547-52b5-469b-8305-770641a1f0a6 /FREE2          ext3    relatime        0       2
# /FREE3 was on /dev/sda15 during installation
UUID=3743f9ab-8c1d-49fc-854c-ce634697bdef /FREE3          ext3    relatime        0       2
# /dynamips was on /dev/sda8 during installation
UUID=fa7f3944-9ac0-480f-bd73-615fffd6377c /dynamips       ext3    relatime        0       2
# /email was on /dev/sda5 during installation
UUID=719ef6b3-c176-4752-b515-a74ab39d2369 /email          ext3    relatime        0       2
# /home was on /dev/sda2 during installation
UUID=596bd02b-720c-442a-b3ef-8612a6668dc5 /home           ext3    relatime        0       2
# /music was on /dev/sda7 during installation
UUID=74f01a2d-bdb6-4105-8430-96e9758ebd89 /music          ext3    relatime        0       2
# /networking was on /dev/sda12 during installation
UUID=81ac311f-066c-4e05-8e85-03ebbca2dc41 /networking     ext3    relatime        0       2
# /personal was on /dev/sda10 during installation
UUID=da905238-955f-4e8c-84af-c99d59b655c0 /personal       ext3    relatime        0       2
# /photos was on /dev/sda14 during installation
UUID=759c02e2-fdb4-46fe-a9c6-76163a086f69 /photos         ext3    relatime        0       2
# /windows was on /dev/sda6 during installation
UUID=15f34904-c066-486d-acbe-9567b57198c6 /windows        ext3    relatime        0       2
# /work was on /dev/sda9 during installation
UUID=61f5933c-6e36-43ae-8229-cbefde365b4b /work           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=b7100b63-1b9b-463d-a958-77d7ceaf9792 none            swap    sw              0       0
/dev/scd1 /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/INDENT]

---

### Post by drs305 on 2009-11-03
Backup your current fstab:
```
sudo cp /etc/fstab /etc/fstab.old
```

Run the following command to see your current UUIDs:


```
sudo blkid -c /dev/null
```

Your fstab still contains references to the following UUIDs, which is what it is complaining about:
42263a90-7f66-4f68-8018-06d417c254d9
128cc547-52b5-469b-8305-770641a1f0a6
> 
# /FREE1 was on /dev/sda11 during installation
UUID=42263a90-7f66-4f68-8018-06d417c254d9 /FREE1 ext3 relatime 0 2
# /FREE2 was on /dev/sda13 during installation
UUID=128cc547-52b5-469b-8305-770641a1f0a6 /FREE2 ext3 relatime 0 2


So these should be removed or commented out if the "blkid" doesn't include them.

Next, you mention sda12 but I don't see 12 listed in fstab. That doesn't necessarily mean anything because *comments cannot be considered accurate*. But looking at your fstab, I see an entry for "/photos". If that is really still your photos partition and you are sure it is sda12, change fstab from/to this:
From:
> 
# /photos was on /dev/sda14 during installation
UUID=759c02e2-fdb4-46fe-a9c6-76163a086f69 /photos ext3 relatime 0 2


> 
# /photos was on /dev/sda[COLOR="Red"]XX[/COLOR] during installation
/dev/sda12 /photos ext3 relatime 0 2


or better, replace the UUID with the real UUID for the photo partition.

Once you have saved the file, close out all your running apps and run these commands to see if everything in fstab is working:
```

sudo umount -a  # Disregard the busy/error messages.
sudo mount -a

```
If you run the second command and get no messages, it means everything mounted correctly.

---

### Post by akelsall on 2009-11-03
drs305, what I ended up doing was removing a duplicate UUID in fstab (related to partition /dev/sda15 which didn't exist any more). Then, I found that /dev/sda13 had the wrong UUID (going by the output of **sudo vol_id /dev/sda13**). So, I changed the UUID for /dev/sda13 in fstab to match the true UUID (from the vol_id command) and all works well now. 

Thanks for all your help!

Andy

---

