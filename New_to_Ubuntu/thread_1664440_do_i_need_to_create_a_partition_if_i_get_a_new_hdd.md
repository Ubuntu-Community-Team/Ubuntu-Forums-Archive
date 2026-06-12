---
title: "do i need to create a partition if i get a new hdd ?"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by neil_1 on 2011-01-10
ive seen all those posts about people having problems with their partitions etc and was wondering 
if i installed a new internal hdd ,
would i have to still create a new partition or can i install ubuntu on it right away ?
 
also 
can i install ubuntu x64 side by side with vista x32 ?

---

### Post by cipherboy_loc on 2011-01-11
1) Most likely you will have to format it before installing Ubuntu. Remove the current HD, swap in the new one, boot the LiveCD, create an ext4 with GParted, and install.
2) If you have a 64 bit processor, yes. Install Grub on the Ubuntu hard drive, and set your computer to boot from the 2nd disk.

Cipherboy


> **neil_1 said:**
> ive seen all those posts about people having problems with their partitions etc and was wondering 
if i installed a new internal hdd ,
would i have to still create a new partition or can i install ubuntu on it right away ?
 
also 
can i install ubuntu x64 side by side with vista x32 ?

---

### Post by Bucky Ball on 2011-01-11
Not that hard. Disk formatting takes place during the install. 

If Gparted doesn't recognise the disk, slap any type of partition on the whole lot. It will be deleted when you install Ubuntu anyway and replaced with EXT4 partition(s).

I'd go for manual install as there is nothing else on it and make these partitions at least:

/ = OS, 20Gb is plenty (I generally go 15Gb)
/home = your data and setting, as big as you like;
/swap = 2Gb, or 4Gb if you want to hibernate.

These partition names are defaults in the install section. You can add any other you want. Make them EXT4 (except /swap which looks after itself). You can play around before hitting the button of no return so if you make a mistake just cancel partitioning and start again. And stick to 10.04 LTS. 10.10 has some issues right now. 

If you are going to install Vista, install that first on a partition big enough for it and leave the rest free space. When you are at the manual partitioning section you will see your vista install clearly; an NTFS partition. Just don't touch that and you'll be fine. 

Side by side with Vista? Easy. Just DON'T try this with 10.10 at the moment. That is one of the issues - known to wipe Windows install. This WON'T happen with 10.04 LTS. 

Welcome to the forums. ;)

---

### Post by neil_1 on 2011-01-11
hi bucky ball ):P
im a newbie to the whole thing so am i getting this right ?
do i have to remove the hdd containing windows in it to install ubuntu on the 2nd hdd ?
or does ubuntu ask which hdd to use ?
if ubuntu dosnt recognize the 2nd hdd then ? dint get this part :confused:
 
> **Bucky Ball said:**
> If Gparted doesn't recognise the disk, slap any type of partition on the whole lot. It will be deleted when you install Ubuntu anyway and replaced with EXT4 partition(s).
 
I'd go for manual install as there is nothing else on it and make these partitions at least:
 
/ = OS, 20Gb is plenty (I generally go 15Gb)
/home = your data and setting, as big as you like;
/swap = 2Gb, or 4Gb if you want to hibernate.

why do i have to use gparted for a new hdd ?
is it to make system,home and swap partitions ?
dosnt the ubuntu installer create them automatically ?
 
edit:
whas the difference b/w 10.04 and 10.04.1 ?
because i have 10.04.1 :S

---

### Post by HDave on 2011-01-11
During the install you get to pick the hard drive you want to install Ubuntu on.  If the hard drive you want has no partitions (because it is brand new) the installer will make them for you using appropriate sizes.  

The installer is very good about making sure you don't lose any data.  Nonetheless, back up everything first!

You should never have to manually mess around with disk partitions....and forget you ever heard of gparted.

---

### Post by Bucky Ball on 2011-01-11
Removing the Windows HDD is precautionary so you don't accidentally overwrite Windows and not that great because the Ubuntu install won't pick up the fact you have Windows installed and add that to the boot menu (grub2). You'll need to do that later when you re-install the Windows disk, which is easy enough I guess.

Yes, Ubuntu will make those things as directories (folders) NOT partitions and will put them all inside one big partition using all free space. This is sometimes not as you would like but it is fixable later. Moving the contents of your /home folder to a /home partition later can be tricky though.

10.04.1 is the one to go for, yes. :)

---

### Post by neil_1 on 2011-01-11
when im installing ubuntu , it does check how much space of which hdd has been used right ? :confused:
so if the 2nd is new ,its goin to be completely empty so i guess i can install on the one that is empty 
also can i go by what HDave said and do the installation automatically instead of manual ?
i dont wanna mess up :(

---

### Post by Synthetic Sam on 2011-01-11
A precautionary note:

If you install Ubuntu on your 2nd HDD (the new one) with the windows HDD still in the computer, the MBR of the first HDD will be overwritten by GRUB.  This means that you'll need the 2nd HDD in the system to boot Windows.

Windows will probably not be in the boot menu after install either.  You may need to run 
```
sudo update-grub
```
to update the list of operating systems from within ubuntu.

Conversely, if you remove the windows HDD from the computer and install ubuntu on the "second HDD" then reinsert the windows HDD as the first, you may find that grub will not boot ubuntu, because it will be looking on the wrong HDD for it. (it would look to boot from (hd0,1) where the ubuntu boot partition was during install, but that is now the windows partition on the first disk and ubuntu is on (hd1,1) for example.)

As far as I'm aware this leaves you two options:

1) Install ubuntu on the second HDD with the windows one in (windows boot loader will be broken) then update grub and you should be able to boot windows, but you need both disks to run any operating system.
2) Install ubuntu on the second HDD with the windows one in, then boot ubuntu, and manually grub-install to the second HDD (moving the bootloader to the ubuntu HDD MBR), then repair your windows HDD MBR using your windows installation disk.  This will allow you to boot ubuntu (and windows once update-grub is run) from the second HDD being selected in the BIOS as the first boot HDD, OR run windows stand-alone if the ubuntu disk is removed.

Hope that was helpful and not too confusing.

[edit] Just thought of a third option, if you install with the windows HDD removed and re-add it afterwards so that the ubuntu HDD is in the "primary" socket of the HDD controller (lowest numbered for SATA configurations, so add the windows HDD to a higher numbered socket will appear lower in the list of HDDs in the BIOS) then it won't stop GRUB from booting ubuntu, and you should be able to add Windows to the GRUB list using update-grub, AND the windows HDD won't be touched.

[edit2] **This is from my experience with 10.10, so I guess that's why they've recommended Lucid 10.4**

---

### Post by Thras0 on 2011-01-11
tnkx for sharing this. i was also planing  in dual booting. your post was just what i needed

---

### Post by HDave on 2011-01-11
> **neil_1 said:**
> when im installing ubuntu , it does check how much space of which hdd has been used right ? :confused:
Yes.  It shows you a nice picture.

> **neil_1 said:**
> so if the 2nd is new ,its goin to be completely empty so i guess i can install on the one that is empty 

Yes.

> **neil_1 said:**
> also can i go by what HDave said and do the installation automatically instead of manual ?
i dont wanna mess up :(
There's no getting around it, you are going to have to try.  It's less scary than you think and there is no harm in running the installation multiple times.  There is nothing permanent about a partition....if you don't like the partitions on your new second drive...you can delete them during a subsequent installation.

Also -- Is your second hard drive is removable? (e.g. a USB hard drive?).  If so, then your situation is  bit more complicated and you need to take Synthetic Sam's advice into account.  If it is a permanently installed hard drive then you can ignore all the talk about GRUB.

---

### Post by Bucky Ball on 2011-01-11
Go the manual. Don't panic, stay relaxed. Planning is what it's all about. Make sure you have what you are going to do written down before you get to the partitioning section (included partition sizes to give you a launch pad for your improvisations!). When you get to manual partitioning section, you can set up and cancel as many times as you like before you hit the button of no return. Experiment until you feel comfortable and you know what you're doing is what you want.

Your Windows install will be very clearly in front of you as an NTFS partition. Just don't go there.

Have a look at the partitioning suggestions I made in post #3. Remember; you can't have more than four primary partitions on one physical hard drive. BUT, you *can* have three primary partitions on one physical hard drive PLUS an extended partition (the fourth partition) which can have just about as many logical drives as you like *inside* it. Still seen as one partition (the extended one) and Ubuntu install will happily live on a logical drive inside an extended partition. ;)

ps: Go with 10.04 LTS. 10.10 has some issues at the moment and let's not complicate yours. ;)

---

### Post by neil_1 on 2011-01-11
alright thanks guys !
im gawna get my new internal hdd only in a month after my exams are done with =/
if i have anything else i'll post back :)

---

### Post by neil_1 on 2011-01-20
ok umm guys i popped open my lappy to check if i had an additional slot before goin ahead and getting a new hdd and turns out i dont :'(
so if i remove the windows hdd, put in the new one and install ubuntu on it , would i be able to use the windows again normally ?

---

### Post by neil_1 on 2011-01-20
ok umm guys i popped open my lappy to check if i had an additional slot before goin ahead and getting a new hdd and turns out i dont :'(
so if i remove the windows hdd, put in the new one and install ubuntu on it , would i be able to use the windows again normally ?

---

### Post by neil_1 on 2011-01-20
ok umm guys i popped open my lappy to check if i had an additional slot before goin ahead and getting a new hdd and turns out i dont :'(
so if i remove the windows hdd, put in the new one and install ubuntu on it , would i be able to use the windows again normally ?

---

### Post by neil_1 on 2011-01-20
ok umm guys i popped open my lappy to check if i had an additional slot before goin ahead and getting a new hdd and turns out i dont :'(
so if i remove the windows hdd, put in the new one and install ubuntu on it , would i be able to use the windows again normally ?

---

### Post by neil_1 on 2011-01-20
ok umm guys i popped open my lappy to check if i had an additional slot before goin ahead and getting a new hdd and turns out i dont :'(
so if i remove the windows hdd, put in the new one and install ubuntu on it , would i be able to use the windows again normally ?

---

### Post by neil_1 on 2011-01-20
i have no idea why that just hapened :(
cant delete double posts :'(

---

### Post by audiomick on 2011-01-20
Regarding the multiple posts:

[http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331)

> If you happen to come across multiple posts that are identical, please  use the report feature to bring this to the attention of the staff, who  will do their best to tidy it up and keep threads readable.Which is to say, click on the "report abuse" button in one of the multiples and just write "multiple posts" or something like that.

It is not your fault. The forum is having some technical issues.


As far as swapping drives goes, if you physically change the drive and install another OS to a different one, you can boot into either OS by re-installing the appropriate drive.

If you have room on your current drive, you can also reduce the size of the Vista partition and install Ubuntu into the space that becomes free. Bearing in mind the advice in the thread thus far, it would be wise to stick to 10.04 for this.

I have seen a lot of advice suggesting that it is better to use the Vista partitioning tool to schrink the Vista partition. You should backup anything that is really important before you do any partitioning work on any system.
When you have changed the size of the Vista partition, start Vista once or twice, and let it run its' disk check thing if it wants to.

---

### Post by neil_1 on 2011-01-20
> **audiomick said:**
> As far as swapping drives goes, if you physically change the drive and install another OS to a different one, you can boot into either OS by re-installing the appropriate drive.
 
If you have room on your current drive, you can also reduce the size of the Vista partition and install Ubuntu into the space that becomes free. Bearing in mind the advice in the thread thus far, it would be wise to stick to 10.04 for this.
 
I have seen a lot of advice suggesting that it is better to use the Vista partitioning tool to schrink the Vista partition. You should backup anything that is really important before you do any partitioning work on any system.
When you have changed the size of the Vista partition, start Vista once or twice, and let it run its' disk check thing if it wants to.
thanks audiomick
but when wubi runs it mentions that some performance will be reduced =/
what exactly reduces ?

---

### Post by audiomick on 2011-01-20
Don't know what is reduced in Wubi, I haven't done a Wubi install. I'd imagine it has to do with shared resources or something, but that is only a guess.

---

### Post by neil_1 on 2011-07-17
> **Bucky Ball said:**
> 
Side by side with Vista? Easy. Just DON'T try this with 10.10 at the moment. That is one of the issues - known to wipe Windows install. This WON'T happen with 10.04 LTS. 

Welcome to the forums. ;)
is this still there ?
i want to upgrade from 10.04 to 10.10

---

### Post by neil_1 on 2011-07-21
> **neil_1 said:**
> is this still there ?
i want to upgrade from 10.04 to 10.10
tried and dosnt

---

