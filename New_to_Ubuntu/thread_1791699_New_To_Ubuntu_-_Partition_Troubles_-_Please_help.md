---
title: "New To Ubuntu - Partition Troubles - Please help"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by jcyshin on 2011-06-27
Hi Guys, 

Just joined the forums and decided to get rid of windows all together. 

However, I have fun into my first big problem. Due to my lack of Ubuntu knowledge, I have managed to partition my 250GB HDD like the screen shot below.

unfortunately, I have no idea how to fix it, can someone please please please help me? 

I tried to install JAVA JDK as well so i can run Android but thats another story for another day. 

Any assistance would be much appreciated.

I am looking at partitioning my 250GB HDD into 4 Partitions, Ubuntu, Windows 7, Android OS 3.0 & XP.

I have attached a screen shot of what it looks like at the moment.

Thanks in advance guys.

---

### Post by el_koraco on 2011-06-27
You can't install Windows 7 on a logical partition, nor can you install it on an ext4 filesystem. It needs to be on a NTFS filesystem, and the first primary partition. I'd suggest you redo your partitioning scheme. First make a primary partition with NTFS in which to install Windows (30-50 GB). Then make an extended partition to put Ubuntu on. Divide the extended partition into three logical ones. 

Make one partition of 20 GB. this will be your / (root) partition. it will serve to host all the system files. Make a second logical partition, with a size of a 100, more or less. This will be your /home partition, used to host your user data. kinda like a Windows D: drive. The last one should be as big as your ram size, and will be used for the swap partition. Leave the rest unallocated.  

Then put the Windows install CD in the drive, and install it to the first primary NTFS partition. After you install Windows, put the Ubuntu Live CD in the drive. When installing, use the "something else", and then "manual partitioning" option. Choose the 20 GB partition, and choose to format it as ext4, with the mountpoint /. Choose the 100 GB partition, format it to ext4, and set the mountpoint to /home. Lastly, choose the last partition, and choose to use it as Linux swap. Reboot, and you'll get a selection of whether to boot to Windows or Ubuntu.

---

### Post by coffeecat on 2011-06-27
Welcome to the forum!

First thing, you need to clarify this:

> **jcyshin said:**
> 
Just joined the forums and decided to get rid of windows all together. 


<snip>


I am looking at partitioning my 250GB HDD into 4 Partitions, Ubuntu, Windows 7, Android OS 3.0 & XP.


You want to get rid of Windows, but you want to have partitions for Windows 7 and XP. Which do you want?

I'll make some commments about your screenshot.

Your home partition is sda1. Your Ubuntu root (/) partition is a logical one - sda6 - but curiously has the label "Windows 7". It's formatted ext4 which is just fine for Ubuntu, but which would not do for Windows. Then you have a logical partition, sda5, which is your Ubuntu boot partition but which has the partition label "Android". And at 46GiB, it's the biggest boot partition I have ever seen!

I think you need to clarify what you are trying to achieve and then ask for help about how to organise your partitions. You may need to start over if you want two varieties of Windows, Ubuntu and Android.

By the way, Windows needs to boot from a primary partition. If you really want to run Windows, you need to be aware of that.

---

### Post by jcyshin on 2011-06-27
Hi Guys,

Thank you both for the information it has opened my eyes to how much I don't know about Ubuntu and anything else that has to do with OS's.

Any chance someone tell me how to wipe the drive clean so I can start again?

I will take all your advice and think carefully before I start.

can you help me clarify what I should do it i wanted all four OS's in a quad boot and how the partitions should be like? I know some of the questions [el_koraco]("http://ubuntuforums.org/member.php?u=1232725") have answered already but lets be 100% sure i don't stuff it up the second time around.

I want Windows 7 to do my uni work and need XP to run some of the stupid Korean Internet Banking systems as after a few updates in Windows 7 the stuff no longer works. 

please help :D

---

### Post by robertc36 on 2011-06-27
I would run xp virtually either in windows or ubuntu.
You could then let the windows installer handle the partition. Then install ubuntu and again just choose  the size you want for the OS.
That's the less complicated method.

---

### Post by jcyshin on 2011-06-27
Thanks robertc36, I will think about that, not having usb access to VB got me thinking of doing the Quad boot. 

still need to find away to get rid of my current Ubuntu Partitions, either a way to repartition without reinstalling or just tell me how I can reinstall .

---

### Post by F.G. on 2011-06-27
hi jcyshin,
just my two cents, but i would second the use of virtual box, or vmplayer, rather than having such a complex boot setup, I thought that if you install guest additions to a virtual box virtual computer it allowed usb access.  otherwise I whould suggest doing a fresh Windows install, and getting all the Windows/ntfs stuff done (i'm not sure how but I think you can install Windows 7 and XP next door to each other). then install ubuntu and do your partitioning (ext4 to be used for /).
N.B. in your picture you have a 88.5GB swap partition, which is way too big.  i've heard it said that you swap partition should be no bigger than twice the size of you main memory (RAM).
good luck.

---

### Post by jcyshin on 2011-06-27
Thank you to all that have contributed to this thread. I will now reinstall Ubuntu 11.04 as my main OS and run VB or VM for the rest.

---

### Post by subchief on 2011-06-27
> **jcyshin said:**
> Thank you to all that have contributed to this thread. I will now reinstall Ubuntu 11.04 as my main OS and run VB or VM for the rest.
  Hey....
i just read your post and i think i got an idea what you want to do!!!

ok...using your ubuntu disk start the machine into the ubuntu live environment!i.e boot from cd into the live environment!
next start gparted application by clicking on system>administration>Gparted
next click on devices then create a new partition table
following the prompts, create 4 partitions of your hard disk...in whatever way you want.
next install the various os's in the different partitions!!!for example...partition 1 is XP 2 is Win7 and 3 is Android.
Finally,install ubuntu!!!!note...ubuntu has to be installed as the last os since it will be the one giving you the option to boot inti the other os's.
i have assumed that you know your way around installing os's and partitioning hard disks so i havent gone into much detail.If however there is a problem,let me know n see what we can do!!!
Good Luck!!!

---

### Post by jcyshin on 2011-06-28
> **subchief said:**
> Hey....
i just read your post and i think i got an idea what you want to do!!!

ok...using your ubuntu disk start the machine into the ubuntu live environment!i.e boot from cd into the live environment!
next start gparted application by clicking on system>administration>Gparted
next click on devices then create a new partition table
following the prompts, create 4 partitions of your hard disk...in whatever way you want.
next install the various os's in the different partitions!!!for example...partition 1 is XP 2 is Win7 and 3 is Android.
Finally,install ubuntu!!!!note...ubuntu has to be installed as the last os since it will be the one giving you the option to boot inti the other os's.
i have assumed that you know your way around installing os's and partitioning hard disks so i havent gone into much detail.If however there is a problem,let me know n see what we can do!!!
Good Luck!!!

Thanks for that, your idea does sound interesting, please tell me more, you can PM me or leave a message here or even email me, would love to hear your whole plan :)

---

### Post by subchief on 2011-06-28
> **jcyshin said:**
> Thanks for that, your idea does sound interesting, please tell me more, you can PM me or leave a message here or even email me, would love to hear your whole plan :)

Hey, will d that...so far what have you done?

---

### Post by jcyshin on 2011-06-28
> **subchief said:**
> Hey....
i just read your post and i think i got an idea what you want to do!!!

ok...using your ubuntu disk start the machine into the ubuntu live environment!i.e boot from cd into the live environment!
next start gparted application by clicking on system>administration>Gparted
next click on devices then create a new partition table
following the prompts, create 4 partitions of your hard disk...in whatever way you want.
next install the various os's in the different partitions!!!for example...partition 1 is XP 2 is Win7 and 3 is Android.
Finally,install ubuntu!!!!note...ubuntu has to be installed as the last os since it will be the one giving you the option to boot inti the other os's.
i have assumed that you know your way around installing os's and partitioning hard disks so i havent gone into much detail.If however there is a problem,let me know n see what we can do!!!
Good Luck!!!

> **subchief said:**
> Hey, will d that...so far what have you done?

At this stage..... reinstalled 11.04, VirtualBox - running Windows 7 and XP, its working ok but slow and the biggest problem is I have all the programs I need but don't now how to pull it from my External HDD or Internal HDD into the VB. Hence why I think your idea sounds much more appealing. I am also having trouble with Ubuntu finding my DVD RW Drive  so am only installing with the OS's into VB with the current ISO images I have on my Internal and External HDD. 

Then there is a problem of getting Android 3.0 loaded as a separate OS, otherwise I will have to use VB or VMware in one of the other OS's to build my Android Apps lol. From the looks of things I am along way away from doing anything substantial , seems like I not only need help, I need a miracle. 

I know I am asking alot and probably should be starting a new thread for this as well, however being o new to Ubuntu forums, I just don't know how.

---

### Post by subchief on 2011-06-28
> **jcyshin said:**
> At this stage..... reinstalled 11.04, VirtualBox - running Windows 7 and XP, its working ok but slow and the biggest problem is I have all the programs I need but don't now how to pull it from my External HDD or Internal HDD into the VB. Hence why I think your idea sounds much more appealing. I am also having trouble with Ubuntu finding my DVD RW Drive  so am only installing with the OS's into VB with the current ISO images I have on my Internal and External HDD. 

Then there is a problem of getting Android 3.0 loaded as a separate OS, otherwise I will have to use VB or VMware in one of the other OS's to build my Android Apps lol. From the looks of things I am along way away from doing anything substantial , seems like I not only need help, I need a miracle. 

I know I am asking alot and probably should be starting a new thread for this as well, however being o new to Ubuntu forums, I just don't know how.

Yea, VBox does run slow especially if you are running resource hungry applications like games e.t.c However, if you want to try it out, there is a way to access your files from the hardisk via the guest OS in the Virtual Machine.
Here's How,
-shutdown all guest OS's i.e Win7 and XP
-In VBox, Click on settings>shared folders
-Click on the Add folder icon
-Select the folder you want to see from your harddisk
-Then save

As for your DVD drive
-Click on settings>Storage
-click on the CD/DVD icon under storage tree
-Then select CD/DVD Device from the attributes section.
-Click ok!

Now you should be able to access your files and DVD rom from the Guest OS.

To access your shared folder...
-run the virtual machine say XP
-Once its up and running, open the run dialogue box and type  \\vboxsvr\share
where share is the name of the folder you want to access!!!

This should work for your virtual machines...

Would you like to try the other method of installing in separate partitions?
it will take a couple of hours or so but i can help...:p

---

### Post by lakosshoots on 2011-06-28
my suggestion is :
100 MB for /boot - ext2 (primary)
not more than 10 GB for / - ext4 (logical all rest)
most for /home - ext4
swap 2 GB if you have more than 3 GB RAM or 3 GB if you have less than 2 GB RAM 

be aware that you can have 4 primary partition noted /dev/sda1 up to dev/sda4 higher number indicate logical ones.

you can always use gparted as mentioned in another post to reallocate more space between partitions

it might be helpful to give it a look

[http://just-more-thoughts.blogspot.com/2011/06/ubuntu-1104-file-systems-56.html]("http://just-more-thoughts.blogspot.com/2011/06/ubuntu-1104-file-systems-56.html")

---

### Post by jcyshin on 2011-06-28
> **subchief said:**
> Yea, VBox does run slow especially if you are running resource hungry applications like games e.t.c However, if you want to try it out, there is a way to access your files from the hardisk via the guest OS in the Virtual Machine.
Here's How,
-shutdown all guest OS's i.e Win7 and XP
-In VBox, Click on settings>shared folders
-Click on the Add folder icon
-Select the folder you want to see from your harddisk
-Then save
 
As for your DVD drive
-Click on settings>Storage
-click on the CD/DVD icon under storage tree
-Then select CD/DVD Device from the attributes section.
-Click ok!
 
Now you should be able to access your files and DVD rom from the Guest OS.
 
To access your shared folder...
-run the virtual machine say XP
-Once its up and running, open the run dialogue box and type \\vboxsvr\share
where share is the name of the folder you want to access!!!
 
This should work for your virtual machines...
 
Would you like to try the other method of installing in separate partitions?
it will take a couple of hours or so but i can help...:p
 
Definately, I am just experimenting with what I can do at the moment and the more the better. Thank you so much for helping aye. I will also try out the VB stuff you talked about above tonight as well. 
 
Lets just say I have big dreams for someone that doesn't know much. After all this is done, I am going to try putting, Win 7, Mac OS, Ubuntu, Android, RedHat, Solaris.
Going to either buy a bunch of SSD and some Raptor's and go nuts lol. 
 
Started a new thread "Multi Booting OS's - Ideas Needed" so lets continue there as I am going way off target for Partition Troubles lol.
 
My apologies to the Forum Mediators and I won't do it again :)

---

