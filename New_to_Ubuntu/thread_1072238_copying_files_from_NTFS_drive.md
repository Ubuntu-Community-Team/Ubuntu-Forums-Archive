---
title: "copying files from NTFS drive"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by dragon_reborn on 2009-02-17
Hi, I have made the plunge. I removed Windows from my homeserver and installed mythbuntu. However my planning was a bit lax. I have some movies on one of my internal drives which is a NTFS type. How can I copy them (the movies) off before I re-format it to a Linux readable format? (I have space available on a FAt32 partition.)

---

### Post by albandy on 2009-02-17
Linux can read and write NTFS partitions

Look at Places for your NTFS drive

---

### Post by dragon_reborn on 2009-02-17
Hi, thanks for that..I am an absolute Newbie..are you talking about Places with in my Linux folders? I am using the Mythbuntu 8.10 distro

---

### Post by JohnLM_the_Ghost on 2009-02-17
Yeah should be there somewhere... I dunno mythbuntu really
Anyways, you can always use (regular) Ubuntu LiveCD, if you have one.

---

### Post by albandy on 2009-02-17
Ok, in Intrepid there is a desktop menu named as places, and you're hard disk should be there.

if not you can do this:
Assuming windows is in your first hard disk and first partition type this:

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1 -o uid=yourusername

now you've your windows partition mountet in /mnt/sda1

---

### Post by egalvan on 2009-02-17
> **dragon_reborn said:**
> I removed Windows from my homeserver and installed mythbuntu. However my planning was a bit lax. I have some movies on one of my internal drives which is a NTFS type. **How can I copy them (the movies) off before I re-format it to a Linux readable format?** (I have space available on a FAt32 partition.)

NTFS is a Linux-readable format, with full read/write support.

You may need to install ntfs-3g (found in the repos)

---

### Post by SamNSane on 2009-02-17
> **dragon_reborn said:**
> Hi, I have made the plunge. I removed Windows from my homeserver and installed mythbuntu. However my planning was a bit lax. I have some movies on one of my internal drives which is a NTFS type. How can I copy them (the movies) off before I re-format it to a Linux readable format? (I have space available on a FAt32 partition.)

You probably won't have to install any additional packages to be able to read ntfs since recent Ubuntu versions have the ability already installed by default. You might even just leave that drive as ntfs if you don't feel like changing it, though read and write performance will probably suffer as a result.

But using a FAT32 partition as a target to copy movies to may be a problem. There's a maximum file size limit of 4 gigs for FAT32. If any of your movies is bigger than that, you won't be able to copy them to FAT32.

---

### Post by Metallion on 2009-02-17
Exactly ntfs is readable by default since Gutsy. The drive will mostly be in one subdirectory of /media/

Otherwise do as albandy says. It could be that you have to replace sda1 by something else though. sda1 means the first partition on your first hard drive. sda2 would be the second partition on your first hard drive while sdb1 would be the frst partition of the second hard drive. sdc4 in turn would be the 4th partition of the 3rd hard drive. Does this make any sence or am I confusing you?

---

### Post by JohnLM_the_Ghost on 2009-02-17
> **Metallion said:**
> Exactly ntfs is readable by default since Gutsy. The drive will mostly be in one subdirectory of /media/

It is at least since Dapper...

---

### Post by Metallion on 2009-02-17
> **JohnLM_the_Ghost said:**
> It is at least since Dapper...

You're right... Let me rephrase that: readable and writable. I remember that I still had to install ntfs-3g myself for write support in Feitsy.

---

### Post by dragon_reborn on 2009-02-17
beautiful!  I followed Albandy's advise and it works, thanks guys. I am really starting to enjoy Linux

---

### Post by dragon_reborn on 2009-02-17
I have a new challenge, I get this when I try to mount the drive:

root@homeserver:/mnt# mount /dev/sdd1 /mnt/sdd1 -o uid=andre
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
 any advise?

---

### Post by JohnLM_the_Ghost on 2009-02-17
You should do as it says... assuming you still have windows...
If not you can try forcing mount with -f option... AT YOUR OWN RISK of course...

---

### Post by jerome1232 on 2009-02-17
Sounds like the file system isn't consistent. I would really try and repair it before forceing a mount. (if it was just the log file not being clean it's not so bad)

If you don't have Windows you can also try ntfsfix, it has very limited capabilities in repairing ntfs drives though, chckdsk would be much better.

To get ntfsfix install ntfsprogs

[apt://ntfsprogs]("apt://ntfsprogs")

Then run

```
sudo ntfsfix /dev/sdd1
```

---

### Post by dragon_reborn on 2009-02-18
Thanks, I tried it but no joy, it seems I will have to reinstall the dreaded windows to fix this drive.

---

### Post by JohnLM_the_Ghost on 2009-02-18
> **dragon_reborn said:**
> Thanks, I tried it but no joy, it seems I will have to reinstall the dreaded windows to fix this drive.
I think chkdsk from Windows' CD repair console will also do the trick!

---

