---
title: "Re- installing ubuntu"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by bessy on 2009-04-06
Hi, having loaded ubuntu as my only os and having a good play with it i would like re-install it as i am not sure i selected to use all available disc space.  I have tried putting the disc i got in and selecting "install ubuntu now" and it loads for a while then comes up with lots of error code. Do i have to do something 1st?

Thanks.

---

### Post by ptn107 on 2009-04-06
Put the CD in and restart.  Let it boot to the menu on the disk and select 'Install Ubuntu.'

---

### Post by bessy on 2009-04-06
Hi, yes i have tried that and loads for a while then flash loads of code up?

---

### Post by kanikilu on 2009-04-06
If you are happy with your current installation and don't want to reinstall simply to use all the disk space, you can non-destructively resize your partitions using gparted. There are numerous how-to's and guides, this one assumes you are using the GParted Live CD, although you can use an Ubuntu Live CD or any other live distro that includes gparted.

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Swatfoot on 2009-04-06
I,m still new to ubuntu myself but I would first check the disk for errors
as I had a bad disk give me problems during a install.If disk is ok you could run live cd, and "sudo gparted' will let get a better idea how your 
partions are set.Remember also to save space for swap. maybe someone more exp might have better answer. good luck!

---

### Post by sneeks on 2009-04-06
> **Swatfoot said:**
> I,m still new to ubuntu myself but I would first check the disk for errors
as I had a bad disk give me problems during a install.If disk is ok you could run live cd, and "sudo gparted' will let get a better idea how your 
partions are set.Remember also to save space for swap. maybe someone more exp might have better answer. good luck!

it does sound like a bad disc,d/l a new one and burn me thinks....
and all should be well..

---

### Post by presence1960 on 2009-04-06
> **bessy said:**
> Hi, having loaded ubuntu as my only os and having a good play with it i would like re-install it as i am not sure i selected to use all available disc space.  I have tried putting the disc i got in and selecting "install ubuntu now" and it loads for a while then comes up with lots of error code. Do i have to do something 1st?

Thanks.

First check the simplest thing it may be- visually inspect your CD for dirt, smudges, etc. Maybe something on surface is causing errors. Clean it if necessary. If that doesn't work you'll probably need to burn a new one.

Once you get past that hurdle you can boot the Live CD and in terminal run ```
gksu gparted
``` or go to System > Administration > Partition Editor. This will bring up your disk(s) info in Partition Editor (gparted). You will then know if all of your disk space is used by Ubuntu or not. If it is not you can add the unused space to Ubuntu from within Partition Editor without going through a reinstall- that is if you are happy with your current install.

First check on the CD problem then you can cross the other bridge when you get to it. Everyone will be glad to help you.

---

