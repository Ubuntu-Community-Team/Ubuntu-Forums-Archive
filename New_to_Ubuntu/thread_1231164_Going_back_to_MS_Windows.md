---
title: "Going back to MS Windows"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Flirtilizer on 2009-08-04
I have a notebook that I installed Ubuntu on.  I perfer Ubuntu but some of the programs I really need just wont work.

When I boot with Windows XP Home it doesn't see the drive I wish to install Windows on.  That drive has Ubuntu on it.

I think I recall having the option to format in NTFS when I installed UBUNTU but decided to go with the non-NTFS.  Am I just making that up?  LOL

If there is such an option, I could re-install Ubuntu and this time select NTFS.  Will that work?

Thanks

---

### Post by kpkeerthi on 2009-08-04
No. It won't. NTFS do not support UNIX/LINUX permissions that is critical for the system filesystems.

---

### Post by MelDJ on 2009-08-04
yes. Ubuntu can be installed on ntfs. You probably had chosen to format your drive in the ext3 format. Hence windows cant be installed as windows cant detect ext3

---

### Post by wizard10000 on 2009-08-04
> **MelDJ said:**
> yes. Ubuntu can be installed on ntfs. You probably had chosen to format your drive in the ext3 format. Hence windows cant be installed as windows cant detect ext3

um - no.  Ubuntu cannot be installed on an NTFS partition.

---

### Post by lisati on 2009-08-04
> **Flirtilizer said:**
> I have a notebook that I installed Ubuntu on.  I perfer Ubuntu but some of the programs I really need just wont work.

Have you looked for an [equivalent]("https://help.ubuntu.com/8.04/switching/applications-equivalents.html") or tried them in [Wine]("https://help.ubuntu.com/community/Wine")?
> 
When I boot with Windows XP Home it doesn't see the drive I wish to install Windows on.  That drive has Ubuntu on it.

Common problem that has been dealt with before in the forums. for example: [http://ubuntuforums.org/showthread.php?t=1223488](http://ubuntuforums.org/showthread.php?t=1223488)
> 
I think I recall having the option to format in NTFS when I installed UBUNTU but decided to go with the non-NTFS.  Am I just making that up?  LOL

If there is such an option, I could re-install Ubuntu and this time select NTFS.  Will that work?

Thanks
To be honest, I don't remember: it's more usual to use ext2/ext3/ext4 for Linux

---

### Post by MelDJ on 2009-08-04
thats weird. I formatted my drive with ntfs and ubuntu works like normal

---

### Post by wizard10000 on 2009-08-04
> **MelDJ said:**
> thats weird. I formatted my drive with ntfs and ubuntu works like normal

wubi doesn't count  ;)

---

### Post by MelDJ on 2009-08-04
o..hehehe i see:oops:

---

### Post by scottuss on 2009-08-04
Yes you are most likely using Wubi, in which case your hard disk is NTFS formatted but the Ubuntu installation sits inside a single virtual hard disk file which is certainly not formatted as NTFS.

---

### Post by MelDJ on 2009-08-04
yes its installed by wubi. is there away i could change ubuntu so that i don't need to have my windows disk connected while I boot into ubuntu?
:confused:

---

### Post by wizard10000 on 2009-08-04
> **MelDJ said:**
> yes its installed by wubi. is there away i could change ubuntu so that i don't need to have my windows disk connected while I boot into ubuntu?
:confused:

Not without repartitioning and reinstalling, I'm afraid.

---

### Post by CatKiller on 2009-08-04
> **MelDJ said:**
> is there away i could change ubuntu so that i don't need to have my windows disk connected while I boot into ubuntu?

I've not used Wubi, but [this]("http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/") might help.

---

### Post by harry2006 on 2009-08-04
wubi runs on a virtual disk ...and the claim saying ubuntu runs on ntfs is wrong...
i agree with @scottus...
@meldj...i guess not...you cant do that.

---

### Post by Paddy Landau on 2009-08-04
> **Flirtilizer said:**
> When I boot with Windows XP Home it doesn't see the drive I wish to install Windows on.  That drive has Ubuntu on it.
I don't quite understand the query.

Are you wanting to see your Ubuntu partition from Windows?

If so, then try [Ext2FSD]("http://www.ext2fsd.com/"). If not, please ignore this post.

---

### Post by Flirtilizer on 2009-08-05
> **MelDJ said:**
> yes. Ubuntu can be installed on ntfs. You probably had chosen to format your drive in the ext3 format. Hence windows cant be installed as windows cant detect ext3

So can I re-install Ubuntu, and choose NTFS?

Or is there no way to ever install Windows to my hard drive again?  Surely that can't be true.  :)

---

### Post by credobyte on 2009-08-05
> **Flirtilizer said:**
> So can I re-install Ubuntu, and choose NTFS?

Or is there no way to ever install Windows to my hard drive again?  Surely that can't be true.  :)

No, you can't install Ubuntu on NTFS ( that's the same as if you would want to install XP on ext3 ). All you can do is to resize your main partition and create a new NTFS partition for Windows.

---

### Post by 3rdalbum on 2009-08-05
> **Flirtilizer said:**
> Or is there no way to ever install Windows to my hard drive again?  Surely that can't be true.  :)

I don't think it's very clear what you actually want to do (what you want the end-result to be), so I'll guess.

If you want a dual-boot with Windows, then the easiest option is to use the Gparted live CD (or live USB) to erase the hard disk and make it NTFS format, then install Windows, then install Ubuntu. In the Ubuntu installer, use the "resize a partition" option; it will shrink the NTFS partition and put its own ext3 or ext4 partition in the freed space.

Make sure you **drag the slider to the left** to give Ubuntu some space. This is on the screen which shows the two bar diagrams. The slider is on the bottom diagram.


If you just wanted Windows only, then use the Gparted live CD/live USB to erase the hard disk to NTFS format only.

The Windows installer will only see fat32 and NTFS partitions, not ext3 partitions. Known bug :-)

---

### Post by Flirtilizer on 2009-08-05
> **3rdalbum said:**
> I don't think it's very clear what you actually want to do (what you want the end-result to be), so I'll guess.

If you want a dual-boot with Windows, then the easiest option is to use the Gparted live CD (or live USB) to erase the hard disk and make it NTFS format, then install Windows, then install Ubuntu. In the Ubuntu installer, use the "resize a partition" option; it will shrink the NTFS partition and put its own ext3 or ext4 partition in the freed space.

Make sure you **drag the slider to the left** to give Ubuntu some space. This is on the screen which shows the two bar diagrams. The slider is on the bottom diagram.


If you just wanted Windows only, then use the Gparted live CD/live USB to erase the hard disk to NTFS format only.

The Windows installer will only see fat32 and NTFS partitions, not ext3 partitions. Known bug :-)

Sorry it wasn't clear, the OP said I wanted to go back to windows, yes I want to install windows on my drive and only windows.  

What is Gparted Live?  hopefully a google will turn it up.

---

### Post by Paddy Landau on 2009-08-05
> **Flirtilizer said:**
> I want to install windows on my drive and only windows.
In that case, you don't want gparted or anything to do with Ubuntu.

You only want your Windows installation disk.

Allow the Windows installation disk to entirely wipe your hard drive when it installs Windows.

---

### Post by MelDJ on 2009-08-05
> **Flirtilizer said:**
> So can I re-install Ubuntu, and choose NTFS?

Or is there no way to ever install Windows to my hard drive again?  Surely that can't be true.  :)

if in wubi yes...as i have learnt:D

---

### Post by Flirtilizer on 2009-08-05
> **Paddy Landau said:**
> In that case, you don't want gparted or anything to do with Ubuntu.

You only want your Windows installation disk.

Allow the Windows installation disk to entirely wipe your hard drive when it installs Windows.

Hi Paddy, thanks but I'm totally sure that is wrong.  :)  Windows can't even see the drive formatted in ext3

---

### Post by rob2uk on 2009-08-05
> **Flirtilizer said:**
> Hi Paddy, thanks but I'm totally sure that is wrong.  :)  Windows can't even see the drive formatted in ext3

Windows can't see it, or the Windows installer can't?

If it's the latter, you most likely have a SATA hard drive which the installer needs special drivers for.

There are a couple of ways around it, but it's not something I've ever dealt with personally, so I'll leave it to someone with a bit more experience :)

---

### Post by Flirtilizer on 2009-08-05
> **rob2uk said:**
> Windows can't see it, or the Windows installer can't?

If it's the latter, you most likely have a SATA hard drive which the installer needs special drivers for.

There are a couple of ways around it, but it's not something I've ever dealt with personally, so I'll leave it to someone with a bit more experience :)

No, it is not a SATA drive.  It's a Sony VAIO that I purchased around 2002.  I don't think SATA was even out.  Since its a Sony it has the confounded setup disk, if I try to use anything else, can't find the drivers for this antique.  :)

Windows cannot see a drive formatted in etc3.  I downloaded the iso for the file someone mentioned before.  Thanks.

---

### Post by Paddy Landau on 2009-08-05
Are you using a normal Windows installation file (you bought Windows separately from the computer), or are you using the installation disk that Sony gave with the computer?

If it's the installation disk that Sony gave you, then most likely it needs a small, usually hidden, partition that sits on your hard drive. Unfortunately, you'd have wiped that partition when you installed Ubuntu. In that case, you'd need to contact Sony for the proper factory installation disk, which will recreate that hidden partition.

If it's a separately-bought Windows CD, then I don't understand why it won't see the disk.

---

### Post by NOTAGEEK on 2009-08-05
> **Paddy Landau said:**
> In that case, you don't want gparted or anything to do with Ubuntu.
 
You only want your Windows installation disk.
 
Allow the Windows installation disk to entirely wipe your hard drive when it installs Windows.
 
> **MelDJ said:**
> if in wubi yes...as i have learnt:D
 
> **Flirtilizer said:**
> Hi Paddy, thanks but I'm totally sure that is wrong. :) Windows can't even see the drive formatted in ext3
 
> **rob2uk said:**
> Windows can't see it, or the Windows installer can't?
 
If it's the latter, you most likely have a SATA hard drive which the installer needs special drivers for.
 
There are a couple of ways around it, but it's not something I've ever dealt with personally, so I'll leave it to someone with a bit more experience :)
 
> **Flirtilizer said:**
> No, it is not a SATA drive. It's a Sony VAIO that I purchased around 2002. I don't think SATA was even out. Since its a Sony it has the confounded setup disk, if I try to use anything else, can't find the drivers for this antique. :)
 
Windows cannot see a drive formatted in etc3. I downloaded the iso for the file someone mentioned before. Thanks.
 
 
 
 
i dont know if i am understanding the quoted posts above **BUT**:
 
i had a brand new pc (now abt a month old) that never had anything on the hdd but ubuntu 9.04... **this pc has a 320gb sata hdd**...
 
as of yesterday this pc now only has 64 bit win vista ult installed...
 
i put in the win install disc and just a few pages into the install **windows saw the ext3** **partitions fine**... all i did to finish the win only install was **delete the existing partitions** and give win the whole 320 gb of **sata** drive for install...
 
works just fine...

---

### Post by Tux118 on 2009-08-05
> **Flirtilizer said:**
> I have a notebook that I installed Ubuntu on.  I perfer Ubuntu but some of the programs I really need just wont work.


Easy, just install [wine]("http://www.winehq.org/") software and you can run all of your windows programs. If you need the .NET framework, just install [mono]("http://www.go-mono.com").

---

### Post by Seed! on 2009-08-05
> **Flirtilizer said:**
> No, it is not a SATA drive.  It's a Sony VAIO that I purchased around 2002.  I don't think SATA was even out.  Since its a Sony it has the confounded setup disk, if I try to use anything else, can't find the drivers for this antique.  :)

Windows cannot see a drive formatted in etc3.  I downloaded the iso for the file someone mentioned before.  Thanks.
  Boot from the Ubuntu livecd, then start Gparted and format your entire harddrive as NTFS. 
Thats it now windows installation cd should detect it, I had similar problem like this before. :)

---

### Post by Paddy Landau on 2009-08-05
> **Tux118 said:**
> Easy, just install [wine]("http://www.winehq.org/") software and you can run all of your windows programs. If you need the .NET framework, just install [mono]("http://www.go-mono.com").
Wine doesn't work on all Windows programs, and when it does work, it doesn't work properly on all of them.

---

### Post by longtom on 2009-08-05
> **Tux118 said:**
> Easy, just install [wine]("http://www.winehq.org/") software and you can run all of your windows programs. If you need the .NET framework, just install [mono]("http://www.go-mono.com").

wow - that would be graet.  Just use wine and mono and all windows programs run.  
That would help to get Linux going - unfortunately it isn't quite that simple....

---

### Post by Mark Phelps on 2009-08-05
> **Paddy Landau said:**
> Wine doesn't work on all Windows programs, and when it does work, it doesn't work properly on all of them.

+1

Don't know why the Wine fans keep pushing the myth that Wine runs everything that MS Windows runs.  I tried for six months myself, and not a single program ran properly.  Half wouldn't even install correctly. And the other half failed to work properly. Which is when I started to learn how to use Linux apps to do everything I was used to doing in MS Windows.

I generally tell folks to check the CodeWeavers Application Compability database for the apps and versions they want to use -- before installing Wine.  After all, if Wine ran everything, they wouldn't need a compatibility database, now would they!

---

### Post by Paddy Landau on 2009-08-05
> **Mark Phelps said:**
> ... check the CodeWeavers Application Compability database for the apps and versions they want to use
Well, with something like [PlayOnLinux]("http://www.playonlinux.com/"), it can be easier just to try it out for yourself (hardware can make a difference).

Also have a look at the table of [Linux equivalent programs to Windows]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html"). It's somewhat dated (2007), but it gives a good idea of the size of the range.

This forum is another good source of up-to-date suggestions.

I've managed to replace all of my Windows programs with Ubuntu-compatible ones, apart from one that does work under Wine and I've been too busy to convert it to the open-source equivalent.

---

### Post by MichealH on 2009-08-05
Bit of Advice when going from EXT3 to NTFS in Windows Vista Install


[LIST]
[*]Delete parttion
[*]Create New
[*]Format as NTFS
[/LIST]
Simples :D

---

### Post by NOTAGEEK on 2009-08-06
> **NOTAGEEK said:**
> i dont know if i am understanding the quoted posts above **BUT**:
 
i had a brand new pc (now abt a month old) that never had anything on the hdd but ubuntu 9.04... **this pc has a 320gb sata hdd**...
 
as of yesterday this pc now only has 64 bit win vista ult installed...
 
i put in the win install disc and just a few pages into the install **windows saw the ext3** **partitions fine**... all i did to finish the win only install was **delete the existing partitions** and give win the whole 320 gb of **sata** drive for install...
 
works just fine...
 
> **MichealH said:**
> Bit of Advice when going from EXT3 to NTFS in Windows Vista Install
 

[LIST]
[*]Delete parttion
[*]Create New
[*]Format as NTFS
[/LIST]Simples :D
 
 
your #2 and 3 bullets are unnecessary---windows does a fine job with them...

---

### Post by theozzlives on 2009-08-06
Why go through a whole install??? Just use GParted to manipulate your partitions.

---

### Post by Paddy Landau on 2009-08-07
> **theozzlives said:**
> Why go through a whole install??? Just use GParted to manipulate your partitions.
The OP clarified ([post 18]("http://ubuntuforums.org/showthread.php?p=7736427#post7736427")) that he currently has only Ubuntu, but instead wants only Windows.

---

### Post by PatrickVogeli on 2009-08-08
What a messy post!!

To reinstall windows on top of Ubuntu, you just have to pop in the windows installer CD. When it comes to partitioning, it will detect some unknown partition. Delete all of them, so that it only shows unpartitioned space, and then install Windows over it (it will take care of creating a partition and so, don't worry).

If you get an error from the installer telling it doesn't find any harddrive and asking you to press F3 to leave, you'll have to investigate why it doesn't find your HDD. It HAS NOT to do with ubuntu or its format, don't investigate that way.

---

