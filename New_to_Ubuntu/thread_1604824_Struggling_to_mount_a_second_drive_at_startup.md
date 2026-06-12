---
title: "Struggling to mount a second drive at startup"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Michael Deats on 2010-10-24
Hi all,

I've been using ubuntu for a while now (sort of off and on) but I've been having a lot more fun with it lately.

I'm using my 10.04 box now as a sort of server even though it's been loaded with the desktop edition.

Now I've added a second hard drive which was installed in my windows machine so it's NTFS.. I've read these two articles concerning auto mounting with fstab:

```
http://www.tuxfiles.org/linuxhelp/fstab.html
http://ubuntuforums.org/showthread.php?t=264626

```But I'm still getting an error :(

My error reads:

```
[mntent]: line 14 in /etc/fstab is bad
```This is what my /etc/fstab file looks like currently:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=10c381a9-5963-4760-ba89-41bc8bd20963 /               ext4    errors=remount -ro 0       1
# swap was on /dev/sda5 during installation
UUID=645ef74c-ee12-416f-8607-6504d6b0cb2e none            swap    sw               0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /media/500 gig2 ntfs    nls=utf8,umask=0222 0    0
```Line 14 where the error is is the one I added:
```
/dev/sda1       /media/500 gig2 ntfs    nls=utf8,umask=0222 0    0
```

Does anyone have any advice for me? :)

It would be highly appreciated!

Kind regards,

Michael

---

### Post by amauk on 2010-10-24
You have a space in the path name
also, try ntfs-3g, instead of just ntfs
```
/dev/sda1       /media/500_gig2 ntfs-3g    nls=utf8,umask=0222 0    0
```

---

### Post by Michael Deats on 2010-10-24
Now I'm getting:

```
fuse: failed to access mountpoint /media/500_gig2: No such file or directory
```Should I create a directory in /media/ called 500_gig2?

Edit: that seems to have worked! Creating the directory that is :)

---

### Post by amauk on 2010-10-24
> **Michael Deats said:**
> Should I create a directory in /media/ called 500_gig2?Yes

---

### Post by Michael Deats on 2010-10-24
> **amauk said:**
> Yes

Thank you so much for your help!

---

