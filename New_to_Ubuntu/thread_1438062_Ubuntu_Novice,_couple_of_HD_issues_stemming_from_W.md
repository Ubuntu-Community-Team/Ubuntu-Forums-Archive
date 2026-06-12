---
title: "Ubuntu Novice, couple of HD issues stemming from Windows problem"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by gallow737 on 2010-03-24
Hello there, I am new to Ubuntu and Linux, and by new I mean about 45 minutes new.  I had always read about Ubuntu and heard nothing but great things, but relied on Windows for its support of the programs I need for my work (video editing).  Well, I got fed up with Windows over the past few days and tried for 2 days to fix my issues and none of them worked, so I found out how to put Ubuntu on a USB disk and I installed it and got it working in less than 10 minutes.  Talk about awesome!  I love it so far, but am having issues with my HD's which are issues that stem from my tooling around trying to fix windows.  I suppose I should start from the beginning, but if you want to skip the backstory I'll just put it in quotes and you can skip it if you'd like and go to the problem below it...

> My computer had some viruses on it and they showed up a mere month removed from restoring my windows because of other viruses.  I could do my work easily in Windows but the viruses were a nuisance (the search engine hijack viruses and a facebook pop up virus and/or malware, whatever).  Needless to say, I ran spyware and virus scans and they all found something, but not the cause of the problem and it never got fixed.  

I decided to go ahead and transfer all my valuable files onto my external HD and reformat and reinstall Windows. I have dual 250GB HD's on my computer, so when I went to reinstall Windows and reformat a HD using an XP boot disk.  Well it all went perfectly fine until it gave me an "NTLDR missing" error and it wouldn't load Windows to install properly.  

I then tried several dozen means of fixing it, none of which worked.  I had to borrow another install disk because mine for some reason didn't have a recovery mode on it.  I got int there and did exactly what several dozen help sites said I should do and sure enough none of it worked.  I tried installing to both HD's and both of them had errors.

I then decided to slow format both HD and try and wipe both of them out completely via a recovery mode's command prompt.  They formatted fine and I restarted and sure enough, no fix after reinstalling windows.  Also, I noticed that after formatting both drives, it said I only had about 130GB free of 250GB, which was strange considering it should've wiped everything clean.  This was about the time I said "ENOUGH!" and I decided to give Ubuntu a try.  And this was about an hour ago, and here I am with a functioning computer with Ubuntu installed on it.  But here's the issue:When I booted up the Ubuntu install and it gave me the demo mode or what have you, it showed I had my two HD's available to click on.  They both said I had bad sectors, which I later found out via a quick google search is a bug with 9.10 and Maxtor HD's and I should ignore it.  So I did.  Anyways, I installed Ubuntu to one of my HD's and it asked me about partitioning and unmounting or something (I told you, I'm novice as all get out with hardware jargon), so I opted to leave it the way it was for now, figuring it could do no harm.

It installed, and everything was fine, till I got into the fully installed Ubuntu and now it only allows me to access one of my HD's.  And on the HD I see three files: "boot.ini" "NTDETECT.COM" and "ntldr", the latter two of the files I needed to copy over from Windows trying to get the Windows install disk to boot up.  These are 261KB in file size... but Ubuntu is telling me I only have 127GB free on my 251GB Filesystem.  So the mystery of my missing HD space still exists.

That's issue #1: Where is my missing space and how do I get it back?  And what is taking that space up?  My first inclination was to reformat the HD, but I haven't the slightest clue how to do that in Ubuntu, or even if that's what I should do.  I have a feeling Windows left some stuff on there (it's pretty obvious actually), and this issue will be the same on the 2nd hard drive, which brings me to...

Issue #2: Why isn't my 2nd hard drive detected and able to be accessed?  It is recognized in the disk utility, but it seems I cannot access it to save files to it.  Perhaps the other is still partly loaded with Windows?  I'd really like to get that HD back and access it via Ubuntu.  Being able to run windows on the other HD would be swell, but Windows is being kind of a jerk to me lately so I'm done with it for now and am committed to trying to get used to Ubuntu and its open source alternatives (or use WINE to run some of the other programs I need), and having that extra HD would be greatly useful.

So those are my two primary issues at the moment... how do I get my disk space back, and how do I get Ubuntu to recognize my other HD.

Aside from those technical issues, I do have some other non technical questions I figured I'd ask while I'm here.  For one, is Ubuntu capable of running Adobe applications?  I use the Adobe production suite for video, graphical, and web editing, this is why I ask.  I know WINE is supposed to emulate windows to get them to run on Ubuntu, will it be able to handle Adobe applications? 

If not, what are some good alternatives?  I'm aware of Gimp, but nothing else in the realm of video or web editing.

Many many thanks if there's anyone out there how can help me!  Until then I'll be getting situated with the OS, I'm loving it so far.  Thanks!

---

### Post by ugm6hr on 2010-03-24
Not really sure exactly what is going on here, but I would suggest you start by running a HD diagnostic. Most HD manufacturers have CDs available to do this, else there are some all-in-one diagnostic disks out there ( [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) )

The missing space probably reflects the way you installed Ubuntu when it asked about partitions etc (unless you do have a faulty HD).  From memory, the default is sometimes to shrink Windows and just use half the drive.

After doing a hardware check - copy and paste the output from:
```
sudo fdisk -l
```

---

### Post by patchwork on 2010-03-24
Can you open a terminal (Applications > Accessories > Terminal) and type```
sudo fdisk -l
cat /etc/fstab
``` and post the output here?

The first command will display your detected hard drives and partitions (and their filesystem format)
The second will display the drives that will be mounted (connected to) on startup.

---

### Post by gallow737 on 2010-03-24
Time for my novice brain to kick in.  I have Hiren's Boot CD, so I have all the programs that come with that, which one should I use to run a HD diagnostic?  Never had todo that before so I don't know which program does what (or how to use them for that matter)

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

FWIW, here is what it currently says when I type that into the terminal:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa932a932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29763   239071266   83  Linux
/dev/sda2           29764       30515     6040440    5  Extended
/dev/sda5           29764       30515     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
16 heads, 63 sectors/track, 486344 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x5d81e8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      486341   245115832+   7  HPFS/NTFS

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e6b2e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1      182401  1465136001    7  HPFS/NTFS


```

---

### Post by ugm6hr on 2010-03-24
Hirens HD diagnostic app:
Maxtor PowerMax 4.23 (for Maxtor drives)
Otherwise HDD Scan looks like it might suffice - but I always use the manufacturers apps myself

fdisk lists your HDs as present:
sda is the HD Ubuntu is installed on. Size is OK - 251GB. You have 2 partitions: main (sda1) and swap drive (think "Virtual Memory" in Windows) sda5. Sizes are about right - reason you can't "see" this drive is it is in the main "root" drive - if you want to add files, just put them in /home (seen as Home)
sdb is your 2nd HD. Size is OK - 251GB. Not sure why it is seen as being half full - but it makes sense to just reformat.  We'll come to that later.
I have no idea what sdg is - 1500GB?

---

### Post by Mark Phelps on 2010-03-24
In answer to your Adobe question, Wine is only able to handle SOME MS Apps, and even then, only some of those well.

The link below is to the WineHQ site where they rate their compatibility with MS Apps.  Enter Adobe next to the "name contains" and click the Update Filter button.

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true")

You can see for yourself that quite a few are rated Garbage, and many of those are the most current version.

---

### Post by natravis on 2010-03-24
> **gallow737 said:**
> Time for my novice brain to kick in.  I have Hiren's Boot CD, so I have all the programs that come with that, which one should I use to run a HD diagnostic?  Never had todo that before so I don't know which program does what (or how to use them for that matter)

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)


From your link, and given that you already stated you had Maxtor drives, the "Maxtor PowerMax 4.23 designed to perform diagnostic read/write verifications on Maxtor/Quantum hard drives" seems to be the logical choice. You can also use SeaTools (stated to work on Maxtor drives, and it has worked for me in the past, but may not be able to give you a diagnosis beyond "all good" or "something wrong").

> **gallow737 said:**
> FWIW, here is what it currently says when I type that into the terminal:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa932a932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29763   239071266   83  Linux
/dev/sda2           29764       30515     6040440    5  Extended
/dev/sda5           29764       30515     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
16 heads, 63 sectors/track, 486344 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x5d81e8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      486341   245115832+   7  HPFS/NTFS

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e6b2e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1      182401  1465136001    7  HPFS/NTFS


```

Your first HDD is confusing me. The partition table looks normal, but you say that the available space doesn't add up. Very strange. The second HDD has a single NTFS partition on it (expected). You have to mount the secondary drives in order to use them. This is normally accomplished by selecting the drive under the "Places" menu, then typing in your password. You can set this up for automatic mounting upon boot, but lets cross that bridge later.

If you have all of your data on the external, safely remove the external. Then, I would insert the LiveCD again, boot from it, and select install, then when you get to the screen asking where to install, use the automated "whole disk" option (not the one that saves windows). If you want, you can use the manual option to setup both drives now. To do that would be something like the following:
[LIST]
[*]Select manual partioning
[*]Select the first HDD
[*]Clear the current partition table
[*]Create a new partition (make it around 10-15 GBs depending on how many programs you think you will be installing), mount it as "/" (without quotes)
[*]Create a new partition that will take up all remaining space minus about 2-4GBs depending on how much RAM you have in the machine (this is for swap space), mount it as "/home"
[*]Create a partition that will take all remaining space as swap (confirm that the number translates to around 2-4GBs (use google for calculator "convert xxx bytes to GBs" for example), change type to "Swap"
[*]Select second 250GB drive
[*]Create a single partition, mount it as /data or /home/(your user name)/extradrive or whatever you want it called. Different names/places for different uses. Let us know what you might be using it for, and we can recommend a better name/mount point.
[/LIST]

I think that is about right, anyone else feel free to chime in if I am in the wrong.

---

### Post by gallow737 on 2010-03-24
1) Oooohhhhh, so "Home" is my 1st HD and the 251GB Filesystem is my secondary.  Excellent, thank you!  

2) The 1500GB thing is my external HD, I had it plugged in (I had Hiren's Boot Cd on there).

3) Thank you for the info on Wine, I'll be sure to peruse it and and also find suitable apps to replace ones I can't use well.  

Also the update manager popped up with a whole mess of updates to install... I went aheadwith it, is this a normal thing for new users?  I'm assuming so

---

### Post by patchwork on 2010-03-24
> 1) Oooohhhhh, so "Home" is my 1st HD and the 251GB Filesystem is my secondary.  Excellent, thank you!  

What that output actually shows is that your first hd has the entire linux filesystem on it, with swap space.  Your second hard drive was not touched during the installation (and remains formatted with the Windows NTFS format).  What natravis is suggesting is to reinstall, and explicitly reformat each of the two hard drives in one process (leaving you with two hard disks formatted for use with linux, one of which will contain the filesystem itself and the other being a storage disk only).

If you decide to go this route, it would be safer to remove the external disk, just in case (Murphy's Law).

---

### Post by gallow737 on 2010-03-24
> **patchwork said:**
> What that output actually shows is that your first hd has the entire linux filesystem on it, with swap space.  Your second hard drive was not touched during the installation (and remains formatted with the Windows NTFS format).  What natravis is suggesting is to reinstall, and explicitly reformat each of the two hard drives in one process (leaving you with two hard disks formatted for use with linux, one of which will contain the filesystem itself and the other being a storage disk only).

If you decide to go this route, it would be safer to remove the external disk, just in case (Murphy's Law).

Gotcha.  I think I definitely want to go that route.  I followed a dozen different NTLDR fixes I found through Google trying to get Windows up and running and while I did them exactly the way they told me to, not a single one of them worked, so I'm completely zonked out of Windows right now.  Getting that space back would be clutch so I think I'll go that route.  Byu doing that will I have to re-do everything I just did (re-adding my bookmarks, the update manager, driver updates), or will it just clear out the other HD?

---

### Post by gallow737 on 2010-03-24
Oh, another thing.  My sound apparently is not working.  I backed up all my drivers in Windows before doing the format and reinstall, but I'm not sure if I can transfer those over to Ubuntu or not.  So far when going into the Hardware Drivers page, it only gives me the option of installing a video card driver, which I did already, but nothing else pops up.

I have a Sound Blaster Audigy sound card, not sure what model/version/etc.

---

### Post by patchwork on 2010-03-24
It depends on how you want to proceed.  There are a couple of ways to go from here.

1.  Keep what you have on the first disk and only reformat the second disk
         Pros:  Keep your updates, and bookmarks
                   Easier
         Cons:  Many people like to keep their root ('/') filesystem separate from their personal documents (in case of disaster in the filesystem, or to install newer versions cleanly without the hassle of upgrading.  This is a personal choice, but I have separate partitions for / and /home.  Right now, your root and personal files are on the same partition.  This makes upgrading to the next version of Ubuntu with a clean install harder (you will need to backup all of your personal documents), but you will be able to easily upgrade without a clean install.

2.  Start from scratch.  Reformat both disks, creating separate /, /home, and swap partitions on your first drive, and however many partitions you want on your second drive.
       Pros:  Separate partitions allow you to do a clean install on upgrading, or to still access your personal data if the root filesystem becomes unusable (through live cd or another OS)
       Cons:  You've wasted a few minutes upgrading an installation that you're going to remove and re-install.

Really, it's up to you.   I personally recommend using natravis' suggestions.  I think you'll be better off long term.



EDIT:  Since drivers communicate between the operating system and the hardware, windows drivers do not work on linux (with a few exceptions for wireless cards with a third-party driver wrapper module).  Sound blaster cards are generally well supported by default, it's more likely that there is a volume setting turned down somewhere.   To check to see if your card is acknowledged, you can type```
lspci | grep -i Audio
``` in the terminal.  You should see your card listed.

---

### Post by gallow737 on 2010-03-24
Think I'll go ahead and give that a whirl.  You guys have been a tremendous help, thank you.

---

### Post by ugm6hr on 2010-03-24
To save having to re-download the updates - copy all files (except the "lock" file) in:
/var/cache/apt/archives
to your external HD

When you re-install, you can copy back to the same location (using "gksudo nautilus") and then the update manager will pick them up.

I would also recommend a re-install using "manual" with separate home partition - you did say it only took 10 minutes the first time. Use about 20GB for the /home - 10GB can be filled if you like experimenting with new applications, which is very likely as someone who hasn't used Linux / Open Source much before.

As suggested, make sure the external drive is unplugged before installing - that way there is no risk of deleting everything.

---

### Post by gallow737 on 2010-03-24
1) Got the sound working, a lot of the options came up after the update, and also the internal speakers were set as default, lol.  

2) Thank you for telling me how to backup the updates, I'll do that.  I'll go ahead and go through with this thing now and let you guys know how it turned out.  Thanks so much

---

### Post by ugm6hr on 2010-03-24
No worries.

If you want further advice - just pop back here.

If you do want advice re: image / video apps, I'd suggest you start a new thread with a sensible title.  But, in brief: Wine - check their site to see what works (not much); GIMP or GIMPshop for images/photo; Cinerella, Openshot, Avidemux, Kino, Kdenlive, Lives are all options for video - a quick search here / Google will give more detail; Inkscape for Vector drawing; Scribus for DTP.

I'm sure I've neglected lots of options - but that should at least get you started.

---

### Post by gallow737 on 2010-03-24
I'm back, and everything is set up wonderfully, thank you guys for the detailed and easy to follow instructions. You just made my Ubuntu experience a thousand times better!

I'll be sure to check those video options out.  Didn't realize there were so many.  Thanks you guys for all the help, if I have any more questions I'll be sure to ask!

---

### Post by errrata on 2010-03-25
Anybody in the tech support industry read this thread!

"I'm back, and everything is set up wonderfully, thank you guys for the detailed and easy to follow instructions. You just made my Ubuntu experience a thousand times better!"

that's how it should end, 'nough said.

---

### Post by natravis on 2010-03-25
> **errrata said:**
> Anybody in the tech support industry read this thread!

"I'm back, and everything is set up wonderfully, thank you guys for the detailed and easy to follow instructions. You just made my Ubuntu experience a thousand times better!"

that's how it should end, 'nough said.

I work tech support for the FDIC in the USA. I actually typed my response while at work, but on my lunch break.

Glad to hear its working for you now! Enjoy learning this awesome tool

---

