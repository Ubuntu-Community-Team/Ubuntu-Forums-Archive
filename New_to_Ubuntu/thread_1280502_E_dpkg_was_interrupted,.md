---
title: "E: dpkg was interrupted,"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by mancroft on 2009-10-02
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Hi guys

Am getting the above error when starting synaptic.

Running sudo dpkg --configure -a gives:

dpkg: failed to open package info file `/var/lib/dpkg/updates/0013' for reading: Stale NFS file handle

I just rebooted and that did not help.

Help!

Cheers.

---

### Post by Paddy Landau on 2009-10-02
I'm not an expert in this. Have you tried opening Synaptic?
System > Administration > Synaptic Package Manager
If you can, then press (in order) the Reload button, Mark All Upgrades, and, if available, Apply.

Let us know whether that works.

---

### Post by mancroft on 2009-10-02
That is the error I get when I try to open synaptic.

---

### Post by wojox on 2009-10-02
May have to try a couple times in terminal:

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```


[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns)

---

### Post by mancroft on 2009-10-02
No luck, wojox:

> john@john-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/updates/0013' for reading: Stale NFS file handle
john@john-desktop:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/updates/0013' for reading: Stale NFS file handle
john@john-desktop:~$ sudo apt-get clean
john@john-desktop:~$ sudo apt-get clean
john@john-desktop:~$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
john@john-desktop:~$ 


---

### Post by sisco311 on 2009-10-02
nm

---

### Post by anaconda on 2009-10-02
I would be worried about the "stale nfs file handle" -warning.

You should propably run fsck on the drive, and then run the dpkg --configure -a

---

### Post by mancroft on 2009-10-02
> **anaconda said:**
> You should propably run fsck on the drive, and then run the dpkg --configure -a

I just ran then tried umount and that did not work.

How do I unmount it?

> john@john-desktop:~$ fsck
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
john@john-desktop:~$ 
john@john-desktop:~$ sudo umount /dev/sda1
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
john@john-desktop:~$ fuser -m /dev/sda1
/dev/sda1:            3802rce  3815rce  3877rce  3878rce  3884rce  3886rce  3897rce  3899rce  3906rce  3915rce  3921rce  3928rce  3929rce  3931rce  3937rce  3947rce  3950rce  3952rce  3954rce  3957rce  3958rce  3959rce  3960rce  3962rce  3965rce  3970rce  3972rce  3974rce  3977rce  3981rce  3989rce  4001rce  4003rce  4017rce  4037rce  4050rce  4054rce  5052rce  5184rce  5409rce  5411rce
john@john-desktop:~$ 


---

### Post by Paqman on 2009-10-02
You did the right thing cancelling that fsck. You'll need to boot up into a LiveCD and run it from there. The drive isn't mounted when you're running from the LiveCD.

---

### Post by mancroft on 2009-10-02
By "LiveCD", do you mean the installation CD?

---

### Post by sisco311 on 2009-10-02
Set the mount count to 30+ and the disk will be automatically checked on the next boot:

```
sudo tune2fs -C 40 /dev/sda1
```
```
sudo reboot
```

---

### Post by mancroft on 2009-10-02
> **sisco311 said:**
> Set the mount count to 30+ and the disk will be automatically checked on the next boot:

```
sudo tune2fs -C 40 /dev/sda1
```
```
sudo reboot
```

BRILLIANT, sisco311!

I did that, it corrected the errors then sudo dpkg --configure -a got synaptic working.

Much obliged.

---

