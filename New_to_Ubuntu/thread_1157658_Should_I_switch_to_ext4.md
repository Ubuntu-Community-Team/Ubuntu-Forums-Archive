---
title: "Should I switch to ext4?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Walter Melon on 2009-05-12
Hello all, 
I'm thinking about doing a fresh install of 9.04 from 8.10 and I was wondering if there had been any bugs with ext4?  Are there any noticeable improvements over ext3?

A thorough search on this topic has lead me to understand that boot time with ext4 significantly reduced.  But this has gotten me worried:> Ubuntu 9.04 and later include ext4 as a manual partitioning option at installation time, including support for ext4 as the root filesystem.

For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, Ubuntu chose to make this decision for some unknown reason. For other versions of Ubuntu, the patch that was applied can be found here. source: [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Is this something I should be concerned about?

Thanks

---

### Post by LowSky on 2009-05-12
Its running fine on my PC without these patches... actually never heard of such issues.

You can always keep your /home partition as EXT3, that way you data is ona more stable (known) formate, while the rest is on EXT4 foor quick boots

---

### Post by deepclutch on 2009-05-13
I have upgraded for past 2 releases of Ubuntu(from hardy to intrepid to jaunty).I converted to ext4 filesystem via  a 2.6.29 kernel based "parted" live cd(88MB).You can also try the same.BTW ,here is the thread:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)
[http://ubuntuforums.org/showpost.php?p=7263762&postcount=37](http://ubuntuforums.org/showpost.php?p=7263762&postcount=37)

---

### Post by lovinglinux on 2009-05-13
You should read this: [Ext3 and Ext4: Which file system to install?](http://ubuntuforums.org/showthread.php?t=1133719)

My personal experience with ext4 has been great so far. I was experiencing performance issues while keeping one drive with ext4 and another with ext3 partitions. The performance improved considerably after making all partitions ext4. I didn't lost anything so far, even after a power failure or after running into an fsck issue. I also restored grub several times while testing Windows 7 and other distros.

---

### Post by mprince on 2009-05-13
I would say stick with ext3, for now. Better to be safe than sorry.

---

### Post by Endolith on 2009-05-20
> 1) There have been reports of crashes having corrupted configuration files and sometimes more with Ext4 in use.

2) This has been addressed in kernel 2.6.30, however it will not hit Ubuntu Jaunty, but Ubuntu Karmic.> [B]
Lock-ups when deleting files from ext4 filesystems[/B]

  In some cases, deleting files from an ext4 filesystem is reported to cause soft lock-ups in the kernel ([330824]("https://bugs.launchpad.net/bugs/330824")). Investigation of this problem is ongoing, and it is expected that a fix for this problem will be made available as a post-release update. To avoid this problem, users may wish to install using the default ext3 filesystem and convert their filesystem to ext4 (as documented on the [ext4 wiki]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")) once a fix is available. 

**Switching to ext4 requires manually updating grub**

  If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the [ext4 wiki]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")), then you *must* also use the grub-install command after upgrading to Ubuntu 9.04 to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot. 
 [B]
Possible data-loss problems resizing ext4[/B]

  The resize2fs tool may cause data loss when growing or shrinking ext4 filesystems off-line. See [this mail from the upstream maintainer]("http://article.gmane.org/gmane.comp.file-systems.ext4/12763") for more details. Unfortunately we became aware of this too late to fix it in Ubuntu 9.04. If you wish to resize an ext4 filesystem using the tools in Ubuntu 9.04, you may be able to work around these problems by first disabling the flex_bg and uninit_bg features (do not attempt this on a mounted filesystem!): 
 
tune2fs -O ^flex_bg,^uninit_bg /dev/DEVICE_NAME
e2fsck /dev/DEVICE_NAME 

However, we still strongly recommend taking significantly more care with backups than usual before attempting to resize an ext4 filesystem.If there are still known bugs, then I'm sure not using it.  I fully expect there to be *unknown* bugs even after they say it's stable. Some improved performance isn't worth the risk.  

We can always upgrade the filesystem later, right?  We can convert an EXT3 to an EXT4 after the bugs are ironed out?

---

### Post by jbruced on 2009-05-20
No problems here, I just chose ext4 during install.

---

### Post by Cammy on 2009-05-20
> **jbruced said:**
> No problems here, I just chose ext4 during install.

Same here, and performance is quite phenomenal.

---

### Post by Endolith on 2009-05-20
> **jbruced said:**
> No problems here, I just chose ext4 during install.

The problem isn't with installing EXT4.  It's with EXT4 becoming corrupt during use and losing all your data.   Good luck!

---

### Post by MontelEdwards on 2009-05-20
Well i would not recommend it with a server.
I personally have not found *any* problems with it
it is extremely good and fast. I would deffenitly recommend installing it.

---

### Post by 73ckn797 on 2009-05-20
> **Endolith said:**
> The problem isn't with installing EXT4.  It's with EXT4 becoming corrupt during use and losing all your data.   Good luck!

I personally would not recommend it. I have had several issues. When I would reformat back to ext3 the drive still had problems. I had to perform a hard drive zero pass wipe and reformat before whatever the ext4 was doing to my drives disappears. That was on several fresh installs using 2 good disks. Currently will stay with ext3.

---

### Post by MontelEdwards on 2009-05-20
> **73ckn797 said:**
> I personally would not recommend it. I have had several issues. When I would reformat back to ext3 the drive still had problems. I had to perform a hard drive zero pass wipe and reformat before whatever the ext4 was doing to my drives disappears. That was on several fresh installs using 2 good disks. Currently will stay with ext3.
Dont you think that there may of been something wrong with your drive then EXT4 because it should of not done anything when you reformatted.

---

### Post by theozzlives on 2009-05-20
I use Ext4 on my whole drive on my laptop, on my server... Ext3 /home and Ext4 /. Haven't had a problem. Every file system has its faults, that's one of the reasons you BACKUP.

---

### Post by logos34 on 2009-05-20
> **Endolith said:**
> There are also three problems listed at [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

If there are still known bugs, then I'm sure not using it.

Can anyone confirm if these bugs are still outstanding/unresolved/unpatched?

---

### Post by MontelEdwards on 2009-05-20
> **logos34 said:**
> Can anyone confirm if these bugs are still outstanding/unresolved/unpatched?
I think that a lot of them have been patched. 
I dont know, but i have had *none* of those problems

---

### Post by Endolith on 2009-05-20
"I'm using it and I haven't seen any problems!" isn't particularly reassuring.  It says the problems aren't going to be fixed until Karmic.  I'm not entrusting something as important as the filesystem to some half-baked patches or forum threads.

---

### Post by 73ckn797 on 2009-05-20
> **MontelEdwards said:**
> Dont you think that there may of been something wrong with your drive then EXT4 because it should of not done anything when you reformatted.

NOPE. One drive was brand new which replaced another that I thought was failing. Turned out to be corrupted due to ext4. I performed a zero pass format, installed into another box and installed 9.04 w/ext3 with no problems at all. After the zero pass format the drive checked perfect. Before, any fsck or chkdsk showed results of having bad sectors. That was on both drives I refer to.

Both drives are Western Digital 160GiB.

I decided it was more time than I wanted to spend to figure out what was going on beyond the obvious issues. 9.04 is very good with ext3 on my systems. I am running it on 3 boxes and my laptop.

---

### Post by Endolith on 2009-05-20
> **73ckn797 said:**
> NOPE. One drive was brand new which replaced another that I thought was failing. Turned out to be corrupted due to ext4. I performed a zero pass format, installed into another box and installed 9.04 w/ext3 with no problems at all. After the zero pass format the drive checked perfect. Before, any fsck or chkdsk showed results of having bad sectors.


That could still be a bad drive.   Did you check SMART data for re-allocated sectors?  Run badblocks -nv?

---

### Post by 73ckn797 on 2009-05-20
> **Endolith said:**
> That could still be a bad drive.   Did you check SMART data for re-allocated sectors?  Run badblocks -nv?

Both drives were perfectly good until I formatted to ext4. That is when the problems began appearing. Once I performed the things previously mentioned, the problems went away. I have been back and forth with fresh installs using ext4. There is another thread where I discuss in more detail what was going on.

[http://ubuntuforums.org/showthread.php?p=7312366#post7312366](http://ubuntuforums.org/showthread.php?p=7312366#post7312366)

---

### Post by 73ckn797 on 2009-05-21
> **Endolith said:**
> That could still be a bad drive.   Did you check SMART data for re-allocated sectors?  Run badblocks -nv?


I ran badblocks -nv before I left to work. When arriving home it was still running and had listed over 60 block number sequences. The drive has also began to make a slight and consistently repetitive squeak type noise. I disconnected the drive to eliminate that as the source of the noise and the noise went away. I did not document the results of the badblock test. The drive seemed to have hung and in over 30 minutes it did not generate any more numbers. It was at that point that I removed the drive. I am still within the 30 day return policy and will exchange the drive.

---

### Post by Endolith on 2009-05-21
> **73ckn797 said:**
> The drive seemed to have hung and in over 30 minutes it did not generate any more numbers.

Well if it didn't have bad blocks, it wouldn't look like it was doing anything at all, except that the drive light would be on.  But it doesn't display anything on the screen until the end of the test, and I don't remember the drive making much noise, since it's not seeking all over the place, just writing and reading each sector in order.  If it does display numbers, then there are bad blocks.  SMART will have a bunch of errors logged in that case (I had 1076 errors on mine :) ).

---

### Post by 73ckn797 on 2009-05-21
> **Endolith said:**
> SMART will have a bunch of errors logged in that case (I had 1076 errors on mine :) ).

Does it generate a log file? I did not see one in the /etc/smartmontools/ folder. I will look around further. I actually aborted the check since it had been running all day (8 hours at least).

---

### Post by 73ckn797 on 2009-05-21
> **Endolith said:**
> Well if it didn't have bad blocks, it wouldn't look like it was doing anything at all, except that the drive light would be on.  But it doesn't display anything on the screen until the end of the test, and I don't remember the drive making much noise, since it's not seeking all over the place, just writing and reading each sector in order.  If it does display numbers, then there are bad blocks.  SMART will have a bunch of errors logged in that case (I had 1076 errors on mine :) ).


Installed the graphical smartmontools app and ran the short test, twice, which immediately confirmed a failing drive.

See attached screenshot.

---

### Post by Noah_Kapiolani on 2009-05-21
My 2 cents:  Because i am a 3 year newbie to Linux, and read all those scary quotes on data corruption and locking up, as well as the advice from those much more knowledgable than I,  I will therefore recommend sticking with ext3 for storage drives to anyone who is more clueless than I am and would be furious at a self-inflicted major data loss  However, i am trying out the separate boot drive (sda1) as ext4 and am impressed.  Lastly, i finally have listened to the posters that type BACKUP in capital letters.  They are not kidding.  The probability of a hardrive failure is 1.0 given an unknown amount of time.  However, be careful what you trust to back your data up.  I have 2 Western Digital external USB drives, 250 G and 500 G, that were my backup and both failed in about a years time.  Stay away from those.  Now i just buy internal drives, (Seagate which i hope will be better) and copy everything to another drive and put it in a box. It may not be pretty, but it is better than trusting a beautiful black and shiny external USB drive because from what little i can gather on reading various reviews on here and newegg, the external USB hard drives, especially Western Digital, seem to have a much higher failure rate although you certainly can find many individuals who will tell you that they have one and have had no problems, but two in a row failed on me. Your mileage may vary.

---

### Post by Endolith on 2009-05-21
> **73ckn797 said:**
> Does it generate a log file? I did not see one in the /etc/smartmontools/ folder. I will look around further. I actually aborted the check since it had been running all day (8 hours at least).

No, you do something like smartctl --all /dev/sda and it will list the last five errors at the bottom. The drive logs the last five internally.

> **73ckn797 said:**
> Installed the graphical smartmontools app and ran the short test, twice, which immediately confirmed a failing drive.

Yeah Gsmartcontrol is good.

---

### Post by wbee on 2009-05-21
Hello,
 
I read the same notes referred to earlier.

My understanding is "4" has a new way to put contiguous data onto a hard drive,with less chance of fragmentation.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

That said,when I did a clean install of JJ,I switched from 3 to 4 without any problem at all.

My booting is NOT any faster,but then again,my drive is fairly clean and I use the 32 version,not the 64 version of JJ.

---

### Post by 73ckn797 on 2009-05-21
> **Endolith said:**
> No, you do something like smartctl --all /dev/sda and it will list the last five errors at the bottom. The drive logs the last five internally.



Yeah Gsmartcontrol is good.

Thanks for the heads up on that tool. I was not aware of it but only the others I mentioned. Now I am considering whether to create a bootable disk to have that as a diag tool. Eliminates guess work and as an auto mechanic, having the right tools makes any job easier.

If there was still a "Thanks" button I would press it for you.

---

### Post by Endolith on 2009-05-21
> **73ckn797 said:**
> Thanks for the heads up on that tool. I was not aware of it but only the others I mentioned. Now I am considering whether to create a bootable disk to have that as a diag tool. Eliminates guess work and as an auto mechanic, having the right tools makes any job easier.

I usually use [System Rescue CD]("http://www.sysresccd.org/Main_Page"), but for last time I had to do all this, I made a USB stick with [portablelinux]("http://rudd-o.com/new-projects/portablelinux") so I could save stuff to it, install SeaTools permanently, etc.  You can actually boot most of the System Rescue CD disk images from grub on the USB stick, so that's good too :)

> If there was still a "Thanks" button I would press it for you.

[http://brainstorm.ubuntu.com/idea/13046/](http://brainstorm.ubuntu.com/idea/13046/)

---

