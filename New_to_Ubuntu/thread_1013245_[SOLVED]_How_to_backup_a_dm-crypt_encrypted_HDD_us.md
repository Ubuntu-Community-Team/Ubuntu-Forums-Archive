---
title: "[SOLVED] How to backup a dm-crypt encrypted HDD using dd?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by janmartin on 2008-12-16
Hi all,

I am on Ubuntu 8.04.1 32 bit, installed using the Alternative Installer CD with the whole HDD encrypted using dm-crypt.
Works fine so far.

Now I got myself a USB HDD, created a Truecrypt Volume on it and like to backup the whole encrypted HDD, but WITHOUT dm-crypt encryption on top.

Before dm-crypt I simply backed up using dd:
dd if=/dev/sda1 of=/media/hda1/sda1backup.img

Mounting was like this:
sudo mount -loop /media/hda1/sda1backup.img /home/backup

However with dm-crypt now I am getting error messages:

Backup:
dd if=/dev/sda5 of=/media/truecrypt4/sda5.img

Failed mounting:
sudo mount /media/truecrypt4/sda5.img /home/backup
**mount: unknown filesystem type 'crypto_LUKS'**

Or:
Backup:
dd if=/dev/mapper/sda5_crypt of=/media/truecrypt4/sda5c.img

Failed mounting:
sudo mount /media/truecrypt4/sda5c.img /home/backup
**mount: unknown file system type 'LVM2_member'**

How the hell do I get the data out of the dm-crypt volume using dd? Btw.  inside the dm-crypt volume there is an ext3 file system anyway.

Simply copying files over doesn't do it, because there are either lots of rights-problems, or certain stuff like sock etc. cannot be copied at all.

Any Idea please?

P.S.:
Btw. I do not have a problem to access the HDD nor run Ubuntu.
When switching on the PC it prompts for the dm-crypt password first, which I enter, and the boots into Hardy Heron.

---

### Post by aurelieng on 2008-12-16
Your post is confusing, since you mention truecrypt, but have dm-crypt in the thread subject, and your partition is listed as crypto_LUKS, and both  clearly refers to LUKS.

If it is a LUKS filesystem, you can mount it from a loopback, with commands more or less liks this:
```

losetup /dev/loop0 /media/truecrypt4/sda5.img
cryptsetup luksOpen /dev/loop0 <mapperpoint> # Will prompt for password
mount /dev/mapper/<mapperpoint> /home/backup

```

---

### Post by janmartin on 2008-12-17
Hi,

well its like this:
dm-crypt for pre-boot encryption of the build-in HDD containing the OS.
Truecrypt for the external USB-HDD for backup.

I am not sure what <mountpoint> should be, but I am getting this error anyway:

sudo losetup /dev/loop0 /media/truecrypt4/sda5.img
[sudo] password for user: 
sudo cryptsetup luksOpen /dev/loop0 sda5
Enter LUKS passphrase: 
/dev/loop0 is not a LUKS partition
Command failed: No key available with this passphrase

Any idea?

Btw, I do not need to use the images i generated yesterday at all. 
Isn't there a way to backup the OS without LUKS and without dm-crypt, just the unencrypted pure data?
After all I am working with it right now, so it must be available anywhere, but where?

---

### Post by janmartin on 2008-12-17
Hi all,

just to report that I finally found the solution:

The dm-crypt encrypted volume is available transparently decrypted at /dev/mapper/me-root

So my backup worked like this:
sudo dd if=/dev/mapper/me-root of=/media/truecrypt4/me-root.img
227737600+0 records in
227737600+0 records out
116601651200 bytes (117 GB) copied, 5423 s, 21.5 MB/s

Testing:
sudo mount -o loop /media/truecrypt4/me-root.img /home/user/backup

unmount afterwards:
jan@me:~$ umount /home/user/backup

Have a good day!

---

