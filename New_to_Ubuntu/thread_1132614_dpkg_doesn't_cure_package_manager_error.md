---
title: "dpkg doesn't cure package manager error"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by ucalagon on 2009-04-22
:confused:  Dear Experts - can't break out of this loop!  Load Synaptics package manager, get error message 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 
I run dpkg command as above as superuser in root terminal and get lengthy feedback including...
gzip: stdout: No space left on device 
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic 
Failed to create initrd image. 
dpkg: error processing linux-image-2.6.27-14-generic (--configure): 
 subprocess post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.27-14-generic; however: 
  Package linux-image-2.6.27-14-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 

Can post entire report if required!  
ubuntu is on 80% of 500GB HDD and is definitely not filling entire space.  When viewed with Disk Usage analyzer, shows 13%, 65.6 GB used.
All help very welcome - what am I doing wrong?  

Roger

---

### Post by lisati on 2009-04-22
Did you remember to use "sudo"? as in ```
sudo dpkg --configure -a
```

---

### Post by Peter09 on 2009-04-22
The part of the error message which says

> gzip: stdout: No space left on device 

Is the problem, your disk is full.

---

### Post by Peter09 on 2009-04-22
To follow this up, it does not have to be the complete disk, jus a partition.

Do
```
df -h
```
and post the output, if you are unsure.

---

### Post by ucalagon on 2009-04-22
> **lisati said:**
> Did you remember to use "sudo"? as in ```
sudo dpkg --configure -a
```
Thanks to both for quick replies.  Yes Did run sudo... after first booting as "generic/recovery" both tries show prob with gzip "no space" despite using only 13% of 500GB?! Curioser and curiouser!!

---

### Post by ucalagon on 2009-04-22
> **Peter09 said:**
> To follow this up, it does not have to be the complete disk, jus a partition.

Do
```
df -h
```
and post the output, if you are unsure.

Thanks  - here's output...
root@ubuntu:/home/roger# sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       27G  5.2G   21G  21% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  252K  1.7G   1% /dev/shm
/dev/sdb1              29G   29G  5.1M 100% /host
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sdb5             421G  3.0G  397G   1% /media/disk

---

### Post by Peter09 on 2009-04-22
You need to do df -h as my post above.

---

### Post by Peter09 on 2009-04-22
Sorry for duplicate post-

this one...

/dev/sdb1 29G 29G 5.1M 100% /host

is full.

---

### Post by ucalagon on 2009-04-22
> **Peter09 said:**
> Sorry for duplicate post-
this one...
/dev/sdb1 29G 29G 5.1M 100% /host
is full.
Thanks Peter - had to give up yesterday - system came to complete lockup after steadily slowing down!
Does this mean I need to alter this partition, delete some files or reformat and start over?!
I have the ubuntu 8.04 CD.

:confused: Roger

---

### Post by barney385 on 2009-04-23
Same thing happened to me today.

I wish I had this advice:

 				 				**Re: Synaptic Package Manager** 			
 			 			 		   		 		 		**sudo apt-get clean ; sudo apt-get autoremove**

install and use Bleachbit

From JuanCarlosPaco

---

### Post by ucalagon on 2009-04-23
Thanks barney but still in the loop! I if I run "clean/autoremove" I get error message to run dpkg which then fails! If I try and D/L bleachbit, I get error to only run one download package at a time

---

### Post by Peter09 on 2009-04-23
Make sure that your trash is empty and delete any files that you do not need. You need to make enough space in the partition for the system to work. 

In the long term you need to understand what is filling your disk. It could be the number of old kernels you have?

---

### Post by nicholls15 on 2009-04-24
Hi folks 

I'm getting the same error ,

paul@lapuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              23G  4.3G   18G  20% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  304K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  152K  249M   1% /dev
tmpfs                 249M   84K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2              46M   41M  2.4M  95% /boot
/dev/sda4             206G   49G  146G  26% /home
paul@lapuntu:~$ sudo dpkg --configure -a
[sudo] password for paul: 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-restricted-modules-2.6.28-11-generic (2.6.28-11.15) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1
paul@lapuntu:~$ 


I know the boot partition is nearly full , but that can't be causing it ??

Any Ideas

---

### Post by nicholls15 on 2009-04-24
Sorry Folks 

Silly me it is the boot partition , any way of clearing that up ???:lolflag:

---

### Post by Peter09 on 2009-04-25
Try going into synaptic and removing any old kernels and headers, just leave the two latest kernels. Be careful....

---

### Post by ucalagon on 2009-04-25
Dpkg failure
After 6/7 hours of trying I gave up, reformatted Side D:  and installed 8.04 from CD on whole of Side D: 
Thank to all for help.  Now on Hardy Heron - fine but no sound with video!!

Roger ;-((

---

### Post by ucalagon on 2009-04-26
After another 6 hours, I gave up and re-formatted Side D:, re-installed 8.04 using whole of D:  Hardy Heron up and running but now back to no sound on video as before!! ;-(

---

