---
title: "Wubi Vs Partitioning"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by mrpinchy on 2009-05-28
Hey All,
 
Am I being paranoid.  Is it that easy to "hit the wrong button".
 
I am torn between using Wubi or trying to partition my HD.  I only have a backup partition for Windows, so if I blow it, I don't have a disc for a re-install.
 
I want to keep MS because I use some programs for work.
 
Has anyone done both and can directly compare Wubi & Partitioning.
 
Thanks,
Joe.

---

### Post by keplerspeed on 2009-05-28
Ok have a look here:

[http://ubuntuforums.org/showthread.php?t=841370](http://ubuntuforums.org/showthread.php?t=841370)

I have done both, and I much rather a partitioned drive, just to keep my linux separate from win. If you pay attention to the installer, you cant do anything wrong, ubuntu will do all the right partitioning for you!

---

### Post by powel212 on 2009-05-28
i am not a big fan of the Wub - Ive tried it and had mixed results

Here is the safest way I know for a windows user to create a dual boot without having to leave his area of understanding



You are familiar with windows so I suggest using the win partitioner to set up your partitions before installing.


Create a new empty partition. Use the "Windows Computer Manager - Disk management tool" to configure your partitions.

Create the partition for Ubuntu.

Leave the new partition unformatted as a blank partition, This is most important, do not format the new partition just leave it blank.. We will deal with it later. Apply changes.

Insert the Live CD and Reboot

Insert your Ubuntu "Live" CD and boot from it "try Ubuntu without changes to my computer"

Once booted and running from the Live cd, chose install.

enter the appropriate information, country, language etc but when you arrive at the partition screen you will have a choice where to install Ubuntu.

This is the important part and this is why we left that unformatted space before. You can now chose to install Ubuntu to "the largest continuous free space" In doing so Ubuntu will now install to the empty space we left unformatted. Do not adjust the slider. Ubuntu will only install to the empty space we made before and will leave your windows alone.

Allow the rest of the install to run and reboot.

Upon reboot you will be greeted with Ubuntu's Grub screen where you will be given a short list of options to boot from. there will be Ubuntu at the top and Windows at the bottom. Just use the arrow keys to select the system you want to boot.

Now you are almost done. But once you have booted into Ubuntu for the first time from the hard drive you won't see the Win partition on your desktop so we need to install a little applet so all your partitions will be mounted automatically.

Go to "Applications-Add/Remove...

Change the box at top that says "show" from "Conical-maintained-applications" to "All available applications"

Than type into the search box "NTFS"

in a second or 2 you will see a program called NTFS configuration tool.

Put a check in the box beside it and then apply changes.

Close Add/remove

Then go to "Applications-System_Tools-NTFS Configuration tool"

if it is not there try

"System-Administration-NTFS Configuration tool"

After launching the tool just check the boxes next to; enable read and write to internal and external drives.

the next time you boot all your drives will appear on the desktop.

I hope that helps.

Powel

---

### Post by Mark Phelps on 2009-05-28
> **keplerspeed said:**
> If you pay attention to the installer, you cant do anything wrong, ubuntu will do all the right partitioning for you!
Unfortunately, if you're running Vista, those answers aren't correct, in that Yes (you can do something wrong) and No (Ubuntu will not do all the right stuff for you). 

There's post after post on this forum mentioning the Vista OS being corrupted after resizing with GParted.  The standard "fix" (which doesn't always work) is to boot from teh Vista DVD (not an OEM recovery CD) and run Startup Repair.  But without the DVD, if the partition does get corrupted, you're pretty much hosed.

As powel212 mentioned, the safest way to do the resizing is with the Vista Disk Management tool. It's crude, but it doesn't corrupt the OS partition as a side effect.

However, once you shrink the Vista OS partition, you can safely use GParted to create the Ubuntu partitions.  I strongly recommend you download, burn, and use the GParted LiveCD (which you can get from distrowatch.com) to do the partitioning.  It's a newer version than the GParted bundled with the distro.

Also suggest that you create an Extended partition in the unallocated space and create Ubuntu partitions inside that.

---

### Post by philinux on 2009-05-28
> **mrpinchy said:**
> Hey All,
 
Am I being paranoid.  Is it that easy to "hit the wrong button".
 
I am torn between using Wubi or trying to partition my HD.  I only have a backup partition for Windows, so if I blow it, I don't have a disc for a re-install.
 
I want to keep MS because I use some programs for work.
 
Has anyone done both and can directly compare Wubi & Partitioning.
 
Thanks,
Joe.

Which version of MS are you running.

---

### Post by mrpinchy on 2009-05-28
Okay; so I was thinking of giving Ubuntu about 50 gigs since I've got 170gigs of free space.  Would that be enough, or should I give a bit more?  
 
Mark,
I am running Vista H-Prem, so I should use the windows partitioning tool?
You say I should create an extended partition and put the Ubuntu partitions inside that.  How many partitions will Ubuntu need, and what constitutes and extended partition
 
Thanks,
Joe.

---

### Post by 3rdalbum on 2009-05-28
50 gigs is plenty. The base system only takes up about 3 gigabytes so there's lots of room for you to grow.

---

### Post by Sidewinder1 on 2009-05-28
I strongly suggest that from windoze (vista or xp) that you [COLOR=Red]DEFRAGMENT[COLOR=Black] BEFORE you shrink the NTFS/FAT32 partition because windoze writes files all over the drive. If you shrink it without defragging you'll probably end up with many corrupted files.
HTH,
Side
[/COLOR][/COLOR]

---

### Post by Hospadar on 2009-05-28
I agree with the above,
defrag windows, and backup super-critical files.

The resizing is very safe and I've never had it corrupt things (defrag or no) but sometimes it fails and prompts windows to chkdisk, and I know people who've had problems.

and in all honesty, you might just make a mistake and wipe your drive, I did it once, if you arn't dumb it won't happen, but we all are sometimes.

---

### Post by philinux on 2009-05-28
All of the above. Make sure to use vista's disk tools to shrink or make your partition. On no account use gparted.

I've recently done this on a lappy running vista premium.

---

### Post by mrpinchy on 2009-05-28
I figure this is probably a preference thing, but what do you folks say about which version to use.  I have heard that 8.04 is the least buggy and a good introduction for a begginer.
 
Thanks,
Joe.

---

### Post by philinux on 2009-05-28
I have 8.04 installed on my GF's pc which she uses for work, open office and internet mainly. As she live 50 miles away I dont want any updates borking her system. 8.04 is the LTS long term support release and is the most stable.

I use 9.04 on one drive and I'm testing 9.10 on the other. I can usually sort out any problems myself.

---

### Post by powel212 on 2009-05-28
Jaunty is awesome but it is a bit buggy on initial install.

First time I recommend intrepid (8.10)

P

---

### Post by Paqman on 2009-05-28
> **powel212 said:**
> Jaunty is awesome but it is a bit buggy on initial install.

First time I recommend intrepid (8.10)


Jaunty is buggy on is Intel graphics cards. If you have one, definitely use Intrepid, but otherwise Jaunty is great.

I'm a big Wubi fan though, it's a great way to get your system installed. You can even transfer a Wubi-installed system onto a dedicated partitions without reinstalling by using LVPM. So it's not really an either/or decision.

---

### Post by Bartender on 2009-05-28
> **mrpinchy said:**
> I only have a backup partition for Windows, so if I blow it, I don't have a disc for a re-install.
Joe.

What do you mean by a "backup partition"?  Don't you mean a recovery partition?  Have you tried to burn recovery discs?

---

### Post by Steelmourne on 2009-05-28
All good answers but do you really need vista in the first place? Most programs can be duplicated on Ubuntu. Just wondering. Otherwise defrag the windows hard drive and use disk management to shrink the main partition. On one PC, vista only shrank 10gb despite 50gb being free. Up to you.

---

### Post by mrpinchy on 2009-05-29
Well, I set up a new partition to drop Ubuntu in when I figure out which works better.  I still am having a wicked time getting 9.04 onto a DVD, and I haven't been able to find 8.10.  8.04 burned fine and I am using the live disc right now.  I may have to order 9.04 so I can try them both out before I go with one or the other.  So far these are the only issues I have.

The speakers are sometimes crackly-

The mouse trackpad won't shut off, which I need it to, don't ask unless you want an answer.

The wireless doesn't turn on.

Compaq laptop,
Vista home prem,
2 gig Athlon X2 64,
2 gigs RAM,
Synaptics pointing device (trackpad),
Atheros 802.11 wireless card,
NVidia sound card

Thanks,
Joe.

---

### Post by powel212 on 2009-05-31
Ubuntu 8.10 intrepid ibex here

[http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

Powel

---

### Post by mrpinchy on 2009-05-31
Thanks for the link.
 
I found a group that holds a meeting for dumb noobs such as myself.  They are meeting this Tuesday here in Boston, so I'm gonna check it out and see what comes of it.
 
Thanks to all who have helped me thus far & I'm sure I'll have all sorts of questions in the near future.  I'm gonna burn 8.10 and bring it with me so I have some options, though I imagine they will have install discs of their own.  Hey, I'm psyched to have got this far.
 
And if I crash my system and it gets wiped, I hope I at least learn something.
 
Cheers,
Joe.

---

