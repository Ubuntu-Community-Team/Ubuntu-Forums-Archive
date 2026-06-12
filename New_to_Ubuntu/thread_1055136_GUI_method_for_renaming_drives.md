---
title: "GUI method for renaming drives?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-01-30
Hi all!

In Nautilus, my various partitions & USB drives seem to get dumb names like "85.9GB Media" or "disk-1".

I thought I could just rename them to something convenient, but attempts get refused.

I started Googling & found complex methods with mtools & terminal & warnings...

Is there really no simple GUI method for renaming partitions & drives?

Thanks for any hints!

---

### Post by mikewhatever on 2009-01-30
Use Gparted if you need gui and change the Labels of your partition. The important thing is, you need to unmount the partition you are about to edit first.

---

### Post by sisco311 on 2009-01-30
EDIT: d'oh, stupid internet connection :) 

I think this tutorial is quiet straightforward: [uhelp]community/RenameUSBDrive[/uhelp]

You can use Synaptic to install mstools, ntfsprogs, e2label, ...
and gparted to change the labels.

---

### Post by jerome1232 on 2009-01-30
> **shipshape said:**
> There is another way I found out. Press Alt-F2 and type:
gksudo nautilus
This will temporarily allow you to browse as root. In the new Windows, browse to the /media folder. Right-click and unmount the drive. Delete the directory named as your current drive and create a new directory and name it as your new drive name. Then go to the /etc directory and copy and paste the fstab file and call the backup copy fstab_backup. Edit the fstab file and change /media/(your current hard disk name here) to /media/(your new hard disk name here).
Then go to Places > Computer and right-click and mount your drive.
Close the "browse as root" Nautilus window.

I think changing the file system label is much better route, more straightforward and doesn't require the editing of any system files.

---

### Post by 2CV67 on 2009-01-30
Thanks for the replies so far!

> **sisco311 said:**
> 
I think this tutorial is quiet straightforward: [uhelp]community/RenameUSBDrive[/uhelp]

You can use Synaptic to install mstools, ntfsprogs, e2label, ...
and gparted to change the labels.

That was the tutorial I was refering to when I said:
"I started Googling & found complex methods with mtools & terminal & warnings..."
 - About 150 lines of instructions, all terminal-based & mentioning:
> "This does not seem to work with 8.04 or 8.10, the mlabel command of mtools 3.9.11 does not know the -i switch. 
For 8.10 add something like drive p: file="/dev/sdb1" to /etc/mtools.conf then use sudo mlabel p:new_label
If you get a message like this:
Total number of sectors (7831520) not a multiple of sectors per track (63)!
You can easily ignore the check by running this command:
echo mtools_skip_check=1 >> ~/.mtoolsrc"

Sorry – we don't have the same idea of what constitutes a simple GUI tutorial!

I was hoping for something like:
 - Right click here.
 - Select "Rename"
 - Type new name.
 - Confirm.

It really is as non-straightforward as all those threads said, then?
Fortunately it is not really important, I have written on a bit of paper what the various drives are.
Surprising though…

---

### Post by jerome1232 on 2009-01-30
You can, in gparted, you need to make sure the required file system tools are installed (search in synaptic for mtools ntfsprogs and etc) and install them.

Then open up gparted, right click the parition you want to edit and click on label, change the label, and it's done.

---

### Post by 2CV67 on 2009-01-30
> **jerome1232 said:**
> You can, in gparted, you need to make sure the required file system tools are installed (search in synaptic for mtools ntfsprogs and etc) and install them.

Then open up gparted, right click the parition you want to edit and click on label, change the label, and it's done.

I'm missing something here...

The system tools are installed in a couple of Ubuntu partitions according to Synapt.

If I try to run GParted from a live CD (but then it doesn't have access to those tools, does it...) then I don't have a "Label" option in the drop-down list when I right click on a partition.
This is GParted version 0.3.2 from about 2006.

I also tried with last week's Remastersys live DVD copy of a Hardy installation (that installation has the tools) but I can't find GParted on that DVD & I ran as far as I dared into the installation program (just prior to wiping a partition...) without seeing anything about labels.

I don't see how to get GParted & those tools together anywhere.

Maybe it will look better in the morning...

---

### Post by boof1988 on 2009-01-30
> **2CV67 said:**
> If I try to run GParted from a live CD (but then it doesn't have access to those tools, does it...) then I don't have a "Label" option in the drop-down list when I right click on a partition.
This is GParted version 0.3.2 from about 2006.

One other option is to download the iso for [GPartEd LiveCD](http://gparted.sourceforge.net/livecd.php) and burn it to your desired format.  This LiveCd version has many of the capabilities of GPartEd already included.

This LiveCD is very slim but can be very useful.

---

### Post by 2CV67 on 2009-01-31
Well, I couldn't find how to do labelling from my old GParted 0.3.2 live CD - should it be possible?

But I installed GParted via Synapt into one of my Ubuntu set-ups (Intrepid), which already had the various tools installed.

The good news is that I very easily re-labelled one drive to "LTS Ubuntu Drive" just by right-clicking, selecting "Label", typing in the new name & "Apply".
It appeared with the new label in GParted & in Nautilus & everythings worked just fine. :D

Next, I re-labelled another partition "XP Drive" & that worked just fine too.
The new labels show up in the main Ubuntu & the LTS Ubuntu & XP...
Impressive!

The bad news is that I lost a partition...
I have (had?) a logical FAT32 partition shown as /dev/hda5 (or /dev/sda5) which is shared between XP & Ubuntu.
GParted showed it mounted at /windows.
I unmounted it in GParted, re-labelled it "SHARE Drive" & could not see how to re-mount it via GParted.
Can you?
I thought I could just click on it in Nautilus & all would be well.
But it does not show up in Nautilus any more!
All the other drives, mounted or not, re-labelled or not, are there OK & can be mounted/unmounted OK.
After a reboot, "SHARE Drive" shows up in GParted with its new label & mounted at /windows again, but is still invisible in Nautilus.
The contents of that drive are present directly in the folder /windows.

If I boot to "LTS Ubuntu" then "SHARE Drive" shows in Nautilus & is located in /media (?).

I am lost!

Thanks for any help, to finish off something that was beginning to look good!

---

### Post by 2CV67 on 2009-02-01
Still scratching my head over this.

Why don't I see my newly-labelled "SHARE Drive" in Nautilus any more?

It appeared OK before I relabelled it (As "5.07GB Media" or something similar).
Surely it should be there?

Attached screenshots of Nautilus (without) & GParted (with)...

This is fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 /home           ext3    relatime        0       2
# /dev/sda5
UUID=48A5-D628  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Any ideas?

Thanks!

---

### Post by Captain Legless on 2009-02-01
I've been following this thread as I'm trying to do the same thing.

I've been successful at changing the labels on one HDD and they show up with the new label in GParted BUT they remain the same i.e Local Disk (two of them) & 21GB Media in Nautilus.

How do I rename them so they  show up with the new labels in Nautilus?

---

### Post by Devport on 2009-02-01
I am not sure if it is capable of doing it for external media but you can setup conditions like serial to give certain partitions a static, labeled mountpoint.

Install pysdm. Setup dynamic configuration rules to match your partition(s).

Be careful since it will change /etc/fstab.

That will not change the partition labels but the names you see in nautilus.

Sorry if it is not useful for your task.

---

### Post by ugm6hr on 2009-02-01
> **2CV67 said:**
> After a reboot, "SHARE Drive" shows up in GParted with its new label & mounted at /windows again, but is still invisible in Nautilus.
The contents of that drive are present directly in the folder /windows.

If I boot to "LTS Ubuntu" then "SHARE Drive" shows in Nautilus & is located in /media (?).

I am not an expert on fstab, but I suspect that nautilus sees it just fine.

Presumably you can still access the files there in /windows?  Perhaps just deleting the reference to /windows in fstab will auto-mount it to /media/"SHARE Drive" as you might expect.

This explains why booting to your LTS installation of Ubuntu mounts it differently (since that probably does not have a modified fstab).

Essentially, Nautilus does not see it as a separate drive, merely a folder within / (/windows) due to its fstab entry.

---

### Post by Captain Legless on 2009-02-01
This is crazy and I feel like I'm messing you guys around but after a couple of reboots and bit of general messing around doing nothing in particular, the labels I assigned in GParted are now being displayed in Nautilus!!!!!!!#-o

Don't ask me how this has happened - it just did!

I hope CV67 sorts his problem out too.

Now I've got to try and see if I can merge two Linux partitions and two Linux-swap files. :-\":roll:

---

### Post by 2CV67 on 2009-02-01
Well I tried many reboots & lots of messing about, but still no progress!

> **ugm6hr said:**
> I am not an expert on fstab, but I suspect that nautilus sees it just fine.

Presumably you can still access the files there in /windows?  Perhaps just deleting the reference to /windows in fstab will auto-mount it to /media/"SHARE Drive" as you might expect.

This explains why booting to your LTS installation of Ubuntu mounts it differently (since that probably does not have a modified fstab).

Essentially, Nautilus does not see it as a separate drive, merely a folder within / (/windows) due to its fstab entry.

You are probably right that Nautilus is seeing it "just fine" but that still leaves me wondering what happened between when I could see "5.07GB Media" in the Nautilus side panel & now when I cannot find it at all.
It has always been shown as mounted at /windows.

Certainly all the contents are OK & are being read automatically by applications, so no need for panic.

Assuming I would prefer to have it in /media rather than in /windows, just so I can see it & access it easier - then how can I reset the mount point? ( by GUI - I am a fanatic!).
Presumably (??) if I could see the drive in Nautilus, I could drag it from /windows to /media (could I?) but as I can't see it at all...

---

### Post by ugm6hr on 2009-02-01
Either:

Delete (or add a # to the start of) the line in fstab referring to /windows - this will have to be done with gedit manually

Or

Just create a shorcut to /windows in Nautilus by dragging the /windows to the bottom left pane.

---

### Post by 2CV67 on 2009-02-02
Thanks very much, ugm6hr, for those 2 suggestions.

I tried them both & they both work - to some extent.
> Just create a shorcut to /windows in Nautilus by dragging the /windows to the bottom left pane.
That's my kind of GUI operation!
I then get an entry "windows" which I can easily rename to anything else, like "Shared Drive" for instance. 
I can access the contents in 1 click from there.
The drive is always mounted, which is what I need.
I will probably stick with that, but just have some philosophical reservations about a link called Shared Drive which points to a folder called windows which seems to contain a bunch of stuff which I know (so long as I remember) is actually in a partition labelled "SHARE Drive" which is totally invisible!

> Delete (or add a # to the start of) the line in fstab referring to /windows - this will have to be done with gedit manually
I instinctively & deliberately avoid this kind of operation, since one slip of the finger can wreak such havoc!
My first attempt stupidly disabled my /home partition, which is not a good thing....
When I got the # in the right place (I understood where to put it, just slipped up the first time) then nothing seemed to happen until I rebooted, when I was delighted to see "SHARE Drive" in Nautilus, just like I wanted & expected last week!
Two snags:
1. It doesn't auto-mount now (I am Googling to try to fix that).
2. The applications which feed off that drive seem to need to be redirected manually...
Not sure I will persist with that - it seems a lot of hassle just to rename a drive.

Windows behaved just like I imagined Ubuntu was going to - after making the changes in GParted, the drives show their new names in Windows Explorer with no functional interference.
Sigh...

Thanks again for all the good suggestions!

---

### Post by 2CV67 on 2009-02-02
Anybody tried Webmin for this job?
[http://www.webmin.com/index.html](http://www.webmin.com/index.html)

They say:
>  To label an existing filesystem, follow these steps :

   1. On the main page of the module, click on the number of the partition that you want to label. This will take you to the partition editing form, as shown in Figure 8-3.
   2. Assuming the partition is not currently in use, you will be able to enter the new label into the Partition label field. It must be at most 16 characters long - for example /home or root.
   3. After you have entered the label, click the Save button. It will be stored in the filesystem, and the browser will return to the module's main page.
   4. At this point, the Disk and Network Filesystems module can be used to mount the labeled filesystem by label name, as explained in chapter 5. 

Looks GUI & promising, but I suppose it could be a whole new can of worms - starting by the fact that it's not in Synapt...

---

### Post by 2CV67 on 2009-02-02
> **Devport said:**
> I am not sure if it is capable of doing it for external media but you can setup conditions like serial to give certain partitions a static, labeled mountpoint.

Install pysdm. Setup dynamic configuration rules to match your partition(s).

Be careful since it will change /etc/fstab.

That will not change the partition labels but the names you see in nautilus.

Sorry if it is not useful for your task.

Thanks for that suggestion, which I missed somewhere along the way.

I installed PySDM & opened it, but was surprised it did not seem to produce a good initial scan of the drives.
It listed sda1 sda2 etc but when I tried to see details it asked to "Configure" the drive, which worried me.
Then it seemed to be very confused between the drives, so for the moment I put it back in the box...

In Googling, I discovered Disk-Manager & MountManager, which are both in Synapt too.
As far as I could see, Disk-Manager has no Label information or capability?
MountManager impressed me as good GUI philosophy, automatically generating backup files & allowing 1-click restoration. :D
It sees Labels correctly but I couldn't find any facility for setting or changing Labels with it.

To be continued...

---

### Post by ugm6hr on 2009-02-02
> **2CV67 said:**
> 1. It doesn't auto-mount now (I am Googling to try to fix that).
2. The applications which feed off that drive seem to need to be redirected manually...

Is the Share Drive an NTFS partition?

If so - you can (easily) solve 1. by installing [ntfs-config]("apt:ntfs-config") which gives you a GUI in the menu to allocate mounting options.

Unfortunately, this default automounts in /media too, so 2. would still be a problem.

---

### Post by jerome1232 on 2009-02-02
You could just slap symbolic link at /windows that points to the new mount point.

--edit-- oops wrote my command backwards!

```
sudo ln -s /media/new_mountPoint /windows
``` 

(am I the only one that thinks these gui tools are actually harder to use?)

---

### Post by ugm6hr on 2009-02-02
> **jerome1232 said:**
> You could just slap symbolic link at /windows that points to the new mount point.

```
sudo ln -s /windows /media/new_mountPoint
``` 

Do symbolic links work for non-linux partions?

---

### Post by jerome1232 on 2009-02-02
The smbolic link is on a linux partition, I certainly hope his root partition isn't a microsoft partition, because that's where the symbolic link is being placed at.

---

### Post by ugm6hr on 2009-02-02
> **jerome1232 said:**
> The smbolic link is on a linux partition, I certanily hope his root partition isn't a microsoft partition, because that's where the symbolic link is being placed at.

So you can link from any Linux partition to any partition at all.  Good to know (shameful I didn't already!).

In which case - this is definitely a good solution.

Unfortunately, while symbolic links can be created by GUI, to place it in / requires "sudo" privileges, which means you have to launch nautilus by typing "gksudo nautilus".

---

### Post by jerome1232 on 2009-02-02
> **ugm6hr said:**
> So you can link from any Linux partition to any partition at all.  Good to know (shameful I didn't already!).


Oh yeah I didn't quite understand your question :oops:

The symbolic link can definitely point to any partition at all I do this quite frequently with ntfs partitions. (have a symbolic link point at them not in them, I actually haven't tried the latter before)

---

### Post by 2CV67 on 2009-02-03
I have been watching this good conversation while looking & wondering myself...

> **ugm6hr said:**
> Is the Share Drive an NTFS partition?

If so - you can (easily) solve 1. by installing [ntfs-config]("apt:ntfs-config") which gives you a GUI in the menu to allocate mounting options.

Unfortunately, this default automounts in /media too, so 2. would still be a problem.

No, my shared drive is FAT32.
I think I can use MountManager to change my mount point to /media & to define auto-mount, all in a (relatively)safe GUI fashion with 1-click restore facility, can't I?

I am playing with symbolic links which look like a feasible solution to connecting the dots.
I managed to understand this last year when I set up the Shared Drive & got my Firefox Scrapbook Add-ons in Ubuntu & in XP to both work with data in the shared drive, but just how I did it....

As a supplementary question, am I right in thinking that my Drive will show up in Nautilus if it's mounted at /media, but not if mounted at /windows or at /mnt?
And that if it shows up in Nautilus (which I want) then it will also unavoidably show up on Desktop (which I would avoid if I could)?

By the way, this is no longer a "problem" but I am trying to get to the bottom of it while I am there!

Thanks again for all the good help in this thread - as usual here! :D

---

### Post by 2CV67 on 2009-02-03
Having trouble with Symbolic Links.

Playing around on Desktop, creating files, making links, looking at emblems (arrow on links), looking at properties (links say they are links & show what they point at) - everything is very clear & simple.

Trying to backtrack to my Scrapbook data is just not clear at all.

See screen shots of Scrapbook data folder accessed in Nautilus via the Shared Drive ( /windows/ScrapBook MAIN) & via my .mozilla/firefox/profile/ScrapBook file.
Looks the same & is the same (I just checked that fresh data is syncronized).
I KNOW the real data is in /windows and I am 99% sure that what I see in .mozilla is due to a symbolic link pointing to /windows/ScrapBook MAIN, which I put there some months ago.
But I cannot find any sign of symbolic links now.
Folder properies for ScrapBook in .mozilla (which should be a link??) suggest it is a real folder, don't they?
How should I be able to see which files/folders are links?
Shouldn't they have big arrows?

My brain hurts!

---

### Post by ugm6hr on 2009-02-03
Show a screenshot of the folder with the link in it, not the linked folder contents (if that makes sense).

i.e. you want to be looking at Scrapbook (assuming this is what you named your link as).

---

### Post by 2CV67 on 2009-02-03
Guys, I've been wasting your time today! :oops:  Sorry...

I dug deeper into the Scrapbook folders & found the one in /.mozilla... was full of old junk, so I (carefully) removed items then even the ScrapBook folder & everything still works 100%.

Finally I tracked down the ScrapBook home site Troubleshooting page: [http://amb.vis.ne.jp/mozilla/scrapbook/misc.php?lang=en](http://amb.vis.ne.jp/mozilla/scrapbook/misc.php?lang=en)
Where it says:> I don't want to store collected data in my profile folder. I want to change the destination to store data.

First, move entire 'ScrapBook' folder to your favorite location. Then go to [Tools] > [Settings] > [Advanced], configure the [Destination to Store Data].

Actually you need to go Firefox > Tools > Add-ons > ScrapBook > Preferences > Organize > Location to Store Data > Save Data To...
but then it's easy!

I really don't remember being there before, but that's certainly how it is now - no Symbolic Links required.

So now I think I can remount my Shared Drive (in MountManager) then re-couple ScrapBook as above.

Any comment on > As a supplementary question, am I right in thinking that my Drive will show up in Nautilus if it's mounted at /media, but not if mounted at /windows or at /mnt?
And that if it shows up in Nautilus (which I want) then it will also unavoidably show up on Desktop (which I would avoid if I could)?

Apologies again!

---

### Post by jerome1232 on 2009-02-03
That's right, drive's only show up as "drives" in nautilus if they are mounted under /media or under your home directory. 

If you mount them anywhere  else they will seem like a regular folder.

---

### Post by 2CV67 on 2009-02-03
OK - I'm all done.

Half a week to change a couple of Drive Labels...

I tried using MountManager to change the mount point & it said it had changed it to /media/ & fstab showed it changed, but when I shut down Mount Manager I was back to /windows.
Even after reboots.
And several attempts - really not clear what to click to apply changes - I thought "Apply" was a good guess, but no...

Then I tried Disk-Manager & that was simpler except when I tried to mount to /media I was told "wrong mount point. /media already in use".
More headscratching to deduce I needed to invent a new file inside /media to mount to.
That may be obvious to you, but not to me yet.

SHARED Drive now appears as such in Nautilus & auto-mounts.

Redirecting ScrapBook to the right folder seemed easy!

The end!

Oh - I also have a USB Flash Drive to re-label, but not tonight...

GUI has some way to go on drive labeling.

Thanks for all your help on this surprising marathon!

---

### Post by 2CV67 on 2009-02-04
AAAAAAAAAGGGHHHHH!!!!!

This morning I felt strong enough to rename my USB Flash Drive, which appears as "16.0GB Media" in Nautilus & Desktop.

So I opened GParted - 5 minutes wait while it "scans all devices"
Selected /dev/sdg
Selected /dev/sdg1
Unmount - 5 minutes wait again
Label - "SanDisk" - Apply - Apply - 5 minutes wait again
No change in Nautilus or Desktop
Unmount & remount - no change
Reboot - no change
Remove & replace Flash Drive (why does Unmounting in Ubuntu leave the LED on while "Remove device" in XP turns it off?)
Bingo - it now calls itself SanDisk in Nautilus & Desktop.
Mission Accomplished at last!

I rebooted to XP to confirm XP also sees it as SanDisk now - OK.

I idly right-clicked on it in Windows Explorer & noticed an option "Rename".......
So I clicked on it & renamed it something else - instantly.
While I was there, I renamed all the other drives I spent a week renaming in Ubuntu - instantly.
Rebooting to Ubuntu - they are all renamed to what I just did in XP!
Not only was it instant, it was simple, GUI & RISK-FREE whereas the Ubuntu methods had me on the edge of wrecking my system.

Moral: The best GUI device for relabelling any drive Windows can see is Windows Explorer.

Ubuntu-ists: I think this is a matter for deep shame!!

Can somebody please correct this anomaly?

---

### Post by ugm6hr on 2009-02-04
> **2CV67 said:**
> Moral: The best GUI device for relabelling any drive Windows can see is Windows Explorer.

Unless naming at the time of formatting, I always use Windows to rename.

I agree that renaming drives is something that can be useful, and a GUI extension for nautilus would be nice...

---

### Post by jerome1232 on 2009-02-20
So today I was helping in a thread and noticed that apparently Nautilus CAN rename file systems, at least the option is there but It gives me the error "operation not supported by backend" so maybe there's something that needs to be installed to get it working I'm not sure. I'm sure it couldn't be that hard for nautilus to call up the right filesystem tool to rename the partition.

See screenshot to see what I'm talking about.

---

### Post by 2CV67 on 2012-02-15
Haven't looked at this for some time, but now it is easy!

Accessories > Disk Utility > Click on Drive > Edit File System Label

That's all!

Call this [SOLVED]

---

