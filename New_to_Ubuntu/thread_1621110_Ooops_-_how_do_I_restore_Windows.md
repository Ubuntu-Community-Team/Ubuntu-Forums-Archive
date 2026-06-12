---
title: "Ooops - how do I restore Windows?"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by theaveng on 2010-11-13
I have a Compaq Presario 700 laptop with Ubuntu and want to restore XP, but the restore CD keeps giving me an error:

"Not enough free space"

I thought maybe the hard drive was full (with ubuntu) so I formatted it.  Now the c: drive is blank, but I'm still getting the same error.  How do I get windows back on this machine?

---

### Post by Paqman on 2010-11-13
You may still have the drive partitioned from when you installed Ubuntu. Make sure you delete all the other partitions and you should be able to install Windows no problem.

---

### Post by theaveng on 2010-11-13
I don't see any partitions, except the FAT32 one.

---

### Post by shadow120 on 2010-11-13
from the ubuntu live cd go to gparted and under device create new partion table.  this will take everything off the drive and windows should install

---

### Post by theaveng on 2010-11-14
> **shadow120 said:**
> from the ubuntu live cd go to gparted and under device create new partion table.  this will take everything off the drive and windows should install  Nope.  That didn't work either.  Still getting the same "not enough free space" error from the Compaq Windows Restore CD.

---

### Post by coffeecat on 2010-11-14
Maybe it's simply looking for a NTFS partition big enough and when it doesn't find one gives you that message. Perhaps the Compaq engineers only anticipated a shrunken NTFS partition, not an absent one, when they coded the restore CD. So, to the CD, an absent NTFS partition is the same thing as one too small.

Now that you've created a new partition table you have a completely unallocated HD. Boot up the live Ubuntu CD and create one big NTFS partition in the unallocated space with Gparted. And then see if the Compaq restore CD will be happy with that.

---

### Post by jrev on 2010-11-14
> **coffeecat said:**
> Maybe it's simply looking for a NTFS partition big enough and when it doesn't find one gives you that message. Perhaps the Compaq engineers only anticipated a shrunken NTFS partition, not an absent one, when they coded the restore CD. So, to the CD, an absent NTFS partition is the same thing as one too small.

Now that you've created a new partition table you have a completely unallocated HD. Boot up the live Ubuntu CD and create one big NTFS partition in the unallocated space with Gparted. And then see if the Compaq restore CD will be happy with that.

Not too big a partitionso that you can use the rest of the HD to install Ubuntu

---

### Post by coffeecat on 2010-11-14
> **jrev said:**
> Not too big a partitionso that you can use the rest of the HD to install Ubuntu

A very good point. :) 

@theaveng, how big is the HD in your Compaq?

---

### Post by apollothethird on 2010-11-14
> **theaveng said:**
> I have a Compaq Presario 700 laptop with Ubuntu and want to restore XP, but the restore CD keeps giving me an error:

"Not enough free space"

I thought maybe the hard drive was full (with ubuntu) so I formatted it.  Now the c: drive is blank, but I'm still getting the same error.  How do I get windows back on this machine?

Try:

fdisk /mbr

To repair the boot record for the Wndows Install utility.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by theaveng on 2010-11-15
Where do I find fdisk?  In the Ubuntu term/ CLI?

---

### Post by Mark Phelps on 2010-11-15
Did this Recovery CD come with the PC, or did you create it yourself using the option to create Recovery CDs?

Asking because, from what I read, that machine requires a SET of CDs, not just one, to do a complete restore.

If you have only one, then it's most probably going to look for a Recovery partition on the drive -- and it that doesn't exist, you won't be able to do a recovery.

---

### Post by apollothethird on 2010-11-16
> **theaveng said:**
> Where do I find fdisk?  In the Ubuntu term/ CLI?

It appears that fdisk isn't shipped with the later versions of Windows.  There are other programs and third party packages that will replace Microsoft's "fdisk /mbr" Master Boot Record repair utility.

I just googled "mbr repair" and find lots of resolutions.  Take a look at: 

How to repair MBR on Windows 7:
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

If those steps doesn't help or you can't find a solution by googling "mbr repair" ( [http://www.google.com/#hl=en&expIds=17259,17291,27606,27615,27629&sugexp=ldymls&xhr=t&q=mbr+repair&cp=6&pf=p&sclient=psy&aq=0&aqi=g5&aql=&oq=mbr+re&gs_rfai=&pbx=1&fp=a2739d2276f2dcad](http://www.google.com/#hl=en&expIds=17259,17291,27606,27615,27629&sugexp=ldymls&xhr=t&q=mbr+repair&cp=6&pf=p&sclient=psy&aq=0&aqi=g5&aql=&oq=mbr+re&gs_rfai=&pbx=1&fp=a2739d2276f2dcad) ) let me know and I'll take some time when I get a chance and test some of the specifics.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by wilee-nilee on 2010-11-16
> **Mark Phelps said:**
> Did this Recovery CD come with the PC, or did you create it yourself using the option to create Recovery CDs?

Asking because, from what I read, that machine requires a SET of CDs, not just one, to do a complete restore.

If you have only one, then it's most probably going to look for a Recovery partition on the drive -- and it that doesn't exist, you won't be able to do a recovery.

Op read this post carefully there are some good points here. The **MBR** is more then likely not the problem here.

My recovery XP OEM reinstall set from acer is 3 cd's. I have a acer single install ISO that fits on one.

---

### Post by soldier1st on 2010-11-16
i suspect that you got a recovery cd which will not allow you to recover windows as the layout of the partition structure is not the same as when you first got the pc as at that time you had windows and it was using up the whole drive that it is checking for any changes which it is detecting and will not allow you to fix it.

---

### Post by apollothethird on 2010-11-16
> **wilee-nilee said:**
> Op read this post carefully there are some good points here. The **MBR** is more then likely not the problem here.

My recovery XP OEM reinstall set from acer is 3 cd's. I have a acer single install ISO that fits on one.

Hi, Wilee-nilee.  Actually I don’t think the recovery CD’s will work when Windows can’t access the boot table.  I had this problem once (it was years ago) and running fdisk /mbr fixed it.  I was going from the lilo boot manager at the time.

A person shouldn’t have to depend on recovering a factory install to install Windows.  Many of my clients prefer a vanilla installation of Windows over what the factory provides.  If he can’t just choose and install either Windows or Linux on his computer, I would consider it a problem.  I’m almost certain that repairing the mbr will make the disk available to a fresh Windows install.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by mastablasta on 2010-11-17
you know what the problem is? - you deleted your system restore partition when installing Ubuntu or if you listened an advice of the users here gave you. my guess is that recovery disk doesn't find space on that partition because partition doesn't exists.
 
AFAIK Presario 700 is better of with Ubuntu, are you trying to sell it or what?

---

### Post by wilee-nilee on 2010-11-17
> **apollothethird said:**
> Hi, Wilee-nilee.  Actually I don’t think the recovery CD’s will work when Windows can’t access the boot table.  I had this problem once (it was years ago) and running fdisk /mbr fixed it.  I was going from the lilo boot manager at the time.

A person shouldn’t have to depend on recovering a factory install to install Windows.  Many of my clients prefer a vanilla installation of Windows over what the factory provides.  If he can’t just choose and install either Windows or Linux on his computer, I would consider it a problem.  I’m almost certain that repairing the mbr will make the disk available to a fresh Windows install.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

I would agree with the nix of the factory install, thats why I have a straight install ISO from acer. I think it is a cd the OP is using as suggested that would access a recovery partition or a backup. The home version doesn't have the backup installed but it is on the XP home cd for install, you just have to know where it is and how to install it.

The MBR isn't ever accessed with a install cd until you install or recover, it sounds like a wiped XP.

Op post the bootscript in my signature in code tags this will tell us exactly whats in the mbr basically and give a full system information text to get you set. This should have been part of anybodies analysis otherwise we are just flailing around.

---

### Post by JohnLM_the_Ghost on 2010-11-17
Hmm how about deleting ALL partitions (even the FAT one) and trying to install on "unpartitioned space".
Or maybe zerofill the HDD altogether.

Hmm OEM Windows CD might not like either though. "Vanilla" Windows wouldn't mind though.

---

### Post by pradeepthundiyil on 2010-11-17
hi,

put windows cd, format the whole drive and install windows first.

then install ubuntu within windows as an application, wubi.. u can boot into both windows and ubuntu.. 

later u can uninstall ubuntu from add/remove softwares in windows control panel..

---

### Post by anewguy on 2010-11-17
> **pradeepthundiyil said:**
> hi,

put windows cd, format the whole drive and install windows first.

then install ubuntu within windows as an application, wubi.. u can boot into both windows and ubuntu.. 

later u can uninstall ubuntu from add/remove softwares in windows control panel..

NO - not wubi!  Check the forum - newbies have problems with it.  It is far better to install Windows, then do a defrag or 2 on the drive, then install Ubuntu by either letting it divide the disk in half, as it seems to by default, or manually specify the size of the partitions.

I appreciate your idea on wubi, believe me I'm not trying to insult or argue with you.  It's just there have been a *lot* of posts from people have trouble getting it to do what they want.  Even better than wubi would be to install a vm in Windows and run Ubuntu in it.  Kind of the same idea, but much cleaner.

Dave ;)

---

### Post by apollothethird on 2010-11-17
> **wilee-nilee said:**
> I would agree with the nix of the factory install, thats why I have a straight install ISO from acer. I think it is a cd the OP is using as suggested that would access a recovery partition or a backup. The home version doesn't have the backup installed but it is on the XP home cd for install, you just have to know where it is and how to install it.

The MBR isn't ever accessed with a install cd until you install or recover, it sounds like a wiped XP.

Op post the bootscript in my signature in code tags this will tell us exactly whats in the mbr basically and give a full system information text to get you set. This should have been part of anybodies analysis otherwise we are just flailing around.

Actually the nix from the factory probably wouldn’t hurt if it worked.  I understand that some computer manufacturers might say they won’t support your personal choice of OS.  But I haven’t seen an occasion yet where you couldn’t just purchase your chosen OS and install it on the computer.  If he originally had Windows XP on the computer and decided to go out and purchase his own Windows XP vanilla edition, it should work.  It should at least install unless there were problems, as in the OP’s case, with the Hard Drive.

I realize the computer manufacturer is getting paid a lot of money by putting bloating the system up with sample software.  One of my clients recently bought a Laptop from Office Max.  It appeared to be standard that their computer department offered him a charged him over a hundred dollars to optimize the computer.  I asked the computer guy what did that entail.  He said cleaning off the sample programs.

My client paid me to optimize his computer by purchasing and OS and installing Windows clean on the system, then only putting the programs that my client would be using.

I do this all the time.  The computer manufacturers try to trick the users into thinking they have to run their factory install.  I’ve never seen an occasion where that was really required.  There was a time when it was hard to find drivers for some of the hardware.  But even that has changed.

The OP has already said that he reformatted the drive and removed all the partitions.  On at this point the only thing left is to repair the MBR which is confusing Windows.

Again, it won’t hurt for the user to find a factory install disk.  But it’s not a requirement to install Windows on a computer.  I’m sure if there was such a computer manufactory that would only allow the users to install their factory version on the computer, I’d have heard about it.  I’m sure enough people would complain that they would remove whatever blockage they install that prevents a vanilla version of Windows from installing.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Mark Phelps on 2010-11-17
OK ... let's recap where we are now in this thread ...

OP started out by asking how they restore Windows from a "recovery cd"

Given that they evidently erased all the partitions on their drive, the simple (and CORRECT) answer is -- you can't!

So, to do what they asked (restore Windows), they will need to do one of the following:
1) Contact the PC manufacturer and obtain a set of full-restore CDs (or DVD) that do NOT rely on a recovery partition being on the drive
2) Obtain full Windows installation media through some other source.

---

### Post by apollothethird on 2010-11-19
> **Mark Phelps said:**
> OK ... let's recap where we are now in this thread ...

OP started out by asking how they restore Windows from a "recovery cd"

Given that they evidently erased all the partitions on their drive, the simple (and CORRECT) answer is -- you can't!

So, to do what they asked (restore Windows), they will need to do one of the following:
1) Contact the PC manufacturer and obtain a set of full-restore CDs (or DVD) that do NOT rely on a recovery partition being on the drive
2) Obtain full Windows installation media through some other source.

You got the recap right.  My messages were along the link of your point #2, which (which will also include point #1).  It’s apparent that the user is trying to perform either a new install or a recover (which with from my experience is a new install of the factory defaults).  Since the OP has mentioned that his attempt is giving the error of not enough space on a hard drive that doesn’t have anything on it, it’s very evident that the Windows is having problems with the disk.

The solution, to me is simple, or has been in the past.  Repair the MBR and Windows shouldn’t have problems with it.  It’ll start to see the space available.

Again, it’s my experience that a recovery disk will basically reformat the disk and bring it back to the way it was from the factory.  A full Windows installation would do similar, but not place un-chosen (by the user) sample software on his system.  The system would be a cleaner install.

I don’t know if he’ll have access to the disk repair utility from the recovery disk since it’s my experience, the recovery disk will wipe everything from the hard drive (which at this point isn’t a problem since he has mentioned that he has already cleaned the hard drive).

The Obtained full Windows Installation media that you mentioned will have the disk repair utility.  He could have used that before erasing all the information from his hard drive.  He can also use it even after erasing all the information off his hard drive.  The difference at this point is that he’ll have a clean disk that’s usable by his OS choice, whether it’s #1 from your list or #2 from your list.

With Windows XP and below the command is: “fdisk /mbr” to repair the master boot record.  With Windows Vista and above the command is: “bootsect /mbr” to repair the master boor record.

Take a look at: [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

You can get a list and description of the options by typing:

fdisk /help

Or

bootsect /help

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by theaveng on 2011-01-28
BUMP.  It's been two months.  

I'm going to try one more time to get Windows XP installed on my Compaq laptop, and if it still doesn't work, then I'll just sell it on ebay for ~50 bucks.  (1)  First I will run the XP Restore CD provided by Compaq.  Later:  And it gave me "not enough disk space" error per usual.

Next I will go into Lightweight Ubuntu (lubuntu) 10.0 and try to fix my partitions using..... um..... well I'm not sure.  

I'm confused.

---

### Post by JKyleOKC on 2011-01-28
Compaq and HP have, for years now, relied on a hidden recovery partition for "restoring" the system -- and when you wiped the disk clean, you removed that partition. You won't be able to get anywhere with that misnamed "recovery disk" because it only looks for the hidden partition -- that no longer exists -- and copies everything from there.

You have only one legal option if you want Windows back: go buy a new copy of Windows and install from its disks. Otherwise, just re-install Ubuntu or some other Linux distribution and continue to use your laptop.

You can probably find illegal pirated copies of Windows at little or no cost, but they are quite likely to be infested with malware and in any case will not pass Microsoft's "genuine Windows advantage" testing so that you won't be able to update them or install many legal packages...

It's too late to help you now, but for the benefit of others who may find this thread, NEVER do a total cleanup of a hard drive unless you are very sure you know what you are doing. Otherwise you may find it impossible to recover from it!

---

### Post by coffeecat on 2011-01-28
> **JKyleOKC said:**
> Compaq and HP have, for years now, relied on a hidden recovery partition for "restoring" the system -- and when you wiped the disk clean, you removed that partition. You won't be able to get anywhere with that misnamed "recovery disk" because it only looks for the hidden partition -- that no longer exists -- and copies everything from there.

Thanks for this information which I'll try to remember if I ever decide to get a HP/Compaq laptop or try to help someone else with the same. Let me be sure I have got this right. The HP "recovery disk" simply contains enough code to boot itself and copy the important stuff from the hidden partition - have I understood right?

That's appalling. With my Sony Vaio the recovery discs I prepared from the Sony utility in Windows can restore just the C: drive or the whole shooting match, including the recovery partition, and it also has one or two other utilities. Or I can boot into the recovery partition and restore the C: drive that way. But that's Sony for you - classy.

And with my Acer laptop I can use the restore DVDs to restore the C: partition but, interestingly, not the recovery partition. But that's Acer for you - not so classy. :)

---

### Post by Quackers on 2011-01-28
I'm horrified by that, personally.
So you get the option to create a recovery cd and all it does is access the recovery partition, which you can access via a key press at boot? Ridiculous imho!
What a sham! Ah well, that's HP and Compaq off my list :-)  (actually, they weren't on the list anyway :wink: )
As coffeecat has already said, the Sony recovery dvd's actually copy the recovery partition. That's a much safer way to do things.

---

### Post by JKyleOKC on 2011-01-28
> **coffeecat said:**
> Thanks for this information which I'll try to remember if I ever decide to get a HP/Compaq laptop or try to help someone else with the same. Let me be sure I have got this right. The HP "recovery disk" simply contains enough code to boot itself and copy the important stuff from the hidden partition - have I understood right?That's my understanding of the situation, although I've not actually disassembled the content of the "recovery" disk or the hidden partition.

I'm typing this via a Compaq that I use as my router/firewall/primary desktop/host for a number of VMs, but I replaced its original 350-GB drive with a 500-GB unit after a corruption problem, and it now single-boots Xubuntu Lucid (I prefer Xubuntu because it has fewer bells and whistles). Interestingly, the corruption vanished when I connected the original drive via a USB adapter to salvage what I could, so I do still have the original Vista and recovery partition available if I want them.

A few years ago when helping a friend with an Emachines system running WinXP Home, we had to use its recovery disk. Turned out that was simply a copy of Norton Ghost that accessed a hidden partition to bring back the original factory configuration! I suspect the Compaq disk would be pretty similar; I didn't get one with this machine at all -- it just booted through a Compaq menu originally, that told me to press F10 to "recover" the factory setup! No help at all, of course, should the drive itself fail...

---

### Post by coffeecat on 2011-01-28
> **JKyleOKC said:**
> Emachines

Emachine! Yes, I had an Emachine once. :-s. Emachines, already - ahem - a budget brand when bought out by Gateway to be used as a brand name for their budget range, in turn bought out by Acer to be used as a brand name for their budget range, with Acer already being a bu.... You get the picture. :wink:

This "can I trust the manufacturers to supply me with recovery partition/DVDs that actually work?" question means that I routinely use [Macrium Reflect Free]("http://www.macrium.com/reflectfree.asp") to image everything Windows-related (including the recovery partition) before I do anything with a new machine. I know this doesn't help the OP but like JKyleOKC, I'm posting this for others who may come across this thread.

---

### Post by theaveng on 2011-01-28
The only flaw with eMachines is the unreliable power supply (dies within 1-2 years).  After I replaced it my brother's Win98 eMachine lasted another decade. > **JKyleOKC said:**
> Compaq and HP have, for years now, relied on a hidden recovery partition for "restoring" the system   This laptop was built circa 2001 (it's an 800 MHz Pentium).  It should still have the full XP OS on the CD, rather than the hard drive.  I just need to figure-out how to get rid of Linux and put the NT File System back on my hard drive.  (I think?)

Also it looks like my experimentation has been postponed to Sunday.  The boss just asked me to work 12 hours today and 8 hours Saturday.  Crud.

---

### Post by Quackers on 2011-01-28
> **theaveng said:**
> This laptop was built circa 2001 (it's a 800 MHz Pentium).  It should still have the full XP OS on the CD, rather than the hard drive.  I just need to figure-out how to get rid of Linux and put the NT File System back on my hard drive.  (I think?)

If it's a cd it's not big enough to hold a recovery image. It would need to be a dvd (or possibly two).

---

### Post by JKyleOKC on 2011-01-28
I've got a couple of copies of WinXP Pro on single CDs, plus one copy of XP Home. They're 700-MB disks and are packed pretty full, but XP could fit (one of the two includes SP1 and the other includes SP2). It wasn't until Vista that the O/S itself gained so much bloat that a DVD or multiple CDs became necessary.

---

### Post by Rasa1111 on 2011-01-28
Am I wrong in thinking that,
 If you "format", you "delete"..
therefore.. recovery disks would do nothing for you..
Youd have to actually reinstall the whole OS. 
Which is *not* on a recovery disc(s). 

Yes? 

 Jkyle...
an OS on a disc, 
is not the same as a "recovery image" 
as Quackers stated., correct?

or again, am I wrong? lol

---

### Post by jd2012 on 2011-01-28
I once run into this problem with a Compaq F700. Totally screwed the OS and MBR, at the time, not knowing what to do, I called HP support.:confused:

I'm not sure if they still do it, but they told me (my computer was OUT of warranty att) they will ship me ONE and ONLY ONE "Full recovery" disc for free.
 (As I formatted the recovery partition months before to reclaim disk space.)  ](*,)

Booted to the disc and it reinstalled Vista flawlessly.

I guess the moral is don't go screwing with critical system components unless you know what your doing, or if you MUST, _do your research _first, then learn from your mistakes as have I. :lolflag:

@ OP, Perhaps try calling HP support, maybe they still do this? My encounter was August 08'

---

### Post by JKyleOKC on 2011-01-29
> **Rasa1111 said:**
> Am I wrong in thinking that,
 If you "format", you "delete"..
therefore.. recovery disks would do nothing for you..
Youd have to actually reinstall the whole OS. 
Which is *not* on a recovery disc(s). 

Yes? 

 Jkyle...
an OS on a disc, 
is not the same as a "recovery image" 
as Quackers stated., correct?

or again, am I wrong? lolA full recovery image should include the o/s in a fully installed condition, along with all thje bloatware sample programs included at the factory, so "so nothing for you" would not be correct. However your observation that the o/s on a disc is not the same as a recovery image is spot on.

I believe the OP wants to just get Windows back in operation so a fresh install of the o/s would do what he asked for. The suggestion by jd2012 to contact HP for a "full recovery" disc, though, is a good one.

---

### Post by theaveng on 2011-01-29
Windows XP shipped on a CD.   It took me all of 30 seconds to google that answer, so I'm not sure why many of ye keep saying   *  "It has to be a DVD,"    *  unless you're just making random guesses, rather than provide True technical support.> **jd2012 said:**
> I guess the moral is don't go screwing with critical system components unless you know what your doing  Maybe Ubuntu shouldn't go erasing Windows boot sector from the disk???  Maybe Ubuntu ought to include a way to preserve NTFS so, if the user decides he wants to go back to Mickeysoft or Mac OS-X, he can do so instead of forever being stuck.

---

### Post by JKyleOKC on 2011-01-29
The reason others were saying "it has to be a DVD" was that they were talking about a recovery image rather than just the o/s itself. A full recovery image could well contain two or three more CDs' worth of sample programs in addition to WinXP.

As for not overwriting at install time, the *buntu installation procedures DO give you a number of options, several of which will preserve your existing Windows installation. 

Perhaps it should default to a dual-boot setup using only available disk space, rather than the guided partitioning that can easily take the whole disk. However a Win7 installation typically has NO available disk space, which makes installing an additional o/s difficult until you've used the Windows tools to shrink it back down to a reasonable size.

---

### Post by coffeecat on 2011-01-29
> **theaveng said:**
> Windows XP shipped on a CD.   It took me all of 30 seconds to google that answer, so I'm not sure why many of ye keep saying   *  "It has to be a DVD,"    *  unless you're just making random guesses, rather than provide True technical support. 

That is very rude and insulting to people who have been trying to help you. Only the Microsoft XP install disc fits on a CD. A "proper" (i.e. one that works) OEM manufacturer's restore disc would almost certainly have to be a DVD (or set of CDs) to be able to fit all the added software, drivers and bloatware that typically comes with a pre-installed version of XP. Have you ever installed XP from a Microsoft disc? No, I guess not. You'd be amazed at what isn't included.

---

### Post by Rasa1111 on 2011-01-30
> **theaveng said:**
>   Maybe Ubuntu shouldn't go erasing Windows boot sector from the disk???  Maybe Ubuntu ought to include a way to preserve NTFS so, if the user decides he wants to go back to Mickeysoft or Mac OS-X, he can do so instead of forever being stuck.


 You are the one who formatted your disk. Not Ubuntu. 
You didnt have to "format" your entire disk just to remove Ubuntu. 

If you dont know what "format disk" actually means..
 You shouldn't have done it. 

 Maybe users ought to learn what they are doing before they go messing around with things, and then placing the blame elsewhere. 
:rolleyes:

 coffeecat,
 most agreed. <3

JKyle~ ahh, thanks mate. :) <3

---

### Post by theaveng on 2011-01-31
> **Rasa1111 said:**
> You are the one who formatted your disk. Not Ubuntu.   Not correct.  It was the "Lubuntu Live CD" that erased the NTFS and replaced it with the Linux file system during the installation process.   Then when I tried to go back to Windows, I discovered the restore CDs did not work. There should have been a warning, "If you do this, you won't be able to run windows in the future," or something along those lines.  If I had seen that I would not have installed Ubuntu.

And if I sound angry, I apologize.    *  It's  Frustration  *  not anger.   I've got the 3 XP restore CDs sitting here, and I can't believe they refuse to install despite all my previous attempts to NTFS the drive. 

I know if I could somehow get NTFS back on there, the restore would work.  
As things stand now, 
my ISP refuses to work with 
ubuntu so the laptop is worthless.

---

### Post by Quackers on 2011-01-31
When booting from the recovery cd are you given any options, like "recover the whole system" or "restore C: drive"? Were the recovery cd's made from the machine you are trying to use them on?
And we are not "technical support"! We are people trying to help other people who may, or may not, have made mistakes.
I think you'll find that technical support is usually paid for.

---

### Post by theaveng on 2011-01-31
FINALLY I got Windows XP reinstalled.  The problem was Lubuntu's partition tool wasn't working properly, so I tried plain-vanilla ubuntu and it did the job (erased the HD).  To give you some idea how old this thing is - it uses Netscape 6 (equivalent to Mozilla/firefox 0.6).  > **anewguy said:**
> It is far better to install Windows, then do a defrag or 2 on the drive, then install Ubuntu by either letting it divide the disk in half, as it seems to by default (or manually specify the size of the partitions).  Why would I need to do a defrag if I just installed Windows?  It shouldn't be fragmented at all.

I have just over 18 gigabytes left.  Probably not enough to do a dual install of Lightweight Ubuntu?  Maybe Puppy would work.

---

### Post by Quackers on 2011-01-31
> **theaveng said:**
> FINALLY I got Windows XP reinstalled.  The problem was Lubuntu's partition tool wasn't working properly, so I tried plain-vanilla ubuntu and it did the job (erased the HD).  To give you some idea how old this thing is - it uses Netscape 6 (equivalent to Mozilla/firefox 0.6), MSN Explorer, and CompuServe as default desktop icons.    Why would I need to do a defrag if I just installed Windows?  It shouldn't be fragmented at all.

I have just over 18 gigabytes left.  Probably not enough to do a dual install of Lightweight Ubuntu?  Maybe Puppy would work.
Because Windows puts files all over the place - even when freshly installed. You only need to defrag if you're going to resize the Windows partition, though.

---

### Post by theaveng on 2011-02-01
Anybody want to explain why, two months ago, I received a "Only dumbasses go back to windows" in my private email?  
Real mature.

---

### Post by NCLI on 2011-02-01
> **theaveng said:**
> Anybody want to explain why, two months ago, I received a "Only dumbasses go back to windows" in my private email?  
Real mature.
Did you receive a PM notification through your email? If so, you should report the user to the moderator team.

---

### Post by Irihapeti on 2011-02-01
> **theaveng said:**
> 

I have just over 18 gigabytes left.  Probably not enough to do a dual install of Lightweight Ubuntu?  Maybe Puppy would work.

My EeePC 900 has a total of 20GB of disk space. A standard install of Ubuntu leaves plenty of room. So I think that 18 GB should be fine. Of course, that partly depends on how many music/video files you want to store.

I've even had standard Ubuntu running off a 4GB SD card. I wouldn't recommend that for daily use, but it shows what can be done.

---

### Post by theaveng on 2011-02-02
My Commodore=Amiga runs off a floppy and half a megabyte.  ;-)

Maybe I'll just advertise the laptop on Ebay as "Windows And Ubuntu Linux" and ship the Linux CD separately.  Leave it up to the winner if they want to install both at the same time.  Otherwise they might be disappointed to see the Windows Half is only ~8 gigs.

---

### Post by Rasa1111 on 2011-02-04
> **theaveng said:**
> Anybody want to explain why, two months ago, I received a "Only dumbasses go back to windows" in my private email?  
Real mature.

 Want to explain How anyone here would know your 'private email"?

Unless you mean private messages.. 

In which case you *could * report the sender of the message to admin.

---

