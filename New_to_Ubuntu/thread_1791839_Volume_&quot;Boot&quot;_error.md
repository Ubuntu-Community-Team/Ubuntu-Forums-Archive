---
title: "Volume &quot;Boot&quot; error"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by seanjuan on 2011-06-27
When trying to update my Ubuntu I received a error message saying [ THe volume"Boot" has only 10.1 MB disk space remaining.]. I'm not sure how to correct this error and have not seen it before. Any help to correct this will be appreciated.

---

### Post by yetiman64 on 2011-06-27
Do you use a separate /boot partition and do you have a lot of older kernels installed ?

---

### Post by seanjuan on 2011-06-27
No... There is no separate boot partition. I'm not sure is there are other kernels installed. Is there a way to check?

---

### Post by yetiman64 on 2011-06-27
Firstly please let us know what version of Ubuntu you are running, I'm doing this on the basis of a 10.04 install here.

Just as a double check of your partitioning could you please post the output of 
> cat /etc/fstab | grep boot if no boot partition is in use you will get no output. If so I may be on the wrong track and it leaves me a bit confused as a Boot volume is mentioned in the error.

Also to see what kernels you have use the code,

```
ls /boot | grep vmlinuz
``` When I run that code here I can see 5 results, you only need the latest kernel and one older one as a back up.

---

### Post by seanjuan on 2011-06-27
here are my results

Code 1:
cat /etc/fstab | grep boot

results:
# /boot was on /dev/sda5 during installation
UUID=e9fda353-f30d-404b-b13f-eb8e487e66f3 /boot           ext2    
relatime        0       2


Code 2:
ls /boot | grep vmlinuz

Results:
vmlinuz-2.6.32-22-generic
vmlinuz-2.6.32-22-generic-pae
vmlinuz-2.6.32-23-generic
vmlinuz-2.6.32-23-generic-pae
vmlinuz-2.6.32-24-generic
vmlinuz-2.6.32-24-generic-pae
vmlinuz-2.6.32-25-generic
vmlinuz-2.6.32-25-generic-pae
vmlinuz-2.6.32-26-generic
vmlinuz-2.6.32-26-generic-pae
vmlinuz-2.6.32-28-generic
vmlinuz-2.6.32-28-generic-pae
vmlinuz-2.6.32-30-generic
vmlinuz-2.6.32-30-generic-pae

---

### Post by bettaproger on 2011-06-27
had this problem myself, if your using the gnome desktop run the disk usage analyzer and see whats going on. FOr me it was sever log files had grown to 11GB and had occupied my entire / partition. deleted and all was well.

---

### Post by yetiman64 on 2011-06-27
> **seanjuan said:**
> here are my results

Code 1:
cat /etc/fstab | grep boot

results:
# /boot was on /dev/sda5 during installation
UUID=e9fda353-f30d-404b-b13f-eb8e487e66f3 /boot           ext2    
relatime        0       2


Code 2:
ls /boot | grep vmlinuz

Results:
vmlinuz-2.6.32-22-generic
vmlinuz-2.6.32-22-generic-pae
vmlinuz-2.6.32-23-generic
vmlinuz-2.6.32-23-generic-pae
vmlinuz-2.6.32-24-generic
vmlinuz-2.6.32-24-generic-pae
vmlinuz-2.6.32-25-generic
vmlinuz-2.6.32-25-generic-pae
vmlinuz-2.6.32-26-generic
vmlinuz-2.6.32-26-generic-pae
vmlinuz-2.6.32-28-generic
vmlinuz-2.6.32-28-generic-pae
vmlinuz-2.6.32-30-generic
vmlinuz-2.6.32-30-generic-paeThey are good results (what I was expecting)
You do have a separate boot partition (on /dev/sda5) and it is very full of old kernels.

You have both generic and generic-pae kernels available but in both if everything is working fine you only need to keep the 28 and 30 numbered kernels the rest are older and taking up space in /boot.

The next is a terminal command to remove the old kernels up to 2.6.32-26 (leaves the lastest two kernels -28 and -30)
```
sudo apt-get remove linux-image-2.6.32-22-generic* linux-image-2.6.32-23-generic* linux-image-2.6.32-24-generic* linux-image-2.6.32-25-generic* linux-image-2.6.32-26-generic*
``` the * indicates the removal of both the generic and generic-pae kernels (please check the list of kernels carefully in the terminal before accepting the list for removal) DO NOT remove the -28 or -30 kernels (including the pae variants), they are the two latest kernels on your install.

To clean up the related header packages (in case they aren't automatically removed in the above step) you can run,
```
sudo apt-get remove linux-headers-2.6.32-22 linux-headers-2.6.32-23 linux-headers-2.6.32-24 linux-headers-2.6.32-25 linux-headers-2.6.32-26 linux-headers-generic-2.6.32-22 linux-headers-generic-2.6.32-23 linux-headers-generic-2.6.32-24 linux-headers-generic-2.6.32-25 linux-headers-generic-2.6.32-26
```I'm not sure if the pae kernels have header packages specific to them or whether they use the generic ones as above. You could check in Synaptic for that if you wish, just be careful if you remove anything from in there.

After the commands have run their course re-run the command
```
ls /boot | grep vmlinuz
``` you should then see only 4 kernels (2 generic and 2 generic-pae) in there. This will free up the space the error you had earlier was complaining about.

Edit: after you update, check what kernels are installed again with the last bit of code above. I suspect the update is trying to install a new kernel (2.6.32-32) and if after a few days all is alright with the new kernel you may want to consider removing the 2.6.32-28 kernel like I have just shown you (alter the commands to suit that kernel version).

---

