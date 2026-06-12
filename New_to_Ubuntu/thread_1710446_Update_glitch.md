---
title: "Update glitch?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by CVGH on 2011-03-19
Hi,

Running 10.10 on USB stick.

Ran upgrade and got errors on what I think is a kernel update.
Now whenever I install or remove a package, this happens:


```

Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic 
Not updating initrd symbolic links since we are being updated/reinstalled  
(2.6.35-22.33 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(2.6.35-22.33 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-22-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-28-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-28-generic; however: 
  Package linux-image-2.6.35-28-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
SettNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
ing up libavidemux0 (1:2.5.3-0ubuntu3) ... 
Setting up avidemux-common (1:2.5.3-0ubuntu3) ... 
Setting up avidemux (1:2.5.3-0ubuntu3) ... 
update-alternatives: using /usr/bin/avidemux2_gtk to provide /usr/bin/avidemux (avidemux) in auto mode. 
Setting up libaudiofile0 (0.2.6-8ubuntu1) ... 
Setting up esound-common (0.2.41-7) ... 
Setting up libesd0 (0.2.41-7) ... 
Setting up avidemux-plugins-common (1:2.5.3-0ubuntu3) ... 
Setting up avidemux-plugins-gtk (1:2.5.3-0ubuntu3) ... 
Setting up esound-clients (0.2.41-7) ... 
Setting up lame (3.98.4-0ubuntu1) ... 
Setting up mjpegtools (1:1.9.0-0.5ubuntu3) ... 
Ignoring install-info called from maintainer script 
The package mjpegtools should be rebuilt with new debhelper to get trigger support 
Setting up twolame (0.3.12-1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-2.6.35-22-generic 
 linux-image-2.6.35-28-generic 
 linux-image-generic 
 linux-generic 
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-28-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic 
Not updating initrd symbolic links since we are being updated/reinstalled  
(2.6.35-22.33 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(2.6.35-22.33 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-22-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-28-generic; however: 
  Package linux-image-2.6.35-28-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured
```

How can I fix this?

Thanks!

---

### Post by andrewthomas on 2011-03-19
Try to reconfigure grub-pc
 
```
 
sudo dpkg --configure grub-pc

```
 
If that is works, then you can 
 
```
 
sudo dpkg --configure -a

```

---

### Post by fabricator4 on 2011-03-19
Open a terminal window and run the following:

```

sudo apt-get check && sudo apt-get update 

```

You might need to run it again if you get some errors.  If you get errors reading repositories check your software sources and and the server you are using. You should be using the recommended server for your country/location (ideally) but if you have trouble accessing it you can try some other servers.

Once you can run the above with no errors, run:

```

sudo apt-get upgrade

```

It should download and install everything including the dependencies you were missing.

Chris

---

### Post by CVGH on 2011-03-20
The problem must have something to do with running the OS
from a flash drive......



```
root@ubuntu:/home/ubuntu# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-28-generic; however:
  Package linux-image-2.6.35-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-28-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/ubuntu# 
```

---

### Post by andrewthomas on 2011-03-20
> **andrewthomas said:**
> Try to reconfigure grub-pc
 
```
 
sudo dpkg --configure grub-pc

```If that is works, then you can 
 
```
 
sudo dpkg --configure -a

```
Have you tried the above commands?

So far, you have only posted the output of apt-get update.

---

### Post by CVGH on 2011-03-21
:oops:

I will run them again tonight and see if I can cut and paste the right thing!!!

---

### Post by CVGH on 2011-03-22
```
ubuntu@ubuntu:~$ sudo dpkg --configure grub-pc
dpkg: error processing grub-pc (--configure):
 package grub-pc is already installed and configured
Errors were encountered while processing:
 grub-pc
``````
ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-28-generic; however:
  Package linux-image-2.6.35-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-28-generic
 linux-image-2.6.35-22-generic
 linux-image-generic
 linux-generic
```

---

### Post by An Sanct on 2011-03-22
AFAIK, live USBs are not supposed to be upgraded, since a part of them is "treated" as a CD, thus read only...

---

### Post by theozzlives on 2011-03-22
> **An Sanct said:**
> AFAIK, live USBs are not supposed to be upgraded, since a part of them is "treated" as a CD, thus read only...

I agree. You should run Ubuntu from your HDD if you're serious about it.

---

### Post by CVGH on 2011-03-22
In my OP, I stated that this was a USB install because I had a suspicion it might be
the problem..... 

So is there a way to stop this, any way to stop the kernal update?

Thanks!

---

### Post by perky on 2011-03-23
> **andrewthomas said:**
> Try to reconfigure grub-pc
 
```
 
sudo dpkg --configure grub-pc

```
 
If that is works, then you can 
 
```
 
sudo dpkg --configure -a

```

G'day

I'm getting the same errors:


```

$ sudo dpkg --configure grub-pc
dpkg: error processing grub-pc (--configure):
 package grub-pc is already installed and configured
Errors were encountered while processing:
 grub-pc

```

```

$ sudo apt-get check && sudo apt-get update && sudo apt-get upgrade

```
The output:
```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
[COLOR="Red"]/etc/grub.d/10_linux: 163: list: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2[/COLOR]
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
[COLOR="Red"]/etc/grub.d/10_linux: 163: list: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2[/COLOR]
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
 * dkms: running auto installation service for kernel 2.6.35-28-generic         
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
[COLOR="Red"]/etc/grub.d/10_linux: 163: list: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.[/COLOR]
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-28-generic; however:
  Package linux-image-2.6.35-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-24-generic
 linux-image-2.6.35-28-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Note that this is not a USB installation, but a propper installation on a hard disk drive.

The red bits look dodgy and might be able to help someone identify what's wrong.


Edit:
Here is the contents of /etc/grub.d/10_linux

[PHP]
#! /bin/sh
set -e
LINUX_KERNELS_DISPLAYED=2
COUNTER=0
# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=${prefix}/share/locale

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || uses_abstraction "${GRUB_DEVICE}" lvm; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  # Use ELILO's generic "efifb" when it's known to be available.
  # FIXME: We need an interface to select vesafb in case efifb can't be used.
  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[zx]-* /vmlinu[zx]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initramfs-${version}.img" \
	   "initrd.img-${alt_version}" "initrd-${alt_version}.img" \
	   "initrd-${alt_version}" "initramfs-${alt_version}.img"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`

  COUNTER=`expr $COUNTER + 1`
  if [ $COUNTER -eq $LINUX_KERNELS_DISPLAYED ]; then
   list =""
  fi
done
[/PHP]
Line 163 is the last line.

---

### Post by perky on 2011-03-23
It looks like the original post is different to my prob, the op's prob looks like this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/739027]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/739027")

No google results for mine.. perhaps I should file a bug on launchpad unless someone can see something obvious that I've missed?

---

### Post by An Sanct on 2011-03-23
> **CVGH said:**
> In my OP, I stated that this was a USB install because I had a suspicion it might be
the problem..... 

> Running 10.10 on USB stick.If you install from a Live CD (installation CD) or a Live USB it is the same. I personally always prefer to install from Live USB, its much faster - no spinning parts, etc. Also if you created the Live USB from an ISO file, you can be sure, that there are no errors (while CDs get scratched, badly burned, ...).

Have you tried:
1. update the grub entries
2. Open synaptic and recheck dependencies
3. sudo apt-get install -f

If yes, what where the results?

---

### Post by CVGH on 2011-03-23
> **An Sanct said:**
> 
Have you tried:
1. update the grub entries
2. Open synaptic and recheck dependencies
3. sudo apt-get install -f

1. Nope, not sure how actually...
2. Yes, said "successfully fixed dependencies problem"
3.
```

buntu@ubuntu:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-28-generic; however:
  Package linux-image-2.6.35-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                    Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-28-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ 
```

---

### Post by perky on 2011-03-23
> **CVGH said:**
> 1. Nope, not sure how actually...
2. Yes, said "successfully fixed dependencies problem"
3.


Could it be that the file system on your mem stick is ntfs/nfs?  See [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/739027") if so ("10.10 desktop is not detecting the NFS root of ym system for kernel 2.6.35-28 ").

Edit:  it seems that ntfs is different from nfs, but it might be somehow related(?)  The errors that show up in that bug look like the ones you are getting.

---

### Post by CVGH on 2011-03-24
The first partition[/cdrom] is FAT32 and the 2nd[/mount/casper-rw] is ext2.

---

### Post by An Sanct on 2011-03-25
Thats still sounds like a Live USB to me ... The problem is with the system files, that are on the squashFS file system (the virtual CD-ROM), they are read only (obviously) and with that, cannot be updated.

---

### Post by CVGH on 2011-03-25
That's what I think as well.
Any way to stop the OS from trying to update the kernel?
Every time I install a package, it tries to finish the kernel update and really slows the process down.....
I now see the boot partition is mounted as /rofs and the persistent partition as /cdrom.

---

### Post by CVGH on 2011-03-29
Gave up and reinstalled to USB. Updated but made sure not to select and Kernel updates...

---

### Post by TULIOESTRADA on 2011-04-19
What are you suppose to do when you get to the license agreement screen and says ok.  I hit enter and nothing happens.

Found the answer myself.  Hit tab and it highlights ok in red.  Hit enter and lets you continue. Next window gives you yes or no option, so hit yes and done although I got some errors.

Setting up linux-firmware (1.38.6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
E: Sub-process /usr/bin/dpkg returned an error code (1)

These were the only errors.  Everything else was ok.

---

