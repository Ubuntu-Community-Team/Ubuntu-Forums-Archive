---
title: "Dual Booting Ubuntu 10.04 LTS and Snow Leopard Grub Issues"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by rgordy on 2011-01-06
I installed with a live cd, and partitioned the HD manually.  I created a 2151mb under swap area, and a 46xxxmb ext4.  On the last step, I click advanced to select where to install the bootloader, but it will not let me install it in the 46xxxmb partition.  I chose to continue without installing it, and am looking for a way to get it from terminal.  Any suggestions?

thanks

---

### Post by TechWiz2100 on 2011-01-06
Real Mac or Hackintosh?

Real Mac:
You can you bootcamp for bootloader instead and it may or may not be easier since you have to chain os x to grub

Hackintosh:
Use Chameleon for the same reason as above

---

### Post by rgordy on 2011-01-06
It is a real mac. I'm not sure what you mean by use bootcamp, I did a few searches for it but came up with nothing.

---

### Post by TechWiz2100 on 2011-01-06
Apple Boot Camp, the thing that Apple created to boot Windows from OS X

Heres a link
[http://ubuntuforums.org/showthread.php?t=678542]("http://ubuntuforums.org/showthread.php?t=678542")

---

### Post by rgordy on 2011-01-06
I don't think I described my problem well previously, so here is what is wrong. 

I used boot camp in snow leopard to create a partition for ubuntu.  I then booted from the live cd, opened gparted and deleted said partition.  After clicking on the install button, I went through the prompts until I reached the partition editing section.

*I first tried clicking "use largest continuous space" and had the same problem in the end.

I click manually partition.

I first create a swap space of 2151mb, this becomes /dev/sda3.  I then create a 46xxxmb ext4 (also tried ext3) partition mounted as " / ".   This becomes /dev/sda4.

On the last screen, I select advanced to change where the bootloader is installed.  

It is my understanding that the bootloader must go in the same partition as the ubuntu install ( in my case this would be /dev/sda4 )

However, when I select /dev/sda4 I cannot click " OK ".

I also tried changing the order in which I partition, ie the ext4 before the swap area but nothing has worked.

---

### Post by TechWiz2100 on 2011-01-07
> **rgordy said:**
> I don't think I described my problem well previously, so here is what is wrong. 

I used boot camp in snow leopard to create a partition for ubuntu.  I then booted from the live cd, opened gparted and deleted said partition.  After clicking on the install button, I went through the prompts until I reached the partition editing section.

*I first tried clicking "use largest continuous space" and had the same problem in the end.

I click manually partition.

I first create a swap space of 2151mb, this becomes /dev/sda3.  I then create a 46xxxmb ext4 (also tried ext3) partition mounted as " / ".   This becomes /dev/sda4.

On the last screen, I select advanced to change where the bootloader is installed.  

It is my understanding that the bootloader must go in the same partition as the ubuntu install ( in my case this would be /dev/sda4 )

However, when I select /dev/sda4 I cannot click " OK ".

I also tried changing the order in which I partition, ie the ext4 before the swap area but nothing has worked.

I think SWAP has to be in an extended partition. Just try making 1 large ext4 partition in the empty space and select that partition. I'm pretty sure Ubuntu will repartition the space to include the SWAP.

---

### Post by rgordy on 2011-01-08
Thanks for all the help. I ended up fixing it by using gparted to format the partitions prior to starting the installer. I think it has to d with grub2 not wanting to use logical partitions

---

