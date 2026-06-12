---
title: "XP ate my Natty"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-08-19
Last week I bought a new Acer netbook with no operating system on it except for Linpus Linux,  so when I got it home,  the first thing I did was install Natty on it as ext4,  creating a grub-controlled dual boot together with the Linpus there.    That was quite easy and I've since been tailoring Natty to my preferences and adding a few things such as Skype.  There were some startup difficulties which I've been working on,   but basically been making good progress resolving them.   At the same time I also formatted an ntfs partition on it which I labelled 'Data'.   So including 2 swaps and a logical, that made a total of 6 partitions

Then I decided I needed to install an OEM WinXP on it,  so since Windows can only manage max 5 partitions,  I decided to sacrifice the Linpus Linux,  reformat its vacated partition sda1 as ntfs,  and install the XP there.  XP can't actually read the content of ext4 or swap partitions,  but it did recognise my partitons were there,  assigned drive names E: F: and G: to them,  and showed them as unallocated.  It had no problem seeing my two ntfs partitions and I was able to tell it to install XP in partition #1 (sda1) there.   So far so good,  or so it appeared...

XP's installation over-wrote my boot file with its own and I lost by grub boot selection,  but at that point I thought I'd be able to go in on the installation mode with my Natty Live CD and have it generate a new dual boot grub file,  this time with XP and Natty on it.   However when Natty's Live CD installation looked at my HDD,  it saw nothing at all there,  as if the whole drive was empty.   No sign of my Natty or swapfiles nor even of my Data and XP partitions.  Just all blank.  It certainly wasn't all blank in reality because my XP is working OK and it can see the files in my Data partition. As a double-check I tried with Gparted,  but that gave exactly the same completely empty HDD result.

Disbelieving these results I then tried 'testdisk' and here the results were a little more encouraging because this detected and displayed all my previous partitions plus my ntfs Data and XP ones.  You can see these results in my attached "td-after-XP.txt".   In the original testdisk display,  all the lines were green, apparently indicating they were valid for writing,  so I pressed "write".   Unfortunately this had no effect on how Natty's Live CD installation mode or Gparted saw my HDD.  It continued to display there as completely empty.

I find it hard to understand why XP has apparently eaten my Natty installation,  and neither can I make any sense of why Natty and Gparted fail to detect the presence of my XP and Data partitions when they are both alive and well.

My aim is to get back to a grub dual boot situation, this time with Natty as 1st choice and XP as last choice,  but I don't understand boot and partition tables well enough to see how to achieve this.  The suggestion of using Wubi has come up,   but as someone who is trying to slowly migrate completely away from
Windows altogether,   I'm not very keen on the idea of having my Linux dependent on a Windows system.

Any explanatory thoughts on these discrepancies and a possible way forward from here?   It wouldn't be the end of the world if I have to completely reinstall either Natty or XP from scratch,  but for future reference I'd like to get to know how these two adversaries can be married together without having to destroy any one of them.

---

### Post by frankbooth on 2011-08-19
[This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should help you recover GRUB.

Sorry for refering to a guide, but there's no need for me to repeat something that someone already has explained properly :).

---

### Post by coffeecat on 2011-08-19
> **Sleepy-zz-John said:**
> Any explanatory thoughts on these discrepancies and a possible way forward from here?  

Yes.

The most likely explanation is that the XP installer has introduced an inconsistency in the partition table. It is highly prone to doing that when there are Linux logical partitions on the drive - the XP installer gets hopelessly confused. In addition, there is a bug in Gparted which causes it to show the whole drive as unallocated when there is a particular partition table inconsistency, and I'm guessing that when you say that the live CD couldn't see your partitions, you mean Gparted. This doesn't stop either Ubuntu or Windows from using the partitions, but it does prevent you from using Gparted. and is confusing.

So that we can see exactly what the situation is and what to do about it, boot into the live Ubuntu CD, or boot into any Linux live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there and post the contents of the RESULTS.txt between [noparse]```
 and 
```[/noparse] tags for clarity. We can take it from there.

Above all, do **not** attempt to repair grub just yet. Windows overwriting the mbr is a trivial issue which we can deal with later. We need to see what is wrong with your partition table.

By the way, you posted a couple of misconceptions - Windows and 5 partitions being one. We'll pick these up later.

**EDIT**: also - testdisk detecting the sometimes-invisible partitions is not surprising. Don't run testdisk again. If the inconsistency is what I think it is, I will point you to a suitable app to fix it. In fact testdisk sometimes creates another partition table inconsistency that also confuses Gparted in the same way.

---

### Post by Sleepy-zz-John on 2011-08-20
> **coffeecat said:**
> Yes.
The most likely explanation is that the XP installer has introduced an inconsistency in the partition table.... 
Thanks for your promising reply.  Yes, this would fit my symptoms.
> *I'm guessing that when you say that the live CD couldn't see your partitions, you mean Gparted.*
Errr, no, not quite.   I was referring to the tool in Natty Live CD - Install Ubuntu - Allocate Drive Space - Something Else - Allocate drive space,   which doesn't look the same as Gparted at all (though it may incorporate some core elements from Gparted),  so I appeared to be getting the same 'empty' indication from both that and from Gparted;  two different tools.    
> [I] So that we can see exactly what the situation is and what to do about it, boot into the live Ubuntu CD, or boot into any Linux live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there and post the contents....[/I]

Right, but sorry,  not clear where to find this script on that site.  Do I need to download and burn one of the several CDs mentioned there?   I did try entering "boot info script" into the search window there and it came up with all these choices: 
  ```

	 	Windows XP Boot CD

	 	Boot Disk Download

	 	Make a Boot CD

	 	Create XP Boot Disk

	 	MS Dos Boot CD

	 	Boot CD Image

	 	Business Directory Script

	 	Ladys Boot

	 	Writing a Film Script

	 	How to Write a Film Script 
``` 

> * Above all, do **not** attempt to repair grub just yet. Windows overwriting the mbr is a trivial issue which we can deal with later. We need to see what is wrong with your partition table.*
OK,  noted.   Thanks for the warning and this makes sense.
> *By the way, you posted a couple of misconceptions - Windows and 5 partitions being one. We'll pick these up later.*
I'm all ears here :)   It was the XP setup programme that gave me the 5 partitions warning when I initially tried to get it to leave my Linpus Linux intact and install XP in a 7th partition.   Here's how it proposed to allocated drive letters and presented at that initial stage which I abandoned (my added comments in bold italics)
```

E: Partition  [unknown]   5001 MB    <5000 Free>  ***linpus sda1***
   Unpartitioned space    147624 MB  
C:  Partition 2 [Data] NTFS 74102 MB <74869 Free>   ***sda2 for Data, not XP***
G: Partition 4 [unknown]  74067 MB   <74076 Free>   ***sda6 Natty***
H: Partition 5 [unknown]  1764 MB    <1764 Free>   ***sda7 swap***
F: Partition 3 <unknown>  1769 MB    <1769 Free>   ***sda5 swap***
```

> ***EDIT**: also - testdisk detecting the sometimes-invisible partitions is not surprising. Don't run testdisk again. If the inconsistency is what I think it is, I will point you to a suitable app to fix it. In fact testdisk sometimes creates another partition table inconsistency that also confuses Gparted in the same way.*
OK,  noted tks.  At least testdisk gave me some hope that my Natty might still be there,  when everything else was showing blanks!

---

### Post by Sleepy-zz-John on 2011-08-20
> **frankbooth said:**
> [This]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should help you recover GRUB.

Sorry for refering to a guide, but there's no need for me to repeat something that someone already has explained properly :).
Thanks Frank.   But maybe this should be done later because as you see, coffecat is now warning me not to touch grub at this stage,  not until my partition table is fixed.   Grateful your response,  anyway :)

---

### Post by coffeecat on 2011-08-20
> **coffeecat said:**
> So that we can see exactly what the situation is and what to do about it, boot into the live Ubuntu CD, or boot into any Linux live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there and post the contents of the RESULTS.txt between [noparse]```
 and 
```[/noparse] tags for clarity. We can take it from there.

> **Sleepy-zz-John said:**
> Right, but sorry,  not clear where to find this script on that site.  Do I need to download and burn one of the several CDs mentioned there?   I did try entering "boot info script" into the search window there and it came up with all these choices: 
  ```

	 	Windows XP Boot CD

	 	Boot Disk Download

	 	Make a Boot CD

	 	Create XP Boot Disk

	 	MS Dos Boot CD

	 	Boot CD Image

	 	Business Directory Script

	 	Ladys Boot

	 	Writing a Film Script

	 	How to Write a Film Script 
``` 



What link did you click on? :? Not the sourceforge one I posted. (Unless someone's been editing your hosts file.) Try that link again. The instructions for downloading the boot info script and running it are quite clear. Just to be sure you're seeing what I'm seeing, have a look at my (cropped) screenshot.

> **Sleepy-zz-John said:**
> Errr, no, not quite.   I was referring to the tool in Natty Live CD - Install Ubuntu - Allocate Drive Space - Something Else - Allocate drive space,   which doesn't look the same as Gparted at all (though it may incorporate some core elements from Gparted),  so I appeared to be getting the same 'empty' indication from both that and from Gparted;  two different tools.

Two possible explanations for seeing nothing in your hard drive in the installer. I believe the partitioner uses the same parted backend as Gparted so would be affected by the same issue when there is an illegality in the partition table. Also, one page of the installer - I can't remember which atm - is confused by residual RAID metadata on the drive and shows a blank. By that I mean a hard drive that was once used in a RAID assembly but which has been reformatted to be used alone, but some RAID metadata remains. Has your drive ever been configured for use in a RAID? **EDIT**: Forget that! Re-reading your OP I see you're using a netbook. That would something of an achievement to configure a netbook HD for RAID! :) **end_edit**

Once you've posted the boot script output, we can take it from there.

---

### Post by Sleepy-zz-John on 2011-08-20
Please see attached "Results.txt"

More comments when I've had a chance to absorb them myself... 

Looks good though!!   :-D

---

### Post by coffeecat on 2011-08-20
OK, I can see what's wrong now. Your extended partition goes beyond the end of the physical hard drive. From your RESULTS.txt:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR="Red"]625142448[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    71,682,047    71,680,000   7 NTFS / exFAT / HPFS
/dev/sda2         312,576,705   466,200,701   153,623,997   7 NTFS / exFAT / HPFS
/dev/sda3         466,202,624   617,891,839   151,689,216  83 Linux
/dev/sda4         617,892,030   [COLOR="Red"]625,153,409[/COLOR]     7,261,380   f W95 Extended (LBA)
/dev/sda5         617,893,888   621,506,543     3,612,656  82 Linux swap / Solaris
/dev/sda6         621,518,848   625,141,743     3,622,896  82 Linux swap / Solaris

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]


```

This is a common side-effect of using testdisk and is the reason the live CD partitioner can't see your partitions. This was one of the irregularities I was referring to. The other is what the XP installer sometimes does in the presence of Linux logical partitions. That is, it attempts to convert one of the Linux logical partitions into a primary one, but keeping it within the extended partition. Which is completely illegal - and also what confuses parted. My guess is that testdisk repaired that problem and then introduced its own. That's a guess because the output from testdisk that you posted is a nightmare to read. But it's theoretical now, because the immediate issue is to repair the extended going beyond the hard drive end problem.

You need fixparts:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

...developed by forum member srs5694. After you've fixed the partition table, then it will be OK to reinstall grub back into the mbr to be able to boot into Ubuntu. You'll also need to run "sudo update-grub" in Ubuntu once you're back into Ubuntu to get Windows into your grub menu, but we'll come to both grub tasks when the partition table is repaired.

I've got to log off now for several hours and when I do log back in again I might be a bit hazy from a celebration lunch! :wink: So that you are not left alone with fixparts and with repairing grub, I'll ask a couple of my forum friends to keep an eye on this thread and help if necessary. I don't know whether they're online at the moment, but be patient. This is all fixable.

---

### Post by Sleepy-zz-John on 2011-08-20
> **coffeecat said:**
> What link did you click on? :? Not the sourceforge one I posted. (Unless someone's been editing your hosts file.) Try that li nk again. The instructions for downloading the boot info script and running it are quite clear. Just to be sure you're seeing what I'm seeing, have a look at my (cropped) screenshot.
Yeah, sorry!   All OK now.  Totally different result to the sourceforge site I was seeing this morning.  They do play around on the DNSs here in Thailand.  Dunno,  maybe there's a clever way of pocketing commission from pay-per-clicks when they divert a legit DN to some other advertising site??   
> *Two possible explanations for seeing nothing in your hard drive in the installer. I believe the partitioner uses the same parted backend as Gparted so would be affected by the same issue when there is an illegality in the partition table. *
That would make sense.  Just now I'm running on BootMed's Live Maverick CD,  and in 'Places' here I can see all three partitions with their labels  'Natty' 'Data' and 'XP' showing up nicely. I've even been able to mount 'Data' and save a copy of 'Results.txt' there. I didn't think to look in Places last time. Meanwhile GParted continues to display a completely empty HDD.  
> [I] Once you've posted the boot script output, we can take it from there.
Yes, that script has produced an impressive and encouraging 'Results.txt'  Is all that information derived from one boot sector file?  Is just one file held there,  or are there other backups?  

So what now?  Do we need to rewrite the MBR so that I can boot to grub choices instead of directly to Windows?  

I know!  Questions, questions....  maybe I should just shut up and let you do the recommending! 

I notice that sda3/boot/grub/grub.cfg file in 'Results.txt' is going to need rewriting to show WinXP in place of Linpus Linux in sda1.

One of the two swapfiles showing as sda5 and sda6 belongs to my Natty and the other to my deleted Linpus,   but I'm not sure which is which.  When we find out which one belongs to Natty,  then the other one needs to be deleted. 

Anyway many thanks,  and I look forward to your comments on 'Results.txt' in due course

---

### Post by Quackers on 2011-08-20
Just go to the Rodsbooks link that coffeecat gave you, download Fixparts and follow the instructions on that page. Fixparts only really needs to look at the current partitions and then write that info to the disc. A new (corrected) extended partition will be created.

---

### Post by Sleepy-zz-John on 2011-08-20
OK,  thanks Quackers.  I need a bit if time to try and absorb some of that FixParts tutorial first anyway.   I'll come back on here after I've done that and downloaded the prog.  Will probably come up with some questions but could be tomorrow 'cos I'm 6hrs ahead of you folks here.   :smile:

---

### Post by Quackers on 2011-08-20
No problem, take your time :-)
It's quite easy to run Fixparts. The actual fix only takes seconds, but it's always a good idea to read about things first. Get things set in your mind.

---

### Post by Sleepy-zz-John on 2011-08-20
OK,  before I retire tonight,  here's a couple of questions:

I've downloaded gptfdisk-0.7.2-1.src.rpm and found gptfdisk-0.7.2.tar.gz in there.  Now obviously I need to run FixParts on the same PC that has the bad partition table,  and I'm presently running on it from a Live BootMed CD (a pared down version of Maverick).  From this platform I can read and write in my Data partition sda2 and that's where I've saved one copy of gptfdisk-0.7.2-1.src.rpm.   I've saved another copy on an external flash drive.  There's also some limited temporary storage in my Live Maverick's home folder,  but of course that all disappears when I shut down.

So my 1st question is:   Does it matter where I install FixParts?   Can I happily run FixParts from my flash drive if I install it there?  Or how about installing and running it from my Data partition when we're going to be working on the partition table that controls that?   Or is there any reason why I ought to install it in my Maverick's home folder where I'd lose it when I switch off?  

My 2nd question is about fixing my mis-sized extended partition sda4.  Will I have to renumber its incorrect end sector manually,  or will using the 'w' option in FixParts do that for me automatically?

Hope the lunch was good, coffecat.   Since I'm off to sleep now, I won't be looking for any answers until I get up tomorrow morning which will be around 02:30am BST.   Thanks again for all the help.

---

### Post by coffeecat on 2011-08-20
> **Sleepy-zz-John said:**
>  Will probably come up with some questions but could be tomorrow 'cos I'm 6hrs ahead of you folks here.   :smile:

Perhaps that's why you asked a couple of questions in post #9 that I'd already commented on in #8! :wink:

Anyway, as Quackers said, concentrate on the fixparts bit first. When you've run fixparts, run the bootscript again and post the newer RESULTS.txt just to make sure it's done what it needs to do. Then we can concentrate on grub and the mbr and all your questions. I think it would be sensible to do one thing at a time.

---

### Post by coffeecat on 2011-08-20
> **Sleepy-zz-John said:**
> 
I've downloaded gptfdisk-0.7.2-1.src.rpm and found gptfdisk-0.7.2.tar.gz in there.

Wrong one, but not your fault. You need the .deb installer for Ubuntu but I can't find the deb for the 0.7.2 version, only the 0.7.1 here:

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/)

Your need the i386 if you are running a 32-bit version of Ubuntu or amd64 for 64-bit. I think you'll be OK with the slightly earlier 0.7.1. I certainly can't find the deb build for 0.7.2 anywhere - don't know what's going on at sourceforge at the moment. 

> **Sleepy-zz-John said:**
> 
  Now obviously I need to run FixParts on the same PC that has the bad partition table,  and I'm presently running on it from a Live BootMed CD (a pared down version of Maverick). 

Run it from the live CD. Simply copy it to the desktop and double-click on it to install it. It will install to RAM and be lost when you power down, but you only need it for one session. Don't try to run it from a flash drive.

> **Sleepy-zz-John said:**
> 
My 2nd question is about fixing my mis-sized extended partition sda4.  Will I have to renumber its incorrect end sector manually,  or will using the 'w' option in FixParts do that for me automatically?

Fixparts will do it for you automatically. Just follow the instructions in the original link.

---

### Post by srs5694 on 2011-08-20
> **coffeecat said:**
> Wrong one, but not your fault. You need the .deb installer for Ubuntu but I can't find the deb for the 0.7.2 version, only the 0.7.1 here:

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/)

Your need the i386 if you are running a 32-bit version of Ubuntu or amd64 for 64-bit. I think you'll be OK with the slightly earlier 0.7.1. I certainly can't find the deb build for 0.7.2 anywhere - don't know what's going on at sourceforge at the moment. 

The problem is that because of library issues the latest binary builds of GPT fdisk no longer work on a wide variety of distributions. This makes it impractical to host binary builds on Sourceforge. Therefore, I'm no longer using Sourceforge to host Linux binaries of the program. Instead, you should check the OpenSUSE Build Service (OBS) for binary builds for specific distributions. I've got a matrix of options here:

[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

This is described in the README that should be displayed from the 0.7.2 downloads page on Sourceforge.

Another option is to install the software using your distribution's package system. Unfortunately, the last I heard, Ubuntu's highest-numbered GPT fdisk was in the late 0.6.x series, which predates FixParts.

For emergency recovery purposes, an [emergency recovery disc](http://www.rodsbooks.com/gdisk/download.html#emergency) is a good option, provided it includes FixParts. PartedMagic 6.2 (and presumably later) does, but I'm not sure about the others.

---

### Post by Sleepy-zz-John on 2011-08-21
Thanks for the replies last night.  FixParts 0.7.2 looks to have worked.  See my attached "Results-2.txt" and "Gparted4.png".   So easy in the end,  simply pressing 'w' there.  Even my cat could have done it!  :-D 

I did have a bit of a problem opening gptfdisk_0.7.2-1_i386.deb in my Live Natty's ubuntu software center.  It made the center crash a couple of times as a result of which I generated Launchpad bug report #830389,  but it didn't really matter because FixParts still got installed and ran OK. 

So now my overrun problem on the end sector of sda4 has been fixed, what do you recommend as my next step?   Rewrite the MBR?   If so, how do we do that?

Anyway, I'm very happy with this step-by-step slow and considered progress.     Thanks! :D

---

### Post by Quackers on 2011-08-21
Ok so now you want to re-install grub to the mbr of the drive - is that correct?
If so, boot from the Ubuntu live cd/usb and select "try Ubuntu" and when the desktop loads open up a terminal and copy/paste these commands in to it, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
This should report "Finished. No errors".
If the second command gives an error try this line instead ```
sudo grub-install --boot-directory=/mnt /dev/sda
```
and when finished, reboot.
At this stage Ubuntu should boot directly without a grub menu. When it loads open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run. You should see the Windows Loader recognised. When that's finished you can reboot, when you should see the new grub menu giving you the choice of which operating system to boot.

---

### Post by coffeecat on 2011-08-21
Let us know when you've finished the instructions Quackers has posted and if you are then able to boot into both Windows and Ubuntu. Then please do post any remaining questions you have. I know you have plenty but I think some of them may have been answered as you've experienced what you have needed to do.

For what it's worth - the Windows XP and 5 partitions situation. I don't know what the exact error message about 5 partitions was when you tried to install XP on a 7th partition with Linpus Lite. But what this probably was about was the limitation of the mbr partition table setup which you will have on that machine, and about the difficulties Windows has with logical partitions. With an mbr partition table (as opposed to other types of partition table) you are limited to 4 primary partitions. To get around that limitation, one primary partition may be substituted by an extended partition (which is simply a special type of primary partition). The sole purpose of an extended partition is to act as a container for logical partitions, and you can have as many of these as you need or for which there is physical space.

Linux can happily work from and boot from a logical partition. Windows cannot. It is possible to install Windows to a logical partition, but only if it has a separate primary partition with the boot files for booting up. I guess you might have tried to install Windows to a logical partition, and it was objecting to this, except I don't understand what the reference to five is all about. And, as I've mentioned before, the XP installer gets confused by logical partitions when they have Linux filesystems in them.

---

### Post by Sleepy-zz-John on 2011-08-21
Oh, wonderful, Quackers!   Thank both you and coffeecat so much.  Worked a treat and I have both my old Natty and my XP both showing and working on grub now.   

The only other thing I want to do is identify which of the two swapfiles is the one that belongs to my Natty and then delete the other one.     I think I can delete it easily enough,  but how can I identify which one it is?

---

### Post by coffeecat on 2011-08-21
> **Sleepy-zz-John said:**
> 
The only other thing I want to do is identify which of the two swapfiles is the one that belongs to my Natty and then delete the other one.     I think I can delete it easily enough,  but how can I identify which one it is?

It's easy enough to do, but we need to be careful. When you first installed Natty, your root partition was sda6 (a logical partition). After your partition table was subjected to the rigours of the XP installer and then testdisk, it ended up as a primary partition, sda3. This is not directly related to what you need to do to the swap partitions, but I wanted to point this out because the swap partition numbers have changed since you installed XP. Going by your RESULTS.txt file, the swap file for Natty was sda7 with a UUID of 6ec19fda-71f6-4532-8d87-e62648372fcf when Natty was first installed. From your /etc/fstab file:

```
# swap was on /dev/sda7 during installation
UUID=6ec19fda-71f6-4532-8d87-e62648372fcf none            swap    sw              0       0
```

But now, that partition is designated as sda5. From your blkid output in the RESULTS.txt:

```
Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        78BF05741A7B77DD                       ntfs       XP
/dev/sda2        671A9663147460DD                       ntfs       Data
/dev/sda3        19fb8d43-4848-49bf-94b9-a08eec919875   ext4       Natty
/dev/sda5        6ec19fda-71f6-4532-8d87-e62648372fcf   swap       
/dev/sda6        2ee93daa-ed0a-4b91-a86b-b3000ebfc9af   swap       
```


The superfluous partition is sda6 with a UUID of 2ee93daa-ed0a-4b91-a86b-b3000ebfc9af. We haven't seen a RESULTS.txt output since you repaired the partition table. The repair probably won't have changed the partition numbers, but take care. Open Gparted and highlight sda6. Right-click on it and select "Information". If the UUID is showing as 2ee93daa-ed0a-4b91-a86b-b3000ebfc9af, then it is safe to delete or reformat. If you are running this from the live CD, you will need to right-click on the swap partition you are about to remove and choose "swapoff".

One comment: sda6 is only about 1.9GB and right up at the end of your hard drive. You're not going to be able to do anything with that freed space without some manipulation of the other partitions. What did you want the space for?

**EDIT:**

> **Sleepy-zz-John said:**
> Oh, wonderful, Quackers!   Thank both you and coffeecat so much.  Worked a treat and I have both my old Natty and my XP both showing and working on grub now.   

Don't forget to thank srs5694 who wrote the software that healed your partition table after it had been mugged by the XP installer and testdisk! :p Indeed, I would like to add my thanks to srs5694 for stepping into this thread and clarifying where you can download fixparts after I got lost in the labyrinth that is Sourceforge. Unlike Theseus, I did not have the benefit of a ball of string.

---

### Post by Quackers on 2011-08-21
coffeecat, if you did have a ball of string you'd only have played with it :-)

Glad to see that things are running well, Sleepy-zz-John.

Well done to all :-)

---

### Post by coffeecat on 2011-08-21
:)

---

### Post by Sleepy-zz-John on 2011-08-21
Yes indeed,  many thanks too to srs5694 for sorting us out where to find FixParts, and of course for FixParts itself, which is just pure magic :D 

> **coffeecat said:**
> [I]
The superfluous partition is sda6 with a UUID of 2ee93daa-ed0a-4b91-a86b-b3000ebfc9af. We haven't seen a RESULTS.txt output since you repaired the partition table. The repair probably won't have changed the partition numbers, but take care. Open Gparted and highlight sda6. Right-click on it and select "Information". If the UUID is showing as 2ee93daa-ed0a-4b91-a86b-b3000ebfc9af, then it is safe to delete or reformat. If you are running this from the live CD, you will need to right-click on the swap partition you are about to remove and choose "swapoff".[/I] 
Yes, thanks,  I checked that the UUID matched, followed it all carefully,  and deleted sda6 (which was previously sda5) so the space now shows as unallocated.  Here's my current "Results-4.txt". 

My Natty still works,  but... (and I know this may sound a little stupid) it doesn't have any hibernate option now and I can't be 100% sure but I think it did before. What would be the effect on Natty if it couldn't find the swapfile that had been previously associated with it?   Is swap actually used for anything else during normal operation, other than hibernation?    In System Monitor - Resources - Memory and Swap History my Swap is indicating "0 bytes (0.0%) of 0 bytes"  which doesn't look right to me! I've a horrible feeling I've somehow managed to screw up the swapfile Natty is expecting to see.   How can I make Natty see its allocated swapfile correctly?  
[QUOTE]*One comment: sda6 is only about 1.9GB and right up at the end of your hard drive. You're not going to be able to do anything with that freed space without some manipulation of the other partitions. What did you want the space for?*[QUOTE]
That's a good question!   You're right!   I can't do much with the space without rearranging everything.   Since I've got plenty of other spare space there,  at this stage my intention was merely to tidy things up.  I did plan at an earlier stage to have two seperate Data partitions instead of one, and I did try (unsuccessfully) to delete my spare swapfile (then sda5) to make space for that,  but as a 2nd Data partition isn't really a priority,  I'm not pursuing it at the moment.

---

### Post by coffeecat on 2011-08-22
Yes, the swap partition is used for hibernation and since that option has disappeared and you get 0 bytes of 0 bytes in System Monitor something seems to have happened to the swap partition referred to in your /etc/fstab.

You forgot to post your latest RESULTS.txt file. By the way, don't attach it, simply post it between [noparse]```
 and 
```[/noparse] tags like this.

As you see it in the message field:

[noparse]```

your
RESULTS.txt
output

```[/noparse]

As it appears in your post:

```
your
RESULTS.txt
output 
```

It's more convenient to read that way.

---

### Post by Sleepy-zz-John on 2011-08-22
> **coffeecat said:**
> *You forgot to post your latest RESULTS.txt file.* 
Oh, sorry!  Dunno what happened there.  I did upload it and saw it attached during draft but it must've dropped off somewhere!  Here it is Results-4:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    71,682,047    71,680,000   7 NTFS / exFAT / HPFS
/dev/sda2         312,576,705   466,200,701   153,623,997   7 NTFS / exFAT / HPFS
/dev/sda3         466,202,624   617,891,839   151,689,216  83 Linux
/dev/sda4         617,893,887   625,141,743     7,247,857   f W95 Extended (LBA)
/dev/sda5         617,893,888   621,506,543     3,612,656  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        78BF05741A7B77DD                       ntfs       XP
/dev/sda2        671A9663147460DD                       ntfs       Data
/dev/sda3        19fb8d43-4848-49bf-94b9-a08eec919875   ext4       Natty
/dev/sda5        6ec19fda-71f6-4532-8d87-e62648372fcf   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=19fb8d43-4848-49bf-94b9-a08eec919875 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=19fb8d43-4848-49bf-94b9-a08eec919875 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=19fb8d43-4848-49bf-94b9-a08eec919875 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=19fb8d43-4848-49bf-94b9-a08eec919875 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=19fb8d43-4848-49bf-94b9-a08eec919875 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=19fb8d43-4848-49bf-94b9-a08eec919875 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 19fb8d43-4848-49bf-94b9-a08eec919875
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 78BF05741A7B77DD
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6ec19fda-71f6-4532-8d87-e62648372fcf none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 268.443843842 = 288.239382528  boot/grub/core.img                             1
 286.483890533 = 307.609735168  boot/grub/grub.cfg                             1
 224.791263580 = 241.367781376  boot/initrd.img-2.6.38-10-generic              1
 232.826171875 = 249.995198464  boot/initrd.img-2.6.38-11-generic              2
 223.630859375 = 240.121806848  boot/initrd.img-2.6.38-8-generic               2
 223.873355865 = 240.382185472  boot/vmlinuz-2.6.38-10-generic                 1
 236.607730865 = 254.055616512  boot/vmlinuz-2.6.38-11-generic                 2
 268.435039520 = 288.229928960  boot/vmlinuz-2.6.38-8-generic                  1
 232.826171875 = 249.995198464  initrd.img                                     2
 224.791263580 = 241.367781376  initrd.img.old                                 1
 236.607730865 = 254.055616512  vmlinuz                                        2
 223.873355865 = 240.382185472  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  00 00 00 00 00 00 00 fe  |.....,Dc........|
000001c0  ff ff 82 fe ff ff 01 00  00 00 f0 1f 37 00 00 00  |............7...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
 

```

---

### Post by coffeecat on 2011-08-22
Hmm... That looks OK. The correct swap partition is still there and the /etc/fstab entry is fine. Run this terminal command:

```
top
```

Look for the Swap line: about 5-6 lines down from the - er - top. Post that line. If it says:

```
Swap:        0k total,        0k used,        0k free
```

... run this command:

```
sudo swapon -a
```

... and then run top again and see if you get some positive figures instead of the first and third zeroes.

---

### Post by Sleepy-zz-John on 2011-08-22
> **coffeecat said:**
> [I]Hmm... That looks OK. The correct swap partition is still there and the /etc/fstab entry is fine. Run this terminal command:

```
top
```
[/I]
OK,  that 5th line shows all zeros at first: 
```
Swap:        0k total,        0k used,        0k free,   292016K cached
```
> [I]... run this command:
```
sudo swapon -a
```
[/I]
Sorry, no.  We've got some problem here.  That command yields:
```

swapon: /dev/sda5: swapon failed: Invalid argument 
```
> *... and then run top again and see if you get some positive figures instead of the first and third zeroes.*

No,  obviously that delivers all zeroes the same as before

Hmmm...  so we've got /etc/fstab still expecting the swap to be on /dev/sda7 and the swapon command not recognising that it's moved to /dev/sda5.    Some sort of mismatch,  it seems.

---

### Post by coffeecat on 2011-08-22
> **Sleepy-zz-John said:**
> 
Hmmm...  so we've got /etc/fstab still expecting the swap to be on /dev/sda7 and the swapon command not recognising that it's moved to /dev/sda5.    Some sort of mismatch,  it seems.

No, you can ignore the sda7 in that part of /etc/fstab:

```
# swap was on /dev/sda7 during installation
UUID=6ec19fda-71f6-4532-8d87-e62648372fcf     none       swap     sw          0  0
```

(I've reduced the spaces a bit.) The '#' at the beginning of the first of those two lines means that it is "commented" - it is not parsed. It's merely providing a comment for humans. Note that it says "... **was** on /dev/sda7...". The UUID in the next line is the important bit, and:

```
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        78BF05741A7B77DD                       ntfs       XP
/dev/sda2        671A9663147460DD                       ntfs       Data
/dev/sda3        19fb8d43-4848-49bf-94b9-a08eec919875   ext4       Natty
[COLOR="Red"]/dev/sda5        6ec19fda-71f6-4532-8d87-e62648372fcf   swap       [/COLOR]
```

It looks AOK and I'm mystified.

@Quackers, any thoughts? What have I missed? :)

---

### Post by srs5694 on 2011-08-22
It could be that the swap space has become corrupted. You could try this:

```

sudo mkswap -U 6ec19fda-71f6-4532-8d87-e62648372fcf /dev/sda5
sudo swapon -a
free -m

```

I've copied the UUID value from your /etc/fstab file. Alternatively, you can omit the "-U 6ec19fda-71f6-4532-8d87-e62648372fcf" part and then use blkid to find the new UUID and copy-and-paste it into the /etc/fstab file. Also, be *very careful* when you specify the partition (/dev/sda5); you don't want to accidentally create swap space on a filesystem partition!

---

### Post by Sleepy-zz-John on 2011-08-22
Well done!  That seems to have fixed it:

```
:~$ sudo mkswap -U 6ec19fda-71f6-4532-8d87-e62648372fcf /dev/sda5

Setting up swapspace version 1, size = 1806324 KiB
no label, UUID=6ec19fda-71f6-4532-8d87-e62648372fcf
:~$ sudo swapon -a
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1738        486       1252          0         32        227
-/+ buffers/cache:        226       1511
Swap:         1763          0       1763

```

and then from top:

```
Mem:   1780552k total,  830364k used,   950188k free,    81536k buffers
Swap:  1806324k total,       0k used,  1806324k free,   439124k cached

```
OK,  after I've posted this,  I'll try a hibernate and then look at the swap status again

---

### Post by Sleepy-zz-John on 2011-08-22
Yes,  pleased to say hibernation and recovery worked fine,  so once again big thanks to all of you.   

Is there anything else you think I should check before I go back to sleep,  just to make sure there's no other hidden problem lurking around on my HDD?

Come to think of it,  if I had to start all over again and install a new WinXP as dual boot on an existing Natty setup,  I don't know how I could avoid going through all this again.   Yes,  it was fun,  but apart from handling all the valuable recovery tools and tricks,  what have we learnt from the excercise for next time?

---

### Post by coffeecat on 2011-08-23
> **Sleepy-zz-John said:**
> 
Come to think of it,  if I had to start all over again and install a new WinXP as dual boot on an existing Natty setup,  I don't know how I could avoid going through all this again.   Yes,  it was fun,  but apart from handling all the valuable recovery tools and tricks,  what have we learnt from the excercise for next time?

As mentioned earlier in the thread, the XP installer has two unpleasant tricks up its sleeve when confronted with a HD with Linux already installed on it. The first is well-known, which is to overwrite the mbr (overwriting grub) with its own booting code. This is easily fixed with the grub commands from the live CD that Quackers gave you.

The second sometimes happens, but not always, and is less well-known. If there are logical partitions in certain configurations containing Linux filesystems already on the drive, the XP installer, for reasons best known to itself, edits the partition table in a futile attempt to change one of the Linux logical partitions into a primary one. A pointless attempt too, for it doesn't use the partition it tries to change. There is strong circumstantial evidence that that is what happened to you.

If this does happen to you again, don't use testdisk. Testdisk fixes the problem introduced by the XP installer but then introduces one of its own. What you need to do in the logical-turned-into-a-primary scenario is to use srs5694's fixparts.

There's no way that I know of to stop the XP installer getting up to its shenanigans. All you can do is to be aware of the potential problem and use fixparts to mop up the mess.

Here's a bit more when I ran a simulation with the XP installer:

[http://ubuntuforums.org/showpost.php?p=10468958&postcount=42](http://ubuntuforums.org/showpost.php?p=10468958&postcount=42)

Just be glad you are not using the Vista installer: :wink:

[http://ubuntuforums.org/showpost.php?p=10470071&postcount=44](http://ubuntuforums.org/showpost.php?p=10470071&postcount=44)

Instead of simply creating a fixable problem, it nukes your Linux partition!

---

### Post by srs5694 on 2011-08-23
> **coffeecat said:**
> The second sometimes happens, but not always, and is less well-known. If there are logical partitions in certain configurations containing Linux filesystems already on the drive, the XP installer, for reasons best known to itself, edits the partition table in a futile attempt to change one of the Linux logical partitions into a primary one. A pointless attempt too, for it doesn't use the partition it tries to change. There is strong circumstantial evidence that that is what happened to you.

If this does happen to you again, don't use testdisk. Testdisk fixes the problem introduced by the XP installer but then introduces one of its own. What you need to do in the logical-turned-into-a-primary scenario is to use srs5694's fixparts.

The way TestDisk works is to scan a disk for filesystem signatures and create new partitions around them. This operation is not guaranteed to work, and in some cases it can actually generate the *wrong* partitions. Thus, I recommend using TestDisk only as a last-resort measure. To be sure, it's a useful tool, but some people on this forum (not you, coffeecat) seem to reach for it far too often. The result can be additional problems. FixParts, sfdisk, fdisk, and some other tools are better ways to repair most types of partition table damage when the partitions are mostly intact but corrupt in some way. TestDisk's forte is in re-creating partitions that have been completely deleted.

> There's no way that I know of to stop the XP installer getting up to its shenanigans. All you can do is to be aware of the potential problem and use fixparts to mop up the mess.As I understand the XP installer's problem, the XP installer's problem is not likely to recur with the partition table shown in post #26. The reason is that the XP installer's attempt to convert a logical partition into a primary will only occur when there's room for another primary in the partition table; but the partition table in post #26 shows all four primary partitions being used.

One other piece of advice I can give is to back up your partition table. I describe a couple of approaches to doing this under "Final Conversion Thoughts" on [this page.]("http://www.rodsbooks.com/gdisk/mbr2gpt.html#final_thoughts") You can ignore the comments about backing up BSD and GPT data, though. With a backup in hand, you'll be able to quickly restore your partition table should something trash it. Be aware, though, that if you or some tool you run changes the underlying filesystems, the old backup will become dangerous to apply. Thus, you should be sure to keep your backup up to date and don't use it if something goes wrong in a partition resizing operation.

---

### Post by Sleepy-zz-John on 2011-08-23
> **srs5694 said:**
> *.....One other piece of advice I can give is to back up your partition table. I describe a couple of approaches to doing this under "Final Conversion Thoughts" on [this page.]("http://www.rodsbooks.com/gdisk/mbr2gpt.html#final_thoughts") ...... With a backup in hand, you'll be able to quickly restore your partition table should something trash it.*
Thanks, and because that sounds like excellent advice,  I've used your
```
sudo dd if=/dev/sda of=backup.mbr bs=512 count=1
``` to back mine up on a flash drive.    I'm wondering though, if there's any easy way to read that short backed up file since it's mostly code, not ascii.  The few acii characters that I can read there say "GRUB GeomHard DiskRead Error".  I've backed up the MBR on both my computers this way, and both files include these same ascii characters

---

### Post by srs5694 on 2011-08-24
An sfdisk backup is easier to read without special utilities; it's a text file that shows partition start points and lengths in sectors.

sfdisk seems to be able to parse MBR backups to retrieve partition information, but of course only for primary partitions -- extended partition information is stored elsewhere on the disk, so it can't be retrieved from an MBR-only backup.

Edit: The "GRUB GeomHard DiskRead Error" string is part of an error message that GRUB presents if it can't read the hard disk. Its presence is perfectly normal if you've installed GRUB to the disk's MBR.

---

