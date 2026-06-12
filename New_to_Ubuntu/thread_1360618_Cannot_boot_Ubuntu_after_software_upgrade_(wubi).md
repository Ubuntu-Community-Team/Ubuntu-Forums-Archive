---
title: "Cannot boot Ubuntu after software upgrade (wubi)"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by itzco on 2009-12-21
I install the latest Ubuntu using wubi, unfortunately I didn't know I was not making a real partition, I used it without any problem for some weeks but yesterday it just stopped booting.

After some research I found that it might be associated with a grub update.

[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg166824.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg166824.html)

I tried a couple of times unsuccessfully to run those instructions.

I'm not interested in keeping this virtual disk install (too dangerous i'll move to a real partition) but I'd like to access it to move my important files out of it. I tried from windows but the file always shows empty (I think this is ext4)

If I backup and make a clean wubi install can I then mount the old virtual file root.disks?

Thanks

---

### Post by utrrrongeeb on 2009-12-21
Yes, but you can also mount the disk image from Ubuntu when installed to a partition. (That is, no need to make another Wubi install.)

There might be some Windows tools to view the files, but I haven't tested it with ext4 disk image files.

---

### Post by itzco on 2009-12-21
Yes you're right, just thought about another wubi to make it faster.

In a last try to boot linux I tried again:

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 
loop=/ubuntu/disks/root.disk 
initrd /boot/initrd.img-2.6.31-14-generic
boot

but I keep getting a file not found :(

Thanks for the answer and nope I don't think ext4 is supported yet, all the way to ext3 can be done

---

### Post by garvinrick4 on 2009-12-21
Go to Vista command line and type  "bcdedit" without quotes and see if the wubi
isntaller is in the boot menu. that will help in finding the problem.  

  	 	 	 	 	 	  Fix Wubi when will not boot  
 

 Describe your new note here.  
 Fix Wubi when will not boot  
 

 How can I access my Wubi install and repair my install if it won't boot?  
 

 Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk

---

### Post by itzco on 2009-12-22
Hi

I'm sorry I was too fast to click delete button on all wubi files so I suppose it makes no sense to fix it anymore. Here the results anyway, perhaps now I need to clean for the new install anyway 

> ?Go to Vista command line and type "bcdedit" without quotes and see if the wubi installer is in the boot menu. that will help in finding the problem. 

Fix Wubi when will not boot 

Describe your new note here. 
Results of bcdedit:

```

Real-mode Boot Sector
---------------------
identifier              {801f35e8-655a-11dc-8f4b-d66e0c947c00}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

```

Shall I remove this entry? How?


*----
Now I'm shrinking my drive from Windows to be able to create a partition where I can install Ubuntu and then mount the partition 

(I'll try your instructions for booting from Ubuntu cd tomorrow, I remove the cd reader from this computer to make it lighter :( )

I actually copied the root.disk to an external drive, is this ok? 

- Should I be able to run what you recommend me without changes?
- Can I mount the disk 1st using normal mount from menu instead?

(I will do this with latest Ubuntu)

> 
sudo mkdir /win 
sudo mount /dev/sda1 /win 


Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 


sudo mkdir /vdisk 
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk 


Thanks

---

### Post by joes7 on 2009-12-22
Why do people use wubi -___-. Try by downloading the ISO from Ubuntu.com and installing it from scratch.

---

### Post by HappyFeet on 2009-12-22
> **joes7 said:**
> Why do people use wubi -___-. Try by downloading the ISO from Ubuntu.com and installing it from scratch.

I guess people are "guarded". I know what you mean.

---

### Post by Mark Phelps on 2009-12-22
> **joes7 said:**
> Why do people use wubi -___-. Try by downloading the ISO from Ubuntu.com and installing it from scratch.

Because (1) many of them have invested a thousand or more $$ in their PC and don't want to risk damaging that in any way by messing around with partitioning, and (2) the Wubi info presents a very positive image of a risk-free way of installing and using Ubuntu.

---

### Post by itzco on 2009-12-23
Hi All,

After 2 days of suffering I was finally able to shrink my C:\ drive to make space for Ubuntu...

That's the reason we use Wubi! I thought it was doing this for me, finding space, shrinking, creating a partition and installing, I know I'm a dreamer...

Wubi makes you think it's all easy and you have ubuntu in 10 minutes running!

One question in the process:

After the wubi problem and finding out that it was a grub problem I'm let's say kind of scared...

A couple of questions:

1) Can this happen with a 'real' install? that I cannot boot my ubuntu? 
- I'm a developer so normally projects cannot wait for me playing around with my OS -

2) Knowing that this happen because a bad release of grub or something similar, shall I use grub or vista loader?

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

What's on the safest side?

Thanks!

---

### Post by itzco on 2009-12-23
After some days of suffering to shrink my vista, I was finally able to re-install Ubuntu and the mounting of the virtual drive worked just perfectly!

Thanks for the support!

Any recommendation on the safest boot style?

---

