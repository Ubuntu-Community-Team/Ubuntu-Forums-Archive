---
title: "cannot write to my usb flash disk"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Franz01 on 2009-05-05
Just installed ubuntu... and I tried to copy some files to a USB flash disk. It is **FAT32**

I could not because ubuntu sees the disk as read-only. 
this is the message:
```

Error opening file '/media/FLASH_8G/cat': Read-only file system

```
I** understood that FAT32 was read and write. Is that true?**

Then I tried to change the permissions but I could not. 
If I right click + properties I see "the permissions ... could not be determined"
If I open the disk and go to the File Browser button (in the upper part of the form) I can see the properties, but Permissions for the owner has file access="---" If I try to change to "read and write" the system does not apply the changes.

After reading other posts in this forum, I tried the USB disk with Windows. I could read and write.
Then I extracted it properly with the "safely remove your hardware" icon.

I tried it with ubuntu again: nothing. I cannot write. As before.

What do I miss?

---

### Post by bluefrog on 2009-05-05
is there a lock button on the usb key?

---

### Post by Franz01 on 2009-05-05
> **bluefrog said:**
> is there a lock button on the usb key? 
No lock button. 
I can write if I use it with WinXp.
I cannot if I use it with ubuntu.

---

### Post by kay-man on 2009-05-05
You may have mounted the stick as root, where only root has read-write access. Try running

ls -l /media

and post the results

---

### Post by Franz01 on 2009-05-05
> **paulklos said:**
>  Try running
ls -l /media


yes, I have some lines like (I am connected with anoter PC, I cannot copy and paste):
```

drwxr-xr-x 2 root root 4896 ..... cdrom0
drwx------ 19 francesco root 8192 ... FLASH_8

```
My usb disk is FLASH_8

what am I supposed to do in order to have it writable? And which is the error I did?

---

### Post by kirsis on 2009-05-05
Try setting the permissions of the FLASH_8 folder with chmod. I don't remember the exact syntax or the proper mode numbers, but something like ...

```

sudo chmod 777 /media/FLASH_8

```

should work, I think.

---

### Post by kpkeerthi on 2009-05-05
> drwx------ 19 francesco root 8192 ... FLASH_8

User francesco has drwx, which means you have read, write and execute permission on the directory (d) FLASH_8. Very strange that you are unable to copy files to it.

---

### Post by roger_1960 on 2009-05-05
Hi

Try, in windows, making the USB stick a shared folder before removing it.  Then try again in Ubuntu.

Also, is there any security software on the USB stick which needs to be configured?

---

### Post by Franz01 on 2009-05-05
> **kpkeerthi said:**
> User francesco has drwx, which means you have read, write and execute permission on the directory (d) FLASH_8. Very strange that you are unable to copy files to it.

Now I am really confused.

here is the copy and paste of ls -l /media

```

francesco@ubuntu:~$ ls -l /media
total 12
lrwxrwxrwx  1 root      root    6 2009-05-04 06:31 cdrom -> cdrom0
drwxr-xr-x  2 root      root 4096 2009-05-04 06:31 cdrom0
drwx------ 19 francesco root 8192 1969-12-31 19:00 FLASH_8G

```

Then I played a little... and I unmounted the disk. When I inserted  it back again, I saw all the files and folders in the disk with a small lock on them....

If I try to change mode:

```

francesco@ubuntu:~$ chmod -v 777 /media/FLASH_8G
chmod: changing permissions of `/media/FLASH_8G': Read-only file system
failed to change mode of `/media/FLASH_8G' to 0777 (rwxrwxrwx)

```

but file system is FAT32.

I attach the screen shot of  the permissions form.
thank you for your suggestion.

---

### Post by Franz01 on 2009-05-05
> **roger_1960 said:**
> Hi

Try, in windows, making the USB stick a shared folder before removing it.  Then try again in Ubuntu.

Also, is there any security software on the USB stick which needs to be configured?
I tried but it is the same, I see it read only in ubuntu.... and no security s/w on the usb stick.

---

### Post by kay-man on 2009-05-05
It looks like the drive is mounted read-only. I don't know off the top of my head how to change the mount options for these drives that are mounted automatically.

Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=262332") will help you.

Alternatively, you can unmount it and then manually mount it again with different options that will allow read-write access.

---

### Post by kay-man on 2009-05-05
come to think of it, can you post the output of

```
cat /etc/mtab
```

That will show exactly how the drive has been mounted

---

### Post by Franz01 on 2009-05-05
> **paulklos said:**
> come to think of it, can you post the output of

```
cat /etc/mtab
```

That will show exactly how the drive has been mounted

thank you for your time. In the meantime I reformatted it. Now it works!

---

