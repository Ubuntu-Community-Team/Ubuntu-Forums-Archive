---
title: "ABOUT:  Bad sectors on a hard drive"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-14
Ubunteros,

I have a Ubuntu 8.04 LTS Desktop Edition (64-bit) CD.

The question I have is this. When I use this particular CD to install Ubuntu 8.04 will Ubuntu during the install process recognize any possible bad sectors on the hard disk drive and mark them so information is placed there?

Second question. As Ubuntu installs the o/s it is also formatting in ext3 at the same time isn't it?

Thanks for your helping!

---

### Post by audiomick on 2010-03-14
Hallo,
regarding possible bad sectors, I am confident that the installer is able to detect bad sectors, but I **don't** know this for sure. I seems logical to me that it must. There is no point in installing to a faulty drive, so it is a fairly basic requirement for the installer to check, isn't it?

If you are concerned about your drive, you might want to run smartmontools across it before you start the install.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
This reads out the usage info that the drive itself generates.

Regarding your question about file system: Yes, as long as you haven't specified something else the 8.04 installer will format to Ext3 as it is installing. Just for your info: Ubuntu changed to Ext4 with 9.10.

---

### Post by srs5694 on 2010-03-14
There are two types of bad-sector checks on modern hardware: Those handled by the hard disk itself and those handled by system software (the OS or its utilities). The checks handled by the hard disk are done no matter what, and clear up the vast majority of problems on anything but very dodgy hardware by replacing bad sectors with good ones from a set of "spares" that the manufacturer created. System software checks are another matter, though....

System-software bad-sector checks are optional with most filesystem creation tools in Linux. The Ubuntu installer presents a front-end to these tools, but I don't recall offhand if it provides an option to do bad-sector checks. I'm 99% positive that these checks are *not* done by default, since they would significantly slow down the installation process -- it could take hours just to create a filesystem on a big modern hard disk.

Personally, I wouldn't install any OS on any hard disk that I suspected might be going bad. By the time the drive's firmware can no longer detect and correct for bad sectors, the drive is most likely failing in a big way, and new bad sectors are likely to crop up in the future. If I had a question about this, I'd use a manufacturer-supplied disk-test tool to check the disk's status, and if it suggested problems, I'd trash the drive.

As to formatting, I'd say that the installer creates a filesystem *before* installing the OS, not "at the same time" as the OS is installed. The "at the same time" terminology could be used if you're just looking at the whole installation process as a single operation, in the sense that you don't need to create the filesystems before you launch the installer.

---

### Post by suomalainen on 2010-03-14
Thank you all for your advice and support!!!!

Attached are three pictures I took when a few days ago, I was trying to boot up Ubuntu to no avail. I have no idea what these lines mean and if they indicate a HDD failure. This same issue happened 2 months ago but Ubuntu seemed able to fix the problem after multiple bootup attemps and then everything was ok....

Can you make heads or tails from these pics???

Thanks

---

### Post by Paqman on 2010-03-14
Your hard drive manufacturer should have tools on their website that will enable you to run a variety of SMART tests on the drive, if you're concerned about the drive, do a good long test. Later versions of Ubuntu also contain a utility that will allow you to see the actual SMART data of the drive, so you can see how many bad sectors you have, and whether the drive has sorted them out.

In general a small number of bad sectors is normal for a drive that's been in use for a while. It's expected, and the drive itself will handle it without any help from the OS.

---

### Post by audiomick on 2010-03-14
> **Paqman said:**
> ...Later versions of Ubuntu also contain a utility that will allow you to see the actual SMART data of the drive...
That is what that smartmontools application that I mentioned in post #2 does.

---

### Post by carandraug on 2010-03-14
> **suomalainen said:**
> Thank you all for your advice and support!!!!

Attached are three pictures I took when a few days ago, I was trying to boot up Ubuntu to no avail. I have no idea what these lines mean and if they indicate a HDD failure. This same issue happened 2 months ago but Ubuntu seemed able to fix the problem after multiple bootup attemps and then everything was ok....

Can you make heads or tails from these pics???

Thanks

This reminds me of an old problem I had when Installing Ubuntu on a very old computer than was given to me (it's kinda of a trend here, really. Their computers get old or broken (and by broken I mean they got a virus and decide to buy a new one) so they give them to me). I asked for [help on this forum too]("http://ubuntuforums.org/showpost.php?p=5607954&postcount=1").

In this case I thought it really was broken and decided it was more hassle than it was worth and left in a corner. One day I may pick it up again. The theory of really being broken, or at least not being worth to fix, was also mentioned later by [another user who seemed very knowledgeable]("http://ubuntuforums.org/showpost.php?p=6110801&postcount=8").

Another user mentioned that it was most likely  a[bug in the kernel]("http://ubuntuforums.org/showpost.php?p=6348022&postcount=14") and I mustagree with his reasoning.

---

### Post by quadproc on 2010-03-14
You received some good input from other posters and I wanted to add one thing: version 8.04 defaults to the ext3 file system but you have many other possible choices when you are creating the file system(s).  For example, you could select ext2, NTFS, or any of several others.  If you need to interact your Ubuntu system with a Windows dual boot system then you may want to choose one of the Microsoft compatible file systems instead.

Additional note: beginning in Ubuntu 9.10, the default file system is ext4 but you still have the option of choosing ext3 or any of the remainder of the older filesystems.  Since ext4 is reputed to sometimes corrupt a disk, you may wish to avoid it until a fix for this problem is announced.

quadproc

---

### Post by audiomick on 2010-03-15
> **quadproc said:**
> ...select ext2, NTFS, or any of several others.  If you need to interact your Ubuntu system with a Windows dual boot system then you may want to choose one of the Microsoft compatible file systems instead.

For a partition which is to be accessible from a Windows and an Ubuntu install, true. The Ubuntu system itself must be on a partition(s) formatted with a Linux file system

---

### Post by suomalainen on 2010-03-15
Thanks everyone for the great support!!! Really, Thank you!!!

If I understand correctly, and as is in my case, Ubuntu 8.04LTS must be in the ext3 file system. If I understand the process correctly, when I do an install using the Live CD Ubuntu will automatically choose the filesystem it needs to do business in and format in ext3.

OR..... If the HDD has already been pre-formatted to say NFTS does it leave that in place and begin the install process?

As a FYI. I have 3 mobile racks in my system. Each contains a 500GB HDD with 1 o/s. XP, 2000, Ubuntu. Each time I want to use an Operating system I power down the PC and turn on the key to the rack with the o/s I want to use and then power up again.

Internally, I have another HDD which also is 500GB. Todate, all 3 o/s I use have been able to access this internal 500GB HDD w/o issue.... And naturally I'm happy about that.

Because I use a Seagate HDD I visited their site to see what tools were available to look at my HDD. I found a DOS copy of Seatools. I learned that my HDD has a total of 7298 POH or 304 non-stop days of use if we divide by 24. Is there a number of hours I should be able to get from this disk?

Thanks again all for your support!!!

---

### Post by audiomick on 2010-03-15
> **suomalainen said:**
> Thanks everyone for the great support!!! Really, Thank you!!!

If I understand correctly, and as is in my case, Ubuntu 8.04LTS must be in the ext3 file system. If I understand the process correctly, when I do an install using the Live CD Ubuntu will automatically choose the filesystem it needs to do business in and format in ext3.

correct, unless you manually choose another Linux system like reiserfs or what ever. There is no real reason to do so, though.

> OR..... If the HDD has already been pre-formatted to say NFTS does it leave that in place and begin the install process?
No, as has already been mentioned, it is not possible to install the system on a non-Linux file system.



> I learned that my HDD has a total of 7298 POH or 304 non-stop days of use if we divide by 24. Is there a number of hours I should be able to get from this disk?You might find figures on the seagate web site. I don't know for sure, but that is less than a year. I would expect at least several years to be possible with a seagate.

---

### Post by quadproc on 2010-03-15
> **suomalainen said:**
> 
As a FYI. I have 3 mobile racks in my system. Each contains a 500GB HDD with 1 o/s. XP, 2000, Ubuntu. Each time I want to use an Operating system I power down the PC and turn on the key to the rack with the o/s I want to use and then power up again.


I see what you are doing and I want to suggest that this is a little hard on the hardware.  There are a number of transient loads (both thermal and mechanical) that occur during poweron and poweroff.  These loads shorten the lifetime of the hardware.  Unfortunately, I cannot give any specifics on how much the lifetimes are shortened because they depend on a huge number of factors such as the thermal resistance between the die of a semiconductor and its external environment, and the power dissipation in that die.  Years ago, RCA used to specify thermal cycle lifetimes for their power transistors and as I recall they were about 10K cycles for a typical application so this might give you an idea of the order of magnitude of the problem.  I have not seen such specs in recent times so the data may not be available any more.

> 
Internally, I have another HDD which also is 500GB. Todate, all 3 o/s I use have been able to access this internal 500GB HDD w/o issue.... And naturally I'm happy about that.
...
Because I use a Seagate HDD I visited their site to see what tools were available to look at my HDD. I found a DOS copy of Seatools. I learned that my HDD has a total of 7298 POH or 304 non-stop days of use if we divide by 24. Is there a number of hours I should be able to get from this disk?


  This is really hard to say because a lot of it depends on how the disks have been handled.  I recently read on the web (sorry, I don't recall who said this or where this was posted) that disks shipped by UPS typically failed in less than a year while disks shipped by Fedex typically lasted longer than a year.  I can well believe this because I have personally experienced UPS damage to some things that I have had shipped to me while packages handled by Fedex come through in good condition.

Disk drives are very high precision devices and they are subject to damage which doesn't immediatey incapacitate them but which can shorten their lifetimes.  I have found that paying a little extra for a careful shipper is well worth it.

Of course, it is wise to handle disk drives carefully yourself: wait until they spin down before moving them, do not drop them or shake them, and do not power them on if they are cold because condensation can do significant damage.

You might wish to consider an electronic method of selecting your disks, rather than physically powering them off and on.  I think that some of the external disk drive boxes that hold multiple drives have this option.  But be sure that such a box can do what you need in terms of interface protocol (e.g., eSATA, Firewire, USB); I learned the hard way that Buffalo's HD-HSQ works with Firewire but not with ESATA even though it claims to.

You may wish to check out smartctl, the Ubuntu disk drive tool for checking disk drives in general.  A previous poster mentioned this, and it is quite versatile.

quadproc

---

### Post by suomalainen on 2010-03-15
All,

Thank you very much for the help and attention you gave to me!!! I received very good advice!!!!

My problem has been solved. I used Dariks nuke and boot to clean the HDD. Then I used Seagates SEATOOLs DOS v 2.17 to find any problems. Then I used immeadiately aftrwards Parted Magic v 4.8 to do the same again and get second opinion.

I then installed 9.10 and getting things going as we speak. So far so good.

As a FYI, I build my PC in November of 2007. Regarding the shortening of the hardware I really don't see this? XP and 2000 are used only on an as needed basis and may go weeks w/o use. I guess only time will tell.

Thanks again to all who helped me!!!!

---

