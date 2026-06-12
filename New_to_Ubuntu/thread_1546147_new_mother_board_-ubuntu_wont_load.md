---
title: "new mother board -ubuntu wont load"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by TimEnid on 2010-08-04
i just replaced my motherboard and when i boot it up, after grub, the ubuntu splash screen shows up and then i get:

> ALERT! /dev/disk/by-uuid/8e4ba2bb-1881-4629-bca4-d9881ce75b5c does not exits. Dr opping to a shell

busybox v.1.13.3 (ubuntu 1
;1.13.3-1ubuntu11) built-in shell (ash)
enter help for a list of built-in commands.
(intitramfs)

also, i am unable to boot from cd.

can someone help?

---

### Post by TimEnid on 2010-08-04
got the live cd to run. thats a step.

my main hd with ubunto on it is not showing up in disk utitlity.

---

### Post by oldsoundguy on 2010-08-04
try a repair boot out of grub.  See if that does it.

---

### Post by TimEnid on 2010-08-04
but my main hd is not showing up, so i cant choose where to install it.

---

### Post by TimEnid on 2010-08-04
when i type in sudo grub, i get command not found.

---

### Post by TimEnid on 2010-08-04
after typing in sudo apt-get install grub2
i get:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-pc
E: Package grub2 has no installation candidate


---

### Post by nerdy_kid on 2010-08-04
had a similar issue before, try booting off of the cd and updating grup.  or try booting from an older kernal.

---

### Post by Zzl1xndd on 2010-08-04
Silly question, but did you ensure that all connections to the drive are hooked up?

---

### Post by 23dornot23d on 2010-08-05
My thoughts too ..... the cable to the hard drive and the power cable to the hard drive ....
check that they are located properly ...... 

How many drives do you have ?

and (does/do) the (drive / s) spin up ...... ?

Something maybe one drive or a USB must be working to get this line -  
/dev/disk/by-uuid/8e4ba2bb-1881-4629-bca4-d9881ce75b5c does not exist.
as it is generated from the GRUB2 boot ,,


Then check in the BIOS ,,,,, to see that drives are recognized ......
*have you added a second hard drive too ... ?

(How did you get the CD working what was the problem there ... was that the cable or have you altered jumper settings)

---

### Post by theozzlives on 2010-08-05
I agree, check the BIOS. If your machine can't find the drives, Ubuntu won't. Really sounds like hardware and not software.

---

### Post by elliotn on 2010-08-05
I agree too, check if the bios detects the drive, if it doesnt play around with the power cable and if its IDE play around with the jumpers

---

### Post by mastablasta on 2010-08-05
even if it's not IDE jumpers might need to be set propperly (especially if there is a new slave drive...)

---

### Post by cascade9 on 2010-08-05
There are no master/slave jumpers for SATA. There are jumper settings, but they are normally things like SSC (spread spectrum clocking) OPT (limit the SATA type), etc..

---

### Post by TimEnid on 2010-08-05
figured out the problem. i had my master boot drive plugged into a 6gb sata port using a 6gb cable, problem is, the drive is not 6gb, its 3gb. All is working now. Thanks for the responses.

---

### Post by cascade9 on 2010-08-05
> **TimEnid said:**
> figured out the problem. i had my master boot drive plugged into a 6gb sata port using a 6gb cable, problem is, the drive is not 6gb, its 3gb. All is working now. Thanks for the responses.

Actually, a SATAII (3Gbit/sec) HDD should have no problems running on a SATAIII (6Gbit/sec) port. 

The problem would be the SATAIII controller, its probably some crap jbmicron RAID controller.

---

### Post by LowSky on 2010-08-05
When you switch out a motherboard and dont connect the drives to the same port numbers you are going to have issues like these.

---

### Post by TimEnid on 2010-08-05
> **cascade9 said:**
> Actually, a SATAII (3Gbit/sec) HDD should have no problems running on a SATAIII (6Gbit/sec) port. 

The problem would be the SATAIII controller, its probably some crap jbmicron RAID controller.

so a 3gbps hd can work on a 6gbps port?

im not familiar with the jbmiron raid controller subject, the motherboard is Asus p6x58d
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131614](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131614)

how can i go about correcting this problem?

if i connect something to a 6gb (an internal 1tb hd) port, its not even visible in ubuntu.

---

### Post by TimEnid on 2010-08-05
> **LowSky said:**
> When you switch out a motherboard and dont connect the drives to the same port numbers you are going to have issues like these.
thanks. i wasnt aware of that. so i cant switch my ports? is there something i have to do prior to switching them?

---

### Post by cascade9 on 2010-08-05
> **TimEnid said:**
> so a 3gbps hd can work on a 6gbps port?

im not familiar with the jbmiron raid controller subject, the motherboard is Asus p6x58d
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131614](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131614)

how can i go about correcting this problem?

if i connect something to a 6gb (an internal 1tb hd) port, its not even visible in ubuntu.

There should be no problems with using a SATAII HDD on a (supported) SATAIII port. 

Asus really should be doing a better job with its website, all it says under 'specifications' for the SATAIII ports is- 

> **Marvell® PCIe SATA 6Gb/s controller** 

[http://www.asus.com/product.aspx?P_ID=wurRaDZ8lo4Ckukj](http://www.asus.com/product.aspx?P_ID=wurRaDZ8lo4Ckukj)

I think its a Marvel 9123 from the drivers is provides for windows. 

I really wouldnt worry about it, a SATAII HDD on a SATAIII port wont be that much faster (sustained transfer will be pretty much exactly the same speed...and 'pretty much' means it could well be slightly slower). Its not worth the trouble of trying to find drivers for the marvell controller, etc.. 

> **LowSky said:**
> When you switch out a motherboard and dont connect the drives to the same port numbers you are going to have issues like these.

Using different ports can give issues, but that would mainly be for multipule HDD setups. For single drive seups, its not normally a problem.....

---

