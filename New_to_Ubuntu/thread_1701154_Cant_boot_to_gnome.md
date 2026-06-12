---
title: "Cant boot to gnome"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-03-06
Recently I accidentally did a dist-upgrade for my ubuntu and that failed because I nearly have zero space...
Now I cant log in.
The boot screen isn't the old splashscreen of ubuntu, it is
```
Ubuntu 10.10
. . . .
```

And When the login screen appears it doesn't detect my mouse or keyboard.
It is Black and instead of the ubuntu sign there is a blue computer and there is an error in the upper right.

Also I cant boot into recovery mode, it stops at some point of loading.

What to do:(

Here is what it looks like, sorry for the crappy photos..

---

### Post by maqtanim on 2011-03-06
Can please write what is the ERROR MESSAGE is? I can't read it from your provided image.

---

### Post by Avidanborisov on 2011-03-06
> **maqtanim said:**
> Can please write what is the ERROR MESSAGE is? I can't read it from your provided image.

This is the error:

> Install Problem!
The configuration defaults for GNOME power management have not been installed correctly. 
Please contact your computer administrator.

---

### Post by Avidanborisov on 2011-03-06
Someone?

---

### Post by Avidanborisov on 2011-03-06
Guys, I need help

---

### Post by Avidanborisov on 2011-03-06
I really need help!

---

### Post by maqtanim on 2011-03-06
Seems like you have to free some spaces in to your system. You can still use the terminal. Press Ctrl+Alt+F1 to use the terminal from login screen. Enter your username and password and execute the following command:
```
sudo apt-get -f install
``` then run the following command
```
sudo apt-get clean
``` then try to restart the pc by following command
```
sudo reboot
```

---

### Post by Avidanborisov on 2011-03-06
> **maqtanim said:**
> Seems like you have to free some spaces in to your system. You can still use the terminal. Press Ctrl+Alt+F1 to use the terminal from login screen. Enter your username and password and execute the following command:
```
sudo apt-get -f install
``` then run the following command
```
sudo apt-get clean
``` then try to restart the pc by following command
```
sudo reboot
```

As I said, keyboard is not detected so I can't enter terminal.

---

### Post by col48 on 2011-03-06
Can you boot from a Live CD - if you have one, of course? If you can, this should recognise the keyboard.

---

### Post by maqtanim on 2011-03-06
Please, go  to the recovery mode. To enter the recovery mode, select the name "Ubuntu (Recovery Mode)" from the grub (from where you select the name of the Operating system). If you have only Ubuntu in your system, then the GRUB will not be visible. To enter the GRUB for selecting the recovery mode, press F1 after booting the computer.

---

### Post by col48 on 2011-03-06
OP's last comment was

> As I said, keyboard is not detected so I can't enter terminal.


If that's true, he won't be able to select anything without some external influence - eg a Live CD?

---

### Post by Avidanborisov on 2011-03-06
> **col48 said:**
> Can you boot from a Live CD - if you have one, of course? If you can, this should recognise the keyboard.

I only have live-cd of 10.04

> **maqtanim said:**
> Please, go  to the recovery mode. To enter the recovery mode, select the name "Ubuntu (Recovery Mode)" from the grub (from where you select the name of the Operating system). If you have only Ubuntu in your system, then the GRUB will not be visible. To enter the GRUB for selecting the recovery mode, press F1 after booting the computer.

As I said, I cant boot into recovery mode.

---

### Post by maqtanim on 2011-03-06
Well... I actually didn't saw that too! :P

If you donot have any 10.10 live CD then I am out of my idea. :( Let's see what is other's opinion. Or you can reinstall Ubuntu.

I think you have allocated low space for root partition. Did you install ubuntu inside windows (wubi installation)? How much space did you specified for Ubuntu (specially the space for root partition)

---

### Post by Avidanborisov on 2011-03-06
Ok, I used my 10.04 live-cd and from seeing gparted I have:
[IMG]http://eliad.org/uploads/1299536762.png[/IMG]

I will burn 10.10 cd soon, what can be done for now?
Actually I dont care to reinstall ubuntu as log as it stays in its partition and I don't have to format all the drive.

---

### Post by Avidanborisov on 2011-03-07
OK I burned 10.10 cd and deleted the partition of ubuntu and made it again with ext4 filesystem here:
[IMG]http://eliad.org/uploads/1299609834.png[/IMG]
but when I try to install ubuntu on that it says:
> No root file system is defined
Please correct this from the partitioning menu

---

### Post by Avidanborisov on 2011-03-07
someone?
please!

---

### Post by teward on 2011-03-07
Okay, not to be annoying, but if you bump your thread every few minutes or every few hours, it doesnt help you at all.  Remember, these are forums, not IRC chat.  Not everyone is on 24/7, and you must expect that you wont get an immediate response.  Bumping your post once a day is acceptable, but anything more than that can get you in trouble sometimes.


The issue I think can be dealt with for that ext3 partition is if you MANUALLY specify the partitioning in the installer menu.  I.E. when it asks you how to partition things, you should specify that you want to manually specify partitions, then you should be able to specify the ext3 partition as your partition to be mounted as /.  I've had to do that occasionally when install gets  interrupted on my systems by power outages and stuff, and I"ve had to reinstall.

Although I might recommend you use ext4 as your partition type, as Ubuntu 10.04 and Ubuntu 10.10 work somewhat better on ext4.  Unless you require an ext3 partition type.

---

### Post by Avidanborisov on 2011-03-07
> **EvilPhoenix said:**
> Okay, not to be annoying, but if you bump your thread every few minutes or every few hours, it doesnt help you at all.  Remember, these are forums, not IRC chat.  Not everyone is on 24/7, and you must expect that you wont get an immediate response.


The issue I think can be dealt with for that ext3 partition is if you MANUALLY specify the partitioning in the installer menu.  I.E. when it asks you how to partition things, you should specify that you want to manually specify partitions, then you should be able to specify the ext3 partition as your partition to be mounted as /.  I've had to do that occasionally when install gets  interrupted on my systems by power outages and stuff, and I"ve had to reinstall.

Sorry for the bumping but I wait and wait and for the meanwhile it is already comes to the second and third pages so this was the only way for getting attention.

First, as I said I made ext4 partition.
Second, I didn't really understand where to specify and what to do. When I run the install I selected the option to Specify partition manually (advanced) and when I try to install on the ext4 partition I get the error:
[IMG]http://eliad.org/uploads/1299600984.png[/IMG]
Any ideas?

---

### Post by teward on 2011-03-07
Select the ext partition, hit "Change..."

In the dialog that pops up, you should see a "Mount point:" dropdown.  Click that, choose " / " (without the quotes) as the mount point, should allow you to install.


Note that when you do this, you'll nuke whatever's currently on that partition, and thus you'll lose any data currently on that partition.
***CLARIFICATION***  To be absolutely certain you understand what i mean... the only data that will be erased prior to installing to that partition is the data already on the ext4  partition.  The NTFS partition wont be affected at all.

---

