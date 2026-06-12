---
title: "removing apparmor"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by SSzretter on 2009-12-07
so I did a sudo apt-get remove apparmor* and also update-rc.d apparmor remove, and even deleted some directories that were related to apparmor, and I am still getting a message at boot :
 chroot: cannot execute /etc/apparmor/initramfs: No such file or directory

Where do I find this reference and get rid of it to eliminate the error?

---

### Post by iponeverything on 2009-12-07
try a 

```
sudo dpkg --purge apparmor
```

---

### Post by MelDJ on 2009-12-07
or uninstall it from synaptic

---

### Post by openuniverse on 2009-12-07
.

---

### Post by JamesParnell on 2009-12-07
i dont even know what it is....

---

### Post by SSzretter on 2009-12-07
Ok, this is frustrating - I almost have it working - I added apparmor=0 to my grub config, and blacklist apparmor to my blacklist.conf, and a couple times it worked - during boot it said it was blacklisted and did not load.    However it is back to trying to load again.

I have the same problem with some other modules, for example the ones that begin with 'snd', I want to get rid of that can cant....

Seems like there should be a simple way to do this...??

---

### Post by NHclimber on 2010-03-21
> **SSzretter said:**
> so I did a sudo apt-get remove apparmor* and also update-rc.d apparmor remove, and even deleted some directories that were related to apparmor, and I am still getting a message at boot :
 chroot: cannot execute /etc/apparmor/initramfs: No such file or directory

Where do I find this reference and get rid of it to eliminate the error?

It's because there's a script in your initrd image that is trying to 'chroot /etc/apparmor/initramfs'. The offender is /etc/initramfs-tools/scripts/init-bottom/_apparmor. To get rid of it, you have to know how to rebuild the Ubuntu kernel or edit an initrd image.

---

### Post by SSzretter on 2010-03-21
Thanks for replying, this became less of a priority, but it is good to know what it would take.

---

### Post by trevelyn on 2010-03-31
If you remove it, you need to update your initramfs.  I did this:

1. created custom kernel and got rid of apparmor (optional)

2. to remove it: ```
apt-get purge apparmor
``` 
3. to get rid of config folder: ```
rm -rf /etc/apparmor*
``` 
4. to not try to load removed apparmor script: ```
update-initramfs -u 
``` 

And it was all gone.  In your case, you may simply need to do the update-initramfs and that's it.  I'd recommend making backups before doing any of these steps!

~douglas

---

