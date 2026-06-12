---
title: "fstab error"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by wgwwm34 on 2011-01-05
I mounted a network drive using fstab and I can access it fine except now I get an fstab error on startup. I was wondering if anyone could check my fstab out for me and let me know if they see anything obnoxiously out of place:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d705806e-fc71-4c27-ae59-999a90c157e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0e69ac7c-2196-43ee-afb5-10207bf37952 none            swap    sw              0       0
//curtis.lawrence.edu/campus_share/ /media/Campus_Share cifs credentials=/home/will/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

The error I am getting is: ```
 [mntent]: line 1 in /etc/fstab is bad

```

---

### Post by stoogiebuncho on 2011-01-05
What is the fstab error that you are getting?

---

### Post by wgwwm34 on 2011-01-05
The error I'm getting on boot and when I mount this is:


[mntent]: line 1 in /etc/fstab is bad


When I boot it offers me the option to skip mounting in order to continue booting, which I do. Despite the error the network share I'm connecting to connects fine.

---

### Post by matt_symes on 2011-01-05
Hi

```
proc /proc proc nodev,noexec,nosuid 0 0
```

Comment out this line by putting a # at the start.

```
#proc /proc proc nodev,noexec,nosuid 0 0
```

Kind regards

---

### Post by wgwwm34 on 2011-01-05
Unfortunately ```
 #proc /proc proc nodev,noexec,nosuid 0 0 
``` didn't work.

---

### Post by coffee412 on 2011-01-05
> **wgwwm34 said:**
> Unfortunately ```
 #proc /proc proc nodev,noexec,nosuid 0 0 
``` didn't work.

Hi, Just running thru the new posts.

Check your line 1. That would be your first line wouldnt it?

Perhaps your UUID changed on the drive? Thats worth looking at. But its your first UUID entry that fstab is bailing on.

---

### Post by sandyd on 2011-01-05
> **wgwwm34 said:**
> I mounted a network drive using fstab and I can access it fine except now I get an fstab error on startup. I was wondering if anyone could check my fstab out for me and let me know if they see anything obnoxiously out of place:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d705806e-fc71-4c27-ae59-999a90c157e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0e69ac7c-2196-43ee-afb5-10207bf37952 none            swap    sw              0       0
**//**curtis.lawrence.edu/campus_share/ /media/Campus_Share cifs credentials=/home/will/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
dump the two begining slashes

should look like
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d705806e-fc71-4c27-ae59-999a90c157e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0e69ac7c-2196-43ee-afb5-10207bf37952 none            swap    sw              0       0
curtis.lawrence.edu/campus_share/ /media/Campus_Share cifs  credentials=/home/will/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0

```
instead

---

### Post by wgwwm34 on 2011-01-05
My UUID's are correct and the two slashes are needed to mount the drive. It didn't mount without them and I still got the same error.

I also updated all the information up top in case I changed anything in this process.

---

### Post by coffee412 on 2011-01-05
> **wgwwm34 said:**
> My UUID's are correct and the two slashes are needed to mount the drive. It didn't mount without them and I still got the same error.

I also updated all the information up top in case I changed anything in this process.

Ok, Got a bit of an idea here. First, Backup your fstab file like so:

cp /etc/fstab /etc/fstab.bak

Now, Go in and remove every line that starts with #. These are suppose to be comment lines. 

Now save the file and reboot. In the error message note which line is bad.

---

### Post by wgwwm34 on 2011-01-05
Oddly enough, deleting all the comment lines eliminated the problem. They mount without error now. I don't see anything in the way that would make those lines look like anything but comments. Oh well, Thanks!

---

### Post by coffee412 on 2011-01-05
> **wgwwm34 said:**
> Oddly enough, deleting all the comment lines eliminated the problem. They mount without error now. I don't see anything in the way that would make those lines look like anything but comments. Oh well, Thanks!


I might be entirely wrong but if one is missing a space after the # sign then it might have had a problem with it.

?

But hey, Your run'in now! :p

---

