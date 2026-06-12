---
title: "&quot;according to mtab............&quot;"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by vanzan on 2009-05-31
I installed Ubuntu to a usb drive last night and all worked great. However I've just noticed that I cannot access the primary partition of my ntfs hard drive. I can access the D drive which has windows recovery software but can't mount the c drive which has windows vista. Here's the error message I get:

"mount: according to mtab /dev/sda3 is already mounted on /media/os"

Where "os" is the c partition of the hard drive.

Now I've gone into /media/ and theres nothing there. I've also open mtab in gedit and found a media/os reference but I'm not knowledgeable enough to interpret the results.

I've run a search and this problem has popped up a few times without resolution. Can anyone help? Thanks

---

### Post by expelledboy on 2009-06-01
Go to a terminal and become the root user
```
sudo su -
```
as when it comes to mounts I have sometimes not been able to see it as a normal user. Then..
```
cd /media/os
```

If the directory exists then..
```
umount
```

Finally edit your /etc/fstab and remove any line that contains */media/os* and replace it with this;
```
/dev/sda3 /media/os      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

```

If you want to use the UUID you can find it with;
```
blkid
```
find the sda3 UUID and replace the *"/dev/sda3"* with *"UUID=*******-****-****-****-************"* in the fstab entry ..obviously replace with  the UUID you found :rolleyes:

---

### Post by petermacuser on 2009-11-16
Ok, but what if /media/os doesn't exist?
I have the same issue, just mine dir is called /media/disk ...it's not there, what's next?
Can I unmount and how to do this using UUID?

BTW I was able to mount this device elsewhere from the same USB stick, what's wrong?

Thanks

---

