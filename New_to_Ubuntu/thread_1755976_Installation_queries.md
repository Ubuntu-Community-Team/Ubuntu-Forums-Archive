---
title: "Installation queries"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by anohs on 2011-05-11
I am using USB (unetbootin) to install 11.04

During the installation process, I am being asked to provide place for root directory. I have a seperate window partition where I want to install ubuntu.

Can anyone provide any detailed step by step instruction for the installation? I am very new to Ubuntu

---

### Post by Hedgehog1 on 2011-05-11
Here is an example of a Dual Boot install (not WUBI) that assumes you have manually creating the partitions yourself:


In gparted, create 3 partitions:

1) ext4 '/'
2) Linux swap
3) ext4 '/home'

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to the **Disk Space Allocation** screen.

If you are installing Natty, select the '**Something Else**' option, If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-11
The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


***The Hedge***

:KS

---

### Post by ClientAlive on 2011-05-11
Doesn't Ubuntu 11.04 have a selection: "Install Alongside Another  . . ." (something)? I've never used that selection but I thought it walked you through a default install that avoids the details of allocating partitions and all that.

---

### Post by Hedgehog1 on 2011-05-11
> **ClientAlive said:**
> Doesn't Ubuntu 11.04 have a selection: "Install Alongside Another  . . ." (something)? I've never used that selection but I thought it walked you through a default install that avoids the details of allocating partitions and all that.

It does indeed offer an 'install alongside'.  And for most folks that works just fine.

The 'install alongside' only creates two partitions:
1) ext4 '/'
2) Linux swap

This manual method creates three partitions:
1) ext4 '/'
2) Linux swap
3) ext4 '/home'

Also, sometimes the install cannot figure out what to do with the drive layout, so a manually install is needed.


***The Hedge***

:KS

---

### Post by ClientAlive on 2011-05-11
> **Hedgehog1 said:**
> It does indeed offer an 'install alongside'.  And for most folks that works just fine.

The 'install alongside' only creates two partitions:
1) ext4 '/'
2) Linux swap

This manual method creates three partitions:
1) ext4 '/'
2) Linux swap
3) ext4 '/home'

Also, sometimes the install cannot figure out what to do with the drive layout, so a manually install is needed.


***The Hedge***

:KS


I see . . . 

Right on.

:D

---

