---
title: "[SOLVED] /boot/ files won't change permissions"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by baruch60610 on 2008-12-21
I noticed that all the files in my /boot/ directory have world read/write/execute permissions set.  I was a bit surprised at this.  Checking other comptuers, I see that this is wrong - the permissions should be set more restrictively.

When I went to change the permissions, I found that they wouldn't change.  I could not restrict the permissions.  I tried chmod o-wx *, for example, both as regular user and as root.  As regular user, I got no error message at all - nothing happened.  As root, nothing happened either.  The files remained the same.  I also tried chmod 0700 *, also with no effect.

I am at a loss to explain this.  Am I missing something here?  I've tried this on other files owned by root.  When I try to chmod them as user, I get a permission error, as expected.  As root, the chmod works.  The only time it doesn't work, it seems, is when I try it on the /boot/ directory.  I would greatly appreciate any help with this.

Edit:  FWIW, I'm running Hardy Heron.

---

### Post by cdtech on 2008-12-21
Wow, that is strange. Could you post the list of files as such:
```
ls -al
```
and post in a code block. Please post your prompt along with it as well.

---

### Post by handydan918 on 2008-12-21
If you suffered a power interuption or something else that would cause an unclean shutdown, root may have been remounted read-only...

---

### Post by baruch60610 on 2008-12-21
```

baruch@ubuntu:/boot$ ls -al
total 49100
drwxrwxrwx  1 root root    4096 2008-12-20 22:59 .
drwxr-xr-x 22 root root    4096 2008-11-27 11:55 ..
-rwxrwxrwx  1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rwxrwxrwx  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rwxrwxrwx  1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rwxrwxrwx  1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rwxrwxrwx  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rwxrwxrwx  1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
drwxrwxrwx  1 root root       0 2008-11-27 11:55 grub
-rwxrwxrwx  1 root root 8183150 2008-11-10 21:33 initrd.img-2.6.24-19-generic
-rwxrwxrwx  1 root root 7922359 2008-11-22 23:28 initrd.img-2.6.24-21-generic
-rwxrwxrwx  1 root root 8179976 2008-11-10 21:38 initrd.img-2.6.24-21-generic.bak
-rwxrwxrwx  1 root root 7923383 2008-12-08 10:19 initrd.img-2.6.24-22-generic
-rwxrwxrwx  1 root root 7922247 2008-11-27 11:56 initrd.img-2.6.24-22-generic.bak
-rwxrwxrwx  1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rwxrwxrwx  1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rwxrwxrwx  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rwxrwxrwx  1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rwxrwxrwx  1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rwxrwxrwx  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rwxrwxrwx  1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic
baruch@ubuntu:/boot$ chmod o-w abi-2.6.24-19-generic
baruch@ubuntu:/boot$
baruch@ubuntu:/boot$ ls -al
total 49100
drwxrwxrwx  1 root root    4096 2008-12-20 22:59 .
drwxr-xr-x 22 root root    4096 2008-11-27 11:55 ..
-rwxrwxrwx  1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rwxrwxrwx  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rwxrwxrwx  1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rwxrwxrwx  1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rwxrwxrwx  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rwxrwxrwx  1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
drwxrwxrwx  1 root root       0 2008-11-27 11:55 grub
-rwxrwxrwx  1 root root 8183150 2008-11-10 21:33 initrd.img-2.6.24-19-generic
-rwxrwxrwx  1 root root 7922359 2008-11-22 23:28 initrd.img-2.6.24-21-generic
-rwxrwxrwx  1 root root 8179976 2008-11-10 21:38 initrd.img-2.6.24-21-generic.bak
-rwxrwxrwx  1 root root 7923383 2008-12-08 10:19 initrd.img-2.6.24-22-generic
-rwxrwxrwx  1 root root 7922247 2008-11-27 11:56 initrd.img-2.6.24-22-generic.bak
-rwxrwxrwx  1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rwxrwxrwx  1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rwxrwxrwx  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rwxrwxrwx  1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rwxrwxrwx  1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rwxrwxrwx  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rwxrwxrwx  1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic
baruch@ubuntu:/boot$                                                  

```What is driving me nuts is, I've got three other servers connected to this computer, all of which are behaving themselves.  It's just this computer.

---

### Post by baruch60610 on 2008-12-21
```
baruch@ubuntu:/boot$ ls -al
total 49100
drwxrwxrwx  1 root root    4096 2008-12-20 22:59 .
drwxr-xr-x 22 root root    4096 2008-11-27 11:55 ..
-rwxrwxrwx  1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rwxrwxrwx  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rwxrwxrwx  1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rwxrwxrwx  1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rwxrwxrwx  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rwxrwxrwx  1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
drwxrwxrwx  1 root root       0 2008-11-27 11:55 grub
-rwxrwxrwx  1 root root 8183150 2008-11-10 21:33 initrd.img-2.6.24-19-generic
-rwxrwxrwx  1 root root 7922359 2008-11-22 23:28 initrd.img-2.6.24-21-generic
-rwxrwxrwx  1 root root 8179976 2008-11-10 21:38 initrd.img-2.6.24-21-generic.bak
-rwxrwxrwx  1 root root 7923383 2008-12-08 10:19 initrd.img-2.6.24-22-generic
-rwxrwxrwx  1 root root 7922247 2008-11-27 11:56 initrd.img-2.6.24-22-generic.bak
-rwxrwxrwx  1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rwxrwxrwx  1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rwxrwxrwx  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rwxrwxrwx  1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rwxrwxrwx  1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rwxrwxrwx  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rwxrwxrwx  1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic
baruch@ubuntu:/boot$ sudo chmod o-w abi-2.6.24-19-generic
[sudo] password for baruch:
baruch@ubuntu:/boot$
baruch@ubuntu:/boot$ ls -al
total 49100
drwxrwxrwx  1 root root    4096 2008-12-20 22:59 .
drwxr-xr-x 22 root root    4096 2008-11-27 11:55 ..
-rwxrwxrwx  1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rwxrwxrwx  1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rwxrwxrwx  1 root root  422838 2008-11-24 16:47 abi-2.6.24-22-generic
-rwxrwxrwx  1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rwxrwxrwx  1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
-rwxrwxrwx  1 root root   80062 2008-11-24 16:47 config-2.6.24-22-generic
drwxrwxrwx  1 root root       0 2008-11-27 11:55 grub
-rwxrwxrwx  1 root root 8183150 2008-11-10 21:33 initrd.img-2.6.24-19-generic
-rwxrwxrwx  1 root root 7922359 2008-11-22 23:28 initrd.img-2.6.24-21-generic
-rwxrwxrwx  1 root root 8179976 2008-11-10 21:38 initrd.img-2.6.24-21-generic.bak
-rwxrwxrwx  1 root root 7923383 2008-12-08 10:19 initrd.img-2.6.24-22-generic
-rwxrwxrwx  1 root root 7922247 2008-11-27 11:56 initrd.img-2.6.24-22-generic.bak
-rwxrwxrwx  1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rwxrwxrwx  1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rwxrwxrwx  1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rwxrwxrwx  1 root root  905617 2008-11-24 16:47 System.map-2.6.24-22-generic
-rwxrwxrwx  1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rwxrwxrwx  1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic
-rwxrwxrwx  1 root root 1921176 2008-11-24 16:47 vmlinuz-2.6.24-22-generic
baruch@ubuntu:/boot$                                        
```OK, forgot to do this as 'root', so here's the same results.  Notice that when I did this as user, I didn't get an error message?

---

### Post by baruch60610 on 2008-12-21
Root as read-only?  I don't understand.  I haven't had any power interruption or other sudden failure.  Everything else seems to be working well enough.  Do you mean that the boot directory is read-only?  It's not, because I already removed a file from it (as user - that's what alerted me in the first place, that I didn't get an error when I forgot to sudo first).

If that's not it, then I don't understand what you were explaining.

---

### Post by cdtech on 2008-12-21
Let me see your "/etc/fstab" file:
```
cat /etc/fstab
```

**UPDATE::.**
Have you tried to switch to "root" user:
```
sudo su
```

---

### Post by baruch60610 on 2008-12-21
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
``````
baruch@ubuntu:/boot$ su
Password:
root@ubuntu:/boot# chmod o-w abi-2.6.24-19-generic
root@ubuntu:/boot# ll
total 49092
-rwxrwxrwx 1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic

```I am wondering what the significance of the fstab file is... is that the file that gets used when 'mount' is invoked?

---

### Post by gTinker on 2008-12-21
[QUOTE=baruch60610]I am wondering what the significance of the fstab file is... is that the file that gets used when 'mount' is invoked?[/QUOTE]

It is the file that gets parsed (read) at boot and then all filesystems that are "auto" are mounted. Likewise, when you use the, mount -a, command.

You might try changing the permissions on the /boot folder itself and see if that helps.

[edit] ...and you'll probably want to figure out how things got into the state they are in so that you can avoid it in the future, this is not something the filesystem would do on its own.

---

### Post by caljohnsmith on 2008-12-21
I think the issue might be that you are using Wubi, and thus your /boot folder is actually a mounted partition from your Kubuntu root.disk image. I'm not familiar enough with Wubi to know, but it might be that having those type of permissions idiosyncrasies is normal. How about trying:
```
cd /
sudo umount /boot
sudo mount /host/ubuntu/disks/boot /boot
sudo chmod /boot/chmod o-w abi-2.6.24-19-generic
ls -l /boot
```
If the mount command does not work, try:
```
sudo mount -w --bind /host/ubuntu/disks/boot /boot
```
Please post the output of the above commands.

---

### Post by baruch60610 on 2008-12-21
@caljohnsmith, I think you've hit it on the head.  I *am* using Wubi, a fact I often forget because I almost never use Windows.  It makes sense that the "file system" would look a little strange where it edges onto the NTFS system it lives on.  All the other computers I connect to use plain old Linux without Wubi.  When the one computer acted differently, I was worried - but like you said, it's probably because this one alone has Wubi on it.

The commands you suggested make me uneasy - I seem to have problems when I mount/umount things.  Since the "problem" looks like it's not really a problem, I think I'll just leave well enough alone for now.

Thank you, though, for your help.  I was getting very frustrated - and pretty worried - about why this was behaving strangely.

---

