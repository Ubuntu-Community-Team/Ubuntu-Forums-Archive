---
title: "Stuck with update error"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by zeasar on 2009-02-18
Hi guys, I ran update manager and was trying to install the updates. Then a error msg appears 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then entered

> sudo dpkg --configure -a

into the terminal and then this error report appears

> Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-23-generic (2.6.24-23.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-generic
dpkg: subprocess post-installation script returned error exit status 1


I have not even used 10% of my total HD space so I dont know what the "no space left on device" is referring to.

Please help as Im unable to update anything as long as this error persists.:(

---

### Post by avtolle on 2009-02-18
From the command line (terminal accessed from Applications>Accessories>Terminal)do```
df -h
```and post result here.

---

### Post by philinux on 2009-02-18
> **avtolle said:**
> From the command line (terminal accessed from Applications>Accessories>Terminal)do```
df -h
```and post result here.

+1. His root partition must be full.

---

### Post by avtolle on 2009-02-18
> **philinux said:**
> +1. His root partition must be full.
Yes, or he created a boot partition, and it's full (or almost).

---

### Post by drs305 on 2009-02-18
Often the "no space" error message is due to the user having a separate (and very small) /boot partition. If you have a separate /boot, check and see how much space remains. If it is almost full, the short-term solution is to remove some of the older kernels to make room for the new ones. The long-term solution is to make the partition larger.

If you don't have a separate /boot partition, it is possible your system partition has become full - usually with undeleted trash, a very small hard drive, or a backup that was mistakenly made onto the system partition instead of a backup device.

Run the following to check your mounted partition usage:
```
df -h
sudo du / -h --max-depth=1

```

---

### Post by avtolle on 2009-02-18
Thought of another scenario, which is related to the partition full; if the OP installed via Wubi, his virtual disk (for lack of a better term) might also be full or nearly full in the root partition. If this is so, the fix will be a bit more complex than if installation was on a separate partition.

---

### Post by zeasar on 2009-02-18
thanks for the reply, and it does look as though my /boot is full

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              27G  3.5G   23G  14% /
varrun                379M  104K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   92K  379M   1% /dev
devshm                379M   12K  379M   1% /dev/shm
lrm                   379M   39M  340M  11% /lib/modules/2.6.24-23-generic/volatile
/dev/sda5              99M   94M     0 100% /boot


how can I safely remove old un-needed stuffs while not accidentally deleting vital files?

---

### Post by avtolle on 2009-02-18
Try going to Synaptic (System>Administration>Synaptic Package Manager) to see if, in the left column, there is a section entitled Installed (Local or Obsolete). If there is, click on it and take a look at what is reported. If there are lines beginning with linux..., these are obsolete kernel versions, mark for complete removal, then select apply.

---

### Post by drs305 on 2009-02-18
> **zeasar said:**
> thanks for the reply, and it does look as though my /boot is full
how can I safely remove old un-needed stuffs while not accidentally deleting vital files?

Check for the kernel you are currently using:
```

uname -r

```
Will return something like: *2.6.27-11-generic*

Open synaptic and type in "2.6.27" (based on the return above).
You should see listings for linux-image..., linux-headers...,, and linux-retricted-modules...

You can safely remove the files with a lower number than the one returned above.

Example:
*uname -r* returns 2.6.27-11-generic

You can remove:
linux-image-2.6.27-5-generic
linux-headers-2.6.27-5-generic
linux-restricted-modules-2.6.27-5-generic
linux-image-2.6.27-7-generic
linux-headers-2.6.27-7-generic
linux-restricted-modules-2.6.27-7-generic

Many users prefer to keep at least one older kernel on their machine in case problems develop with the current kernel.

---

### Post by zeasar on 2009-02-18
Again thanks for the help.

But now the same error occurs when I try to run synaptic package manager.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Anyway to break this dead cycle of error?

---

### Post by avtolle on 2009-02-18
You need to rerun[sudo dpkg --configure -a[/code]to complete the kernel installation. Good luck.

---

### Post by zeasar on 2009-02-18
running that command would just return with a "no space left.." error.

So how else can I clean up my /boot without synaptic package manager?

edit: i managed to go into terminal and used some old school windows command like cd and dir

now im in /boot and i can see some old versions packages, what command do i use to delete the old files?

edit 2: rite, google told me its rm, gona give it a try

---

### Post by drs305 on 2009-02-18
You use "sudo rm" but be very careful because if you run it on the wrong kernels you can break your system and there is no undelete. Good luck!

---

### Post by zeasar on 2009-02-18
Finally broke that error cycle by sudo rm each and every one of those old files that's taking up spaces. :D

now my system is updating again happily

thanks everyone for the support ;)

---

