---
title: "Uninstall Ubuntu from Dual Boot XP, with no install disks"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by TracyA on 2011-05-20
Hi All, 
I installed Ubuntu as a dual boot with my XP (I had another thread asking about my XP's corrupt IP settings and installing Ubuntu alongside) .. Anyway, I've tried it for a few days and decided I just don't have the time or energy or dedication right now, to learn a new platform. So, I need to uninstall Ubuntu from my dual boot XP. I want to then do a clean install of Win 7 thus getting rid of XP as well. 
I've been googling, and most of the uninstall-and-go-back-xp instructions that I've found involve the Windows XP install disks which I do not have. 
Other instructions seem pretty complicated, (I've never even heard of a Grub) and don't forget I have no internet on the XP side of my machine as my IP settings are corrupted so therefore if I need to download any clean-up program to run on the XP side, I can either download it from the ubuntu side,or I have another computer here and I can put it on the external HDD to transfer it over. 

Ok Hope there's help here who's logged in, because I'm hoping to do this tonight. !

Thanks in advance! 
Tracy.

---

### Post by josephmills on 2011-05-20
I really don't mean to sound like a dork or any thing but have but have you tried Zorin yet?[http://distrowatch.com/table.php?distribution=zorin](http://distrowatch.com/table.php?distribution=zorin) (I hate to see someone leave the open source scene ) also why is windoz saying your ip is tainted ? I am sure that the windoz crew could help with that  so you dont have internet with windoz xp? when you boot into safe mode with networking do you get it then. I am sorry but this is the first time that I have heard of xp not allowing you to connect unless it is a pirate copy (that could have some root kits on it also )I hope that you get it worked out. is it you ip because you can change that also is it the mac-address that might be causing this to happen also? have you ran tracert in windoz to see if it get past you isp where is it getting redirected? at any rate please post as I am super curious thanks 
Joseph

---

### Post by TracyA on 2011-05-20
Hi Joseph, 
My TCP/IP settings were corrupted by a virus,and I worked for 3 days trying to get them back. they are gone and Windows will not let me do anything to define them. A reinstall of Windows is absolutely necessary. I have no doubt about this. I just thought I'd try out Ubuntu first just out of curiosity. My question in the other thread was whether installing Ubuntu as a dual boot would make it's own IP settings so I would have internet while trying out Ubuntu... The answer turned out to be yes .. (my other thread is here [http://ubuntuforums.org/showthread.php?t=1759195](http://ubuntuforums.org/showthread.php?t=1759195) )

No offense but I am so tired ... really tired..  of dealing with that problem and I've backed up all my files, and ready now to do that XP to Win7 change.
I need help now to uninstall Ubuntu so I can leave my XP and then clean install win7. 
Thanks!

---

### Post by Hedgehog1 on 2011-05-20
Here is where you can download the XP home repair disks:

[http://www.allbootdisks.com/download/xphome.html]("http://www.allbootdisks.com/download/xphome.html")

Here is where you can download the XP Pro repair disks:

[http://www.allbootdisks.com/download/xppro.html]("http://www.allbootdisks.com/download/xppro.html")


***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-20
> **TracyA said:**
> Hi Joseph, 
My TCP/IP settings were corrupted by a virus,and I worked for 3 days trying to get them back. they are gone and Windows will not let me do anything to define them. A reinstall of Windows is absolutely necessary. I have no doubt about this. I just thought I'd try out Ubuntu first just out of curiosity. My question in the other thread was whether installing Ubuntu as a dual boot would make it's own IP settings so I would have internet while trying out Ubuntu... The answer turned out to be yes .. (my other thread is here [http://ubuntuforums.org/showthread.php?t=1759195](http://ubuntuforums.org/showthread.php?t=1759195) )

No offense but I am so tired ... really tired..  of dealing with that problem and I've backed up all my files, and ready now to do that XP to Win7 change.
I need help now to uninstall Ubuntu so I can leave my XP and then clean install win7. 
Thanks!
Hi, I did lot of research and found this link about half way down the page it says you can restore win 98 and xp without a disk. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by josephmills on 2011-05-20
> **TracyA said:**
> Hi Joseph, 
My TCP/IP settings were corrupted by a virus,and I worked for 3 days trying to get them back. they are gone and Windows will not let me do anything to define them. A reinstall of Windows is absolutely necessary. I have no doubt about this. I just thought I'd try out Ubuntu first just out of curiosity. My question in the other thread was whether installing Ubuntu as a dual boot would make it's own IP settings so I would have internet while trying out Ubuntu... The answer turned out to be yes .. (my other thread is here [http://ubuntuforums.org/showthread.php?t=1759195](http://ubuntuforums.org/showthread.php?t=1759195) )

No offense but I am so tired ... really tired..  of dealing with that problem and I've backed up all my files, and ready now to do that XP to Win7 change.
I need help now to uninstall Ubuntu so I can leave my XP and then clean install win7. 
Thanks!


You need to care of that virus I will make a bet that it is hidden deep now and it could be a multipliable kernel virus if you really want to can you erase your hd then do a fresh install of win 7? I would also do a rkhunter after I installed 7 as I would think that a virus with that power would stay with you I would use gparted to delete and my win xp side then install the 7 over my hd of ubuntu wait one min I would NEVER install windoz over ubuntu!!!!!!!!! I am sorry but I can not help you maybe you could try a windoz forum sorry best of luck ;)

---

### Post by Hedgehog1 on 2011-05-20
If you boot into XP, you can also change the MBR to boot only XP by running this command at the DOS prompt:

```
FDISK /MBR
```

Once are are booting into XP only, you can delete the Ubuntu partitions:


[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-20
As a side note, Windows 7 is the nicest MS Windows yet.

In the end, you need to use the OS that works for you.


***The Hedge***

:KS

---

### Post by jtarin on 2011-05-21
You can keep Ubuntu and install Win7 over XP if they are on separate partitions.Installing Win7 will wipe out Grub2. This is easily remedied by using the Windows bootloader to boot Ubuntu by chainloading Grub2. Look to my signature for the answer....EasyBCD. I have been dual-booting Win and Linux,BSD,Qnx for more than a few years.This will give you time to learn Linux and still have your Windows.

---

### Post by Allavona on 2011-05-21
Agreed with all replies. If your machine is capable of running 7, do so. XP is obsolete and tired software. 7 will amaze you actually. It's really quite nice and Aero is impressive to say the least.

You need no disc for an uninstall, if your just removing OS's. I'm assuming you have a LEGAL Windows 7 disc...Just insert that into your cd/dvd drive and start up. Format the entire drive and install.

jtarin mentioned keeping Ubuntu, if their on separate partitions, this is good to for the reasons already described in earlier posts. EasyBCD is great for manipulating the windows bootloader. 

With all that said, Hedgehog1 has hit the nail on the head:

> In the end, you need to use the OS that works for you.

---

### Post by TracyA on 2011-05-21
Hi All,
Well I did get Ubuntu completely off the computer, Hedge thanks so much for your screenshots that was great. love screenshots.. you're awesome to go to the effort! 
... the only thing is that there is no FDISK command in XP. so, I ended up using the instructions here: [http://ubuntuforums.org/archive/index.php/t-940130.html](http://ubuntuforums.org/archive/index.php/t-940130.html) 

What I did find though is that after deleting the partition, it showed as unallocated but I still had to use Partition Master to assign that freespace back into my XP partition.. 

I've installed Win7 now, formatting the drive within the install. Everything went smooooooth  :cool: 
Yes I like Win 7,  I've used Win 7 on my kids' computers and although it's very different than XP I like it. 

The one I've been using in the interim while my net was down on the XP is my daughter's old Vista and it is TERRIBLE. Hated Vista from Day One (didn't everyone?) I think I'll wipe out that one and install 7 on it as well. 
Maybe that will be the computer I give Ubuntu a better effort, and that Zorin looks like a nice baby-step towards the Linux world. I had already deleted half of this computer in anticipation of installing Win7, so I had some room to put Ubuntu as a dual boot. ..  I can't run it alongside my OS on this computer because my disk is only 70GB. (Don't laugh at my small disk, it's not the size it's how you use it LOL ... I got a huge external HDD that will rock your world though LMAO) 

If I get out the cleaner and the canned air I might even be able to convince myself I got a new computer!(well except for the stupid trackpoint-nipple thing don't ever think of getting a computer with that, it is truly awful)

Thanks again for all your help!
Tracy :)

---

### Post by Hedgehog1 on 2011-05-21
> **TracyA said:**
> What I did find though is that after deleting the partition, it showed as unallocated but I still had to use **Partition Master** to assign that freespace back into my XP partition.. 

Tracy,

Using Partition Master (or another tool like it) was a perfectly appropriate thing to do because Disk Manager in XP does not offer the 'expand a partition' feature.

Windows 7 version of Disk Manager does offer the 'expand a partition' feature, so that is one less thing you will need Partition Master for.

Glad you are operational again!

***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-21
> **TracyA said:**
> Hi All,
Well I did get Ubuntu completely off the computer, Hedge thanks so much for your screenshots that was great. love screenshots.. you're awesome to go to the effort! 
... the only thing is that there is no FDISK command in XP. so, I ended up using the instructions here: [http://ubuntuforums.org/archive/index.php/t-940130.html](http://ubuntuforums.org/archive/index.php/t-940130.html) 

What I did find though is that after deleting the partition, it showed as unallocated but I still had to use Partition Master to assign that freespace back into my XP partition.. 

I've installed Win7 now, formatting the drive within the install. Everything went smooooooth  :cool: 
Yes I like Win 7,  I've used Win 7 on my kids' computers and although it's very different than XP I like it. 

The one I've been using in the interim while my net was down on the XP is my daughter's old Vista and it is TERRIBLE. Hated Vista from Day One (didn't everyone?) I think I'll wipe out that one and install 7 on it as well. 
Maybe that will be the computer I give Ubuntu a better effort, and that Zorin looks like a nice baby-step towards the Linux world. I had already deleted half of this computer in anticipation of installing Win7, so I had some room to put Ubuntu as a dual boot. ..  I can't run it alongside my OS on this computer because my disk is only 70GB. (Don't laugh at my small disk, it's not the size it's how you use it LOL ... I got a huge external HDD that will rock your world though LMAO) 

If I get out the cleaner and the canned air I might even be able to convince myself I got a new computer!(well except for the stupid trackpoint-nipple thing don't ever think of getting a computer with that, it is truly awful)

Thanks again for all your help!
Tracy :)
Hi, glad it all worked out.

---

