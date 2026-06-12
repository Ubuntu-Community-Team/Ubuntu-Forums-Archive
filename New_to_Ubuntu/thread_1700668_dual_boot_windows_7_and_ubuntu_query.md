---
title: "dual boot windows 7 and ubuntu query"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by indyeah on 2011-03-05
Hi all

Posting here after a long time.Well i recently bought a dell laptop which has windows 7 installed.i want to dual boot my laptop with ubuntu but i want MBR control to be with windows itself.Is there any way to install ubuntu and then give back MBR control to windows instead of ubuntu??

For the record i have ubuntu installed on my desktop as dual boot with windows xp and i have quite a bit of experience with ubuntu.Just wanted to ask before i take the plunge

thanks in advance

---

### Post by indyeah on 2011-03-05
never mind i will install ubuntu using wubi.....

---

### Post by Megaptera on 2011-03-05
It's perfectly OK to leave Grub in charge of boot & choose W7 or Ubuntu at boot.

You didn't wait long for a reply before going for Wubi!

---

### Post by Mark Phelps on 2011-03-05
Have seen numerous postings about Wubi problems with 10.10 -- sorry, don't have the links available.  So, don't be surprised if that does not work.

Unfortunately, Dell also has a nasty habit of using up all four Primary partitions on your drive -- which is the limit you can have.  Makes it very difficult to install Ubuntu using the traditional partition method because you will have to delete an existing Dell-created partition to make room.

Either way, the FIRST thing you should do, since you have Win7, is use the Backup feature to create and burn a Win7 Repair CD.  If you ultimately decide to do the traditional dual-boot setup, you are likely to end up needing that CD. Plus, that CD gives you a way of restoring the original Wint MBR to your drive -- which will get overwritten when you install Ubuntu using the traditional dual-boot approach.

---

### Post by indyeah on 2011-03-05
> **Mark Phelps said:**
> Have seen numerous postings about Wubi problems with 10.10 -- sorry, don't have the links available.  So, don't be surprised if that does not work.

Unfortunately, Dell also has a nasty habit of using up all four Primary partitions on your drive -- which is the limit you can have.  Makes it very difficult to install Ubuntu using the traditional partition method because you will have to delete an existing Dell-created partition to make room.

Either way, the FIRST thing you should do, since you have Win7, is use the Backup feature to create and burn a Win7 Repair CD.  If you ultimately decide to do the traditional dual-boot setup, you are likely to end up needing that CD. Plus, that CD gives you a way of restoring the original Wint MBR to your drive -- which will get overwritten when you install Ubuntu using the traditional dual-boot approach.


Thanks for all your replies.Actually i did install ubuntu using wubi on my dell on a separate partition of my HDD on my laptop and it worked fine.What i want is ubuntu as my dual boot and honestly i don't want to mess up my windows 7 OS.

i have made 4 separate partitions of my hard drive so let me see.I have windows 7 re installation CD in case something goes wrong.Its just that i don't want grub to take control of MBR,guess there is no way around it and i have to live with it.

---

### Post by indyeah on 2011-03-07
Finally i installed ubuntu as wubi installation.The CD i used had 32 bit ubuntu 10.10 while my laptop is 64 bit.Will i face any perfromance issues running 32 bit OS on 64 bit laptop??

---

### Post by mastablasta on 2011-03-07
> **indyeah said:**
> Finally i installed ubuntu as wubi installation.The CD i used had 32 bit ubuntu 10.10 while my laptop is 64 bit.Will i face any perfromance issues running 32 bit OS on 64 bit laptop??
 
no. you may face performance issues because you are using virtualisation of Operating system. your Wubi is running within windows. and it's all in one large big file.
 
Make sure to turn off the grub updates or you could mess up your boot record and you wont' be able to boot into win7 or Ubuntu. nothing it can't be fixed but why not avoid it on start?
 
after you try it out and if all works in wubi i would suggest to try and make a side by side install (installing Linux on a separate partition in it's own filesystem).
 
why not let GRUB take control? Grub just loads before windows boot loader. if oyu have backup CD of windows you shoul dbe OK as GRUB doesn't really touch windows boot loader. Instead it loads before it and when you select windows in the menu it will just start the windows boot loader. otherwise it will load Linux of your choice.
 
with a windows CD/DVD in your hands (and if needed) you can recover and replace GRUB back with windows loader with a few simple steps.: [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

---

### Post by oldfred on 2011-03-07
While I like grub2, and in most cases it works fine for all versions of windows, and I rarely recommend this.  You can use this third party boot loader to boot windows and it will let you boot Ubuntu.

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

The only users who seem to have issues booting win7 is software with DRM or writes into the sectors just after the MBR. Grub2 has already fixed issues with one DRM software-flexnet as it writes around it. Some HP & Dell software conflicts, but most users just delete that from their system as it is not essential. Then grub2 works without issue.

---

### Post by indyeah on 2011-03-07
thanks mastabasta and oldfred for your replies.

At home i have desktop running windows 7 and ubuntu in dual boot mode with EasyBCD and everything works like a charm.This Dell laptop is fairly new and its like i dont want to mess up in this laptop.Let me try ubuntu some more in wubi before i feel more confident and ready to install windows and ubuntu side by side as you people suggested.

---

### Post by indyeah on 2011-03-08
ok i am ready to install ubuntu side by side windows 7 in dual boot mode.I have few queries to which i need clarification and help.

1. I have made 4 partitions of my hard drive.One partition contains Windows 7,the other 2 has my data stored and last one is empty about 68 GB free.I want to install ubuntu to this empty partition.My question is how many gigs is preferably idea for ubuntu???

2.Secondly during the installation process does it give me the option of how many gigs for swap.My laptop has 3 GB RAM and i read somewhere twice the RAM is ideal for swap.Any suggestions??

My laptop is DELL intel i3 64 bit,3GB RAM,320 GB HDD

Thanks in advance

---

### Post by oldfred on 2011-03-08
If you have used 4 partitions, you have to delete one and convert it to a container for logicals called an extended partition. It can hold many logical partitions.

Swap used to be 2X RAM when  RAM was only 256K or 512K. Now with 3GB you may not use swap much at all. One times RAM (plus a fraction) is required if you hibernate.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Do not let the auto installer install with the newest distribution. If you click on use entire partition it uses entire drive and erases the others. Be sure to back up all important data.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Use gparted to create partitions in advance is the best way. Although you can use manual install and create partitions that way.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by indyeah on 2011-03-08
> **oldfred said:**
> If you have used 4 partitions, you have to delete one and convert it to a container for logicals called an extended partition. It can hold many logical partitions.


thanks for the reply.How do i do this???

As for clicking on auto installer and using entire hard disk i will make sure no to do it.I have an entire partiton empty close to 68 GB,just want to use it for ubuntu.

For shared NTFS partition i already have other partitions which i can easily share with windows and ubuntu.

Swap part is easily understood.

---

### Post by oldfred on 2011-03-08
Just use gparted in advance, then manual install to choose partitions to format and use as / & swap. Or the new version lets you under manual install create partitions. But if you have an NTFS partition you cannot use it. You have to have an extended partition and then put the logicals inside the extended.


Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by indyeah on 2011-03-08
thanks oldfred that cleared lots of doubts

---

### Post by indyeah on 2011-03-09
Finally i installed ubuntu as dual boot with windows..few points worth mentioning.

1. For all those users who are apprehensive about installing ubuntu in dual boot mode its quite easy.You just have to take some precautions here and there.I had one empty partition (68 GB) of my HDD to which i installed ububtu.When installing i choose the 3rd option of manual install and made 10 GB extended partition as ext4 for / and further 10 GB extended partition  as ext3 for /home from my 68 free partiton (in my case it was designated as sda5).

2. Now for 2nd point few people are apprehensive about overwriting their windows 7 MBR and rightly so because they have new laptops/desktops (i was one of them) but there is a solution for it.During the installation process at bottom you have an option for choosing where to write MBR,Dont choose your entire disc as it will overwrite your windows MBR.Just choose the partition you had initially set for ubuntu (in my case sda5).After installation finishes log into windows and download EasyBCD and their add linux in add entry and click on write MBR and you are all set.Now when you boot it will give you option of either windows 7 or linux and yes your windows MBR is control of your machine.

Thats all.I hope i made myself useful a bit in this forum.Some of these things might seem confusing to a newbie but if you experiment a bit its quite easy and lastly when installing ubuntu make sure you have proper backup of your windows and data in case something goes wrong.

---

