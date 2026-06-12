---
title: "A quick question?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by RJ12 on 2009-06-24
Ok now my parents want me to switch to Windows XP. How would I go about doing that. I have the Cd would I just pop it in delete the partitions then it will uninstall grub and it will let windows come up with its own bootloader without using grub

Sorry but I have to leave Ubuntu:(

Can you help me one last time?

---

### Post by milton1 on 2009-06-24
if it is a full version cd, then yes, just boot from the cd and follow the prompts.

---

### Post by Tews on 2009-06-24
Just pop in the install cd and reformat the drive when it comes up.... I guess dual booting is out of the question?? :confused:

---

### Post by diwas on 2009-06-24
Do you currently have a dual boot or are you talking about a fresh install of XP?

---

### Post by Sef on 2009-06-24
> I have the Cd would I just pop it in delete the partitions then it will uninstall grub and it will let windows come up with its own bootloader without using grub

Yes that will work.  You could ask them if they would consider dual booting.

>  Sorry but I have to leave Ubuntu:sad:

That's ok.  When you get your own computer, you can put Ubuntu on it.

---

### Post by RJ12 on 2009-06-24
> **diwas said:**
> Do you currently have a dual boot or are you talking about a fresh install of XP?
It is currently only on Ubuntu 9.04 no dual boots and I want now only Windows XP on their

---

### Post by Cheesemill on 2009-06-24
You may have problems with the Windows installer not recognising the hard disk as valid if it has ext2/3 partitions on it.
 
Just run the Ubuntu Live CD and use Partition Editor to delete all the partitions on your drive. Windows should then install without any problems.

---

### Post by NightwishFan on 2009-06-24
Good luck, and keep wubi in mind.

---

### Post by diwas on 2009-06-24
Pop in live CD and delete all the partitions. Reboot with Windows XP cd on and you'll have all the instructions there.

---

### Post by RJ12 on 2009-06-24
Ok In GParted I see /dev/sda1 which says ext3
there is also /dev/sda2 which says extended
there is also /dev/sda5 which says linux-swap which is under /dev/sda2
which do I delete

---

### Post by Gaweph on 2009-06-24
> **Cheesemill said:**
> You may have problems with the Windows installer not recognising the hard disk as valid if it has ext2/3 partitions on it.
 
Just run the Ubuntu Live CD and use Partition Editor to delete all the partitions on your drive. Windows should then install without any problems.

Im pretty sure that windows will recognize the harddrive and partitions, it just wont know what to do, and you wont be able to install onto them.

Just pop in teh Windows XP cd, and follow the instructions, when you get to teh selecting where to install, just press D (or whatever key it says to delete)

And you will be able to delete and reformat the partition to NTFS from there.

---

### Post by milton1 on 2009-06-24
> **RJ12 said:**
> Ok In GParted I see /dev/sda1 which says ext3
there is also /dev/sda2 which says extended
there is also /dev/sda5 which says linux-swap which is under /dev/sda2
which do I delete

all of them

---

### Post by RJ12 on 2009-06-24
> **Gaweph said:**
> Im pretty sure that windows will recognize the harddrive and partitions, it just wont know what to do, and you wont be able to install onto them.

Just pop in teh Windows XP cd, and follow the instructions, when you get to teh selecting where to install, just press D (or whatever key it says to delete)

And you will be able to delete and reformat the partition to NTFS from there.

> **milton1 said:**
> all of them
So which one do I do pop in windows XP and delete from there or GParted

---

### Post by Gaweph on 2009-06-24
If youve currently loaded the live CD, and thats where you are then just use GPARTED.

it sounds like you just want to wipe the drive and start again.

I would suggest partitioning it this time, then if you ever change your mind again, you will have a safe place to save everything.

---

### Post by RJ12 on 2009-06-24
It wont let me delete the ones that say extended and linux-swap

---

### Post by Gaweph on 2009-06-24
Just try it with the windows CD.

Im sure it works, when you get to the blue screen that asks where to install it, you can go around deleting all the partitions etc...

If your still in GPartition, then check that the ones you cant delete are unmounted.

---

### Post by NightwishFan on 2009-06-24
Make sure you are on live cd, not using installed system to delete partitions.

You need to turn the swap off by right clicking and using swap off. Then you can delete the unmounted extended partitions.

Just installing Windows should be fine. Tell it to use the entire disk. (I hope you have drivers/install key otherwise your outta luck.)

---

### Post by Gaweph on 2009-06-24
Yes very good point, i was assuming you were usign the live CD and not booted into ubuntu (which you cant delete as your using it)

---

### Post by jimv on 2009-06-24
Nm

---

### Post by 3rdalbum on 2009-06-24
If your computer uses SATA and you are installing Windows XP, you might come across some trouble. Windows XP's installer does not support SATA.

You can use a floppy disk (how quaint!) to load your SATA drivers into the Windows installer, or turn on IDE compatibility mode in your BIOS until you have installed Windows XP and added the SATA driver.

---

### Post by Cheesemill on 2009-06-24
> **Gaweph said:**
> Yes very good point, i was assuming you were usign the live CD and not booted into ubuntu (which you cant delete as your using it)

Even using the Live CD the swap partition would still be mounted.

The Live CD automatically makes use of any swap partitions it finds to improve performance.

---

### Post by Cheesemill on 2009-06-24
> **Gaweph said:**
> Just try it with the windows CD.

Im sure it works, when you get to the blue screen that asks where to install it, you can go around deleting all the partitions etc...


9 times out of 10 this will work fine, but sometimes the Windows installer refuses to see the drive as valid because of the non-native partitions.

---

### Post by papenpj on 2009-06-24
Well You say your parents want windows and only windows, will they know the difference if you dual boot?
If you were to give windows a decent size patition leaving 10GB for ubuntu.  Reinstall windows, then install ubuntu.
setup the menu.lst file so Windows would be the first option above the automatic list. Set it to use the hidden menu where you need to press "ESC" to access grubs menu and a timeout of say 2-4 seconds. You could easily have it with the ability to dualboot and nobody without much computer experience would notice the difference.

Edit:
Oh and Im not saying you shouldn't listen to your parents but, If they don't know the difference and you want to use Linux because it better. It couldn't hurt to have a backup operating system ready to go if windows fails.

---

### Post by Polaris96 on 2009-06-24
to wipe everything?  forget parted this is the easy way:

YOU CANNOT UNDO THIS AND YOU WILL BE COMPLETELY WHACKING YOUR UBUNTU SYSTEM.  DO NOT GO FURTHER UNLESS YOU REALLY WANT TO WIPE OUT THE SYSTEM.

sudo fisk /dev/sda

type 'm' to get an idea of the available commands
if you want to type 'p' and you will see a list of partitions.  you don't have to do this, i'm just giving a tour

type 'o' to create a new DOS partition table.

type 'w' to write the changes.  When you press enter after typing 'w', you will be at the point of no return.  

reboot the system.  you will probably need to do a hard reboot (reset button on the chassis)

...and now I know how veterinarians must feel when they have to put down a well loved family pet :(

---

### Post by Cheesemill on 2009-06-24
> **Polaris96 said:**
> sudo fisk /dev/sda
Should be:
```
sudo fdisk /dev/sda
```

---

### Post by Polaris96 on 2009-06-28
thanx cheesemill.  That could've really messed up what I was trying to say

---

