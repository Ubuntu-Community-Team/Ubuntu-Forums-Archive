---
title: "I think I screwed up my partitions"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by kudzu on 2010-01-12
Hey everyone,

I think I gave Windows too big of a partition and Ubuntu too small of a partition when I installed Ubuntu.  I've been playing around with Ubuntu a little bit for the past year and I've decided to abandon Windows and use Ubuntu exclusively, since I've come to enjoy it so much more than Windows.  I figured I might as well leave Windows on my computer, even if I won't be using it, though.  So, I was cleaning up my Windows, uninstalling programs and degragging so as to minimize the space taken up by Windows on my hard drive, when I noticed that my Windows partition seemed to be pretty big, relative to my hard drive space, according to My Computer in Windows.  I checked on Ubuntu, and from what I can tell, Windows is allotted 94GB of my 120GB hard drive, while Ubuntu is allotted 22GB.  I could be misunderstanding this, so I've attached two screenshots to this post.

If it is the case that my partition arrangement doesn't suit my intended uses for my system, how might I got about repartitioning my hard drive?  Windows came pre-installed on my computer and I have no idea where the Windows disc is.

Thanks.

---

### Post by scragar on 2010-01-12
If you still have your ubuntu liveCD look into gParted which is installed on the CD.

---

### Post by pricetech on 2010-01-12
You are reading correctly.  Before you downsize your winders partition you need to turn off system restore (temporarily) and defrag it.  Once you decide how small you want your winders partition to be, then downsize accordingly.

Hypothetically speaking;  If you had the Dell installation media, would you do away with winders ??

---

### Post by kudzu on 2010-01-12
My original Ubuntu live disc was for version 8.04 and I just upgraded to 9.10... and I definitely don't have that disc anymore, anyway (I moved from the U.S. to Korea not long after I bought my computer and installed Ubuntu - I left the live disc, along with a lot of stuff, back home).

EDIT in response to pricetech: What would be a good size for an unused Windows partition, in your opinion?  And then how do I do it?  I have considered getting rid of Windows, actually, and my installation media is probably somewhere back home.  How hard is it to get rid of Windows?  The only thing holding me back, really, is that my webcam doesn't work automatically in Ubuntu, and I like to use it to call back home on Skype.  I've looked into the situation and it seems like the drivers are out there and workable, but I haven't had any luck sorting the situation out yet.

---

### Post by raymondh on 2010-01-12
I've had XP down to 20gb.  Vista and 7, about 40gb.

Which version windows are you using?  

Raymond

---

### Post by kudzu on 2010-01-12
I'm using Vista.

---

### Post by raymondh on 2010-01-12
> **kudzu said:**
> I'm using Vista.


I would download and burn this first...just in case....

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Use Vista to shrink the vista partition.  Note that windows has a habit of 'scattering' (my words) immovable files around the partition.  The net effect is that, using the vista disc management tool, you won't be able to shrink as much.  There is a workaround posted by how-to-geek.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Even with this, would I still recommend using Vista to shrink Vista?  Yes.  *(Note, I say YES even though I am a big fan of gparted*).

After shrinking Vista, boot into it (vista) and let it run its' checkdsk.  Make sure Vista is booting fine.  Then boot into the liveCD and access gparted to enlarge the existing Ubuntu root (/) install.

Back-up your files.  Good luck.

Raymond

---

### Post by btedm on 2010-01-12
Instead of changing partition sizes, you could probably leave it alone and rearrange your files.  Your Linux partition is reasonably large and you will only need more room if you have some large directories for example with music or pictures.  These large directories can be stored on the Windows partition.  Ubuntu can access NTFS partitions so make a directory/folder there and most of the data can be stored on the Windows partition.  There are many ways of arranging a drive so select the method you like the best.

---

### Post by pricetech on 2010-01-12
> **kudzu said:**
>  What would be a good size for an unused Windows partition, in your opinion?

I do a lot of imaging to replicate winders setups across several identical computers.  A typical XP image tends to be between 6 and 8 gigs depending on what's installed.  Based upon that I would agree that 20 gigs should be fine for an XP partition.

I haven't deployed vista yet, so I can't say what's the best size for it,  I'd guess that the 40 gig recommendation would be sound.

I also concur that downsizing it with vista is probably the best approach, then use Ubuntu to take up the new free space.  Are you planning a fresh install of Karmic ??

---

### Post by kudzu on 2010-01-12
scragar, pricetech, raymondh, btedm - thanks guys!  

I hate to waste your advice, but the more I think about it, the more I think I'd like to just get rid of windows altogether.  I've read on this forum that if I make a live disc and run GPartEd from the disc that I can delete the Windows partition on my hard disc.  Going on the screenshots of my partitions that I attached to my first post, is there anything else I need to know about this process?  For example, I read that it's best to have Linux on the first partition, since that's the fastest part of the hard drive - will Linux occupy the first partition after I delete Windows using GPartEd?

---

### Post by sandyd on 2010-01-12
> **kudzu said:**
> scragar, pricetech, raymondh, btedm - thanks guys!  

I hate to waste your advice, but the more I think about it, the more I think I'd like to just get rid of windows altogether.  I've read on this forum that if I make a live disc and run GPartEd from the disc that I can delete the Windows partition on my hard disc.  Going on the screenshots of my partitions that I attached to my first post, is there anything else I need to know about this process?  For example, I read that it's best to have Linux on the first partition, since that's the fastest part of the hard drive - will Linux occupy the first partition after I delete Windows using GPartEd?
you will have to manually expand the linux partition using Gparted after deleting the windows partition.
Right Click -> Resize i believe

---

### Post by kudzu on 2010-01-12
Ok, cool.  Should I still go into Windows and turn off system restore and defrag my hard drive before I delete the Windows partition with GPartEd?  And will expanding the Linux partition on my hard drive by using GPartEd sort out all of the partitions so that Linux is on the fastest partition?

---

### Post by raymondh on 2010-01-12
> **kudzu said:**
> Ok, cool.  Should I still go into Windows and turn off system restore and defrag my hard drive before I delete the Windows partition with GPartEd?  And will expanding the Linux partition on my hard drive by using GPartEd sort out all of the partitions so that Linux is on the fastest partition?

Defrag is always a good idea.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Since ubuntu is in an extended partition, you'll need to resize the extended partition first ... and then resize the Ubuntu partition.  Tip:  *Click to highlight the partition* you intend to resize (you can also double check by looking at the partition table and verify that the same partition is highlighted).  

If you need help identifying the partitions, kindly access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

Small L.  It will ask you for your password which will be invisible when you type.

Copy and post back the results of that command.

Raymond

---

### Post by kudzu on 2010-01-12
Here's my partition information, raymondh:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13         274     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         274       11761    92274688    7  HPFS/NTFS
/dev/sda4           11762       14593    22748040    5  Extended
/dev/sda5           11762       14470    21760011   83  Linux
/dev/sda6           14471       14593      987966   82  Linux swap / Solaris


Since I don't have access to my original live cd, can I just download a new one?  And if I do, will it fresh install Ubuntu?  If possible, I'd like to keep Ubuntu with the programs and plugins that I've installed since I started running it.

---

### Post by raymondh on 2010-01-13
> **kudzu said:**
> Here's my partition information, raymondh:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13         274     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         274       11761    92274688    7  HPFS/NTFS
/dev/sda4           11762       14593    22748040    5  Extended
/dev/sda5           11762       14470    21760011   83  Linux
/dev/sda6           14471       14593      987966   82  Linux swap / Solaris


Since I don't have access to my original live cd, can I just download a new one?  And if I do, will it fresh install Ubuntu?  If possible, I'd like to keep Ubuntu with the programs and plugins that I've installed since I started running it.

Go ahead and burn a Ubuntu liveCD.  It will not install unless you tell it to (by clicking on the icon/selection INSTALL).  If you want to be sure and not make a mistake with any INSTALL icon, why nto download and burn a [live gparted cd.]("http://sourceforge.net/projects/gparted/files/").

What you will be resizing, in order, are

-sda4
-sda5

See the previous link about resizing reference.

Good luck.

Raymond

---

### Post by kudzu on 2010-01-13
Awesome, thanks.  I read the link you posted and I feel pretty prepared for the procedure at hand, but I still have one more question before I shut up and get to work: Will deleting Windows and resizing sda4 and sda5 leave me with an optimally sorted-out hard drive for my purposes of running Linux exclusively?  Is there anything else I can do, partition-wise, like what I've heard about making Linux the first partition, or sda1, I guess?

Thanks a ton for all your help so far.

---

### Post by raymondh on 2010-01-13
> **kudzu said:**
> Awesome, thanks.  I read the link you posted and I feel pretty prepared for the procedure at hand, but I still have one more question before I shut up and get to work: Will deleting Windows and resizing sda4 and sda5 leave me with an optimally sorted-out hard drive for my purposes of running Linux exclusively?  Is there anything else I can do, partition-wise, like what I've heard about making Linux the first partition, or sda1, I guess?

Thanks a ton for all your help so far.

Is this a fairly new install?  Do you have back-up (tested) of your files? How important is that DELL utility partition to you.

If you don't mind a new install, what you can do is tell ubuntu to install with option "use entire disk".  That will erase everything and re-install Ubuntu. 

If you want to keep your current ubuntu (as you originally wanted) ... proceed with your plan to erase windows and its' recovery partition and just enlarge the extended partition and then the ubuntu partition. 

As for being optimal, that is quite subjective.  I don't think the location will affect the speed/responsiveness that much to be noticeable. Also, it would not matter whether it be sda1 or sda5.

On a side note, I prefer to have my system files .... which we refer to as ROOT, also known as / (slash mark) .... separate from /home (where your user files and configurations reside).  That way, should I need to re-install because of any mishap, I just re-install the root whilst keeping /home intact.  Net effect is that my specific files and configuration remain intact with the new install. To do this will require either:

- creating the partitions beforehand and then manually installing unto them (my choice because I have more control over the process) or,
- separating /home after installing Ubuntu.

If you want to read up on that, here's a link by psychocats

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

And this is a reference read about the linux file system hierarchy for a better understanding about root and everything else.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

No worries on the questions.  Ask as much as you want/need :)  The best preparation is to get yourself comfortable and informed with the task at hand.

Raymond

---

### Post by kudzu on 2010-01-14
I appreciate your continued help with all of this newbness.   

I thought about what you said, about the "use entire disk" option, and from what I gathered from googling the matter, I decided leave my Dell partition intact, considering that I think I have my Dell disc back home, but I'm not exactly sure.  While doing that research I discovered that I was mistaken about thinking that I have a Windows disc at home, since apparently no Dells come with Windows installation disks, but merely recovery discs, like the kind that the link you provided earlier shows how to make.

So, I decided to go back to my original plan to shrink my Windows partition down as small as possible and then expand my Linux partition.  I followed the Vista partition tricks as outlined in the other link you provided, and then I went to shrink my partition but it would only allow me to shrink it by roughly 7GB, down to about 82GB total.  I tried it anyway and got an "Access Denied" message, even though I was using my administrator account.  I researched the matter and all I could find were posts that recommended using a third party partitioning program, like GPartEd.  

You said that you recommend using Vista to shrink my Vista partition - why is that you recommend Vista's partitioning program over GPartEd?

---

### Post by oldfred on 2010-01-14
Microsoft changed with Vista and 7 where it starts its partition. Everyone including XP started at 63 but Vista changed to 2048 which is not a cylinder boundary. With some versions of gparted it will move Vista to 63 and often cause boot problems. They should be solvable since you can install Vista in a XP partition that starts with 63 but many have issue and it requires repairs.

I would download a gparted liveCD and use it. Make sure to uncheck the round to cylinder.

Herman on Gparted old error and not in Ubuntu but still use Vista partitioner for safety:
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

I have seen where windows is not happy if it down not have at least 20% free space, so that should give you an idea of how small you can make it.

After editing the partitions, boot Vista several times. It will want to do some fixes like checkdisk since it will see that changes have been made.

---

### Post by kudzu on 2010-01-25
Thanks guys.  I used GParted and I think my partitions are pretty well sorted out now (I did decide to delete Windows, in the end).  I created a home partition, and I'm having some problems booting now, but the partitioning process seemed to go well aside from my own bone-headed mistake of making my /home partition too small and then copying more data from my /home folder than I had room for in my /home partition.  I created another thread for this problem, though, so I'm marking this thread as "solved."

---

