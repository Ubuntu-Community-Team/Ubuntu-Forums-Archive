---
title: "distribution numbers/names"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by cfr42 on 2011-04-12
I have been trying to figure out whether I could run ubuntu on my laptop and, if so, how. I burnt the relevant 10.10 iso to a DVD (instructions say CD but my utility says every CD I try is too small). I can boot my machine from the liveCD. I'm not sure what to expect. Most things fail in odd ways but I'm not sure how usual this is or if it is expecting me to have a network connection at that point. I don't get error messages. Mostly, nothing happens. Sometimes the application or window just vanishes. Not sure if these are just incomplete on the liveCD.

One thing which clearly doesn't work is the touchpad.

I know that I might need firmware for some things. So I thought I would look to see what was available as "missing firmware". The ubuntu page directs me to the relevant debian page, telling me to "just select the relevant release" and download the tarball. This is easier said than done. How am I meant to know which release of debian corresponds to which release of ubuntu? I've searched the forums and documentation. I've googled. And I'm starting to think that if it is this difficult to find what I would have expected to be a fairly ordinary piece of key information, maybe this really isn't something I should be trying to do. Oh, I also skimmed the technical overview for 10.10 and it seems to tell me a lot about various versions but not the corresponding debian release. Surely this is pretty basic? Why is it so well hidden?

Apologies for sounding so frustrated. As I say, maybe this is just much more difficult than I thought and I should concede the issue quietly.

PPC G4 1.5 GHz 1.25GB nVIDIA GeForce FX Go5200 64MB Aluminium 12" PowerBook trackpad built-in Airport Extreme BlueTooth FW400 USB SuperDrive mini-DVI etc.

---

### Post by earthpigg on 2011-04-12
You barked up the wrong tree with the 'missing firmware' conjecture :)

> ***PPC*** G4 1.5 GHz...

Are you using the PPC iso, or the regular one? If regular, you need to use a LiveCD intended for PPC instead of standard x86.

you kind of have to hunt to find it....

[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)

> Mac (PowerPC) and IBM-PPC (POWER5) desktop CD
    For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines.

note the distinctive file name:

ubuntu-10.10-desktop-**_powerpc_**.iso

note that this is for PPC only, not for ***all*** Mac computers. Only those older pre-Intel ones.

---

### Post by cfr42 on 2011-04-13
I'm pretty sure I got the right .iso image and, yes, it was not at all obvious where to find it. I used [ubuntu-10.10-desktop-powerpc.iso]("http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-powerpc.iso") from the page you linked to above. I could be wrong, but I doubt the image which the regular download page offered me would have booted my machine at all. At any rate, this seemed to be the right choice so that's the one I burnt. My first attempt to download it didn't succeed but the checksums matched those given the second time, so that's the one I burnt to disk.

In OS X, the volume mounts as Ubuntu_PowerPC_maverick and README.diskdefines confirms it is for the ppc architecture. I booted from the LiveCD, choosing the default option at the boot prompt ("live") and got to the desktop. As I say, some things then worked but seemed fairly flaky. The trackpad and buttons on my laptop didn't work at all. Neither did the network but I didn't expect that to work.

Thanks.

---

### Post by migs73 on 2011-04-13
Try checking the checksum of the image on the DVD/CD.

Remember to always burn at the lowest speed possible as well.

Mike :)

---

### Post by cfr42 on 2011-04-13
```

cd /Volumes/Ubuntu_PowerPC_maverick
gmd5sum -c md5sum.txt

```This yielded many errors. I thought this might be because I burnt at too high a speed.

I downloaded another copy of the iso and checked the sha256 hash against that given. I burnt this following the suggested procedure in Disk Utility at speed 2.4 which is the lowest possible. Data verified fine, as before.

Repeat:
```

cd /Volumes/Ubuntu_PowerPC_maverick
gmd5sum -c md5sum.txt

```Again, many errors. In fact, I get exactly the same errors as before. I "tee"ed the output to holding files in both cases and then compared them.

In both cases I got the same 18 files triggering error messages:
```

./pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-1_all.deb: FAILED open or read
./pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-1_all.deb: FAILED open or read
./pool/main/b/build-essential/build-essential_11.5_powerpc.deb: FAILED open or read
./pool/main/d/dpkg/dpkg-dev_1.15.8.4ubuntu3_all.deb: FAILED open or read
./pool/main/d/dpkg/libdpkg-perl_1.15.8.4ubuntu3_all.deb: FAILED open or read
./pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.4-14ubuntu5_powerpc.deb: FAILED open or read
./pool/main/g/gcc-4.4/g++-4.4_4.4.4-14ubuntu5_powerpc.deb: FAILED open or read
./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu7_powerpc.deb: FAILED open or read
./pool/main/w/wvstreams/libuniconf4.6_4.6.1-1ubuntu1_powerpc.deb: FAILED open or read
./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1ubuntu1_powerpc.deb: FAILED open or read
./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-1ubuntu1_powerpc.deb: FAILED open or read
./pool/main/libs/libspe2/libspe2-2_2.2.80-95-3.1ubuntu4_powerpc.deb: FAILED open or read
./pool/main/libs/libspe2/elfspe2_2.2.80-95-3.1ubuntu4_powerpc.deb: FAILED open or read
./pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_powerpc.deb: FAILED open or read
./pool/main/p/ps3pf-utils/ps3pf-utils_2.0-2build1_powerpc.deb: FAILED open or read
./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_powerpc.deb: FAILED open or read
./pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb: FAILED open or read
./pool/main/s/setserial/setserial_2.17-45.2ubuntu2_powerpc.deb: FAILED open or read

```In at least some cases, this seems to be because what is burnt on the disk is a differently named file. For example:
```

ls ./pool/main/liba/libalgorithm-merge-perl/
libalgorithm-merge-perl_0.08-1_

```

---

### Post by earthpigg on 2011-04-13
odd.

at this point, in your shoes, i would try downloading via .torrent and different cd burning software and, if handy, a CD-R from a different batch.

---

### Post by cfr42 on 2011-04-14
OK. So I found a BitTorrent client for OS X and installed it. I got the .torrent file corresponding to the image I need (ubuntu-10.10-desktop-powerpc.iso.torrent) and I downloaded the torrent using transmission. I then verified the sha256 checksum.

Rather than using Disk Utility, I this time used Burn (an open source CD/DVD burning application for OS X). Used slowest speed (x2), verified the burn etc. All looking fine. I then mounted the disk in OS X and repeated the check I ran above.

I get exactly the same errors for the same 18 files. Again, when I look at the files on disk, the names do not match.

The only thing I didn't do was use a different brand of media because I don't have any handy. I have CD-Rs around but I can't burn a 710MB image on a 700MB CD. In the past, I had some problems burning DVDs but on my third attempt, I found a brand that worked reliably and have not had any problems since. The DVDs I've been turning into coasters are the same brand and from the same batch. So it would be surprising if it was the particular batch or brand that was causing a problem. (Unless Ubuntu just took a personal dislike to it?!) Moreover, the fact that I'm getting exactly the same errors every time doesn't look to me like a flaky burn problem. Not that I know much about these things.

I'm not sure how an .iso image should behave in OS X but for whatever it is worth, OS X says that there is a problem with it:
```

hdiutil attach ubuntu-10.10-desktop-powerpc.iso
The disk image you are opening may be damaged and could damage your system.
Are you sure you want to open this disk image? (Y/N) n
hdiutil: attach failed - no mountable file systems

```As I say, I've no idea whether this is what you'd expect OS X to say about an .iso since it isn't a format I'm familiar with. (OS X disk images are .dmg files.) I mention it only in case somebody does know whether this is normal or not.

---

### Post by earthpigg on 2011-04-14
wait, the official ppc ubuntu .iso is 710mb?

if so, that may warrant more googling and perhaps a bug report...

---

### Post by cfr42 on 2011-04-14
Yes. Strictly, 709.something, I think. From [http://cdimage.ubuntu.com/ports/releases/10.10/release/:](http://cdimage.ubuntu.com/ports/releases/10.10/release/:)
[ubuntu-10.10-desktop-powerpc.iso]("http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-powerpc.iso")               08-Oct-2010 02:37  710M  Desktop CD for Mac (PowerPC) and IBM-PPC (POWER5) computers (standard download)

---

### Post by KL_72_TR on 2011-04-14
p { margin-bottom: 0.08in; }  Keep these in mind when running in Live Distro Mode.
 _Settings_: When you shut down the PC every setting will be lost or each time you boot is like the first time and you have to make these settings from the beginning.
 _System_: Ubuntu is unaware (for some strange reason) of running in Live Distro Mode. In the beginning has the need to update but can't update a CD or DVD so that can confuse the system a bit which is running from the CD.
 > **cfr42 said:**
> One thing which clearly doesn't work is the touchpad.
  	 	 	 	p { margin-bottom: 0.08in; }  For this would suggest the Ubuntu Netbook.[http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)

---

### Post by cfr42 on 2011-04-14
Did you read the remainder of this thread? I cannot see the relevance of your remarks to my situation as currently understood. If I am misunderstanding you, perhaps you could provide a more detailed explanation.

For what it is worth:

Yes, I appreciate that any settings made will be lost when I shut down. I only want to run from the CD to establish whether things are likely to work when I install properly on a free partition of my HD.

The netbook option is not appropriate for my machine. So far as I can tell, there is no ppc netbook version. This is true for both 10.04 and 10.10. (In any case, the systems the netbook install is designed for do not sound as though they are designed for a full laptop. But even if they would be brilliant for this, they will not work for this architecture.)

In any case, right now it is impossible to tell what would or would not work from a properly burnt LiveCD because it is looking as though it is impossible for me to obtain one. So my worries about the touchpad not working have been superseded by the difficulty I am having in obtaining a suitable CD at all. Whether the touchpad or anything else would or would not be supported by such a CD is therefore a moot point.

---

### Post by cfr42 on 2011-04-14
I've now created a 10.04 DVD coaster to accompany my collection of 10.10 DVD coasters. They are all truncating long file names. (Don't know if it is the file name per se or if it is the length of the file name plus the directory path but it is, in any case, truncating everything.)

I wondered if this is a known issue but haven't yet found much. There are some old reports of problems using Disk Utility to burn ubuntu isos in OS X 10.3 specifically. Unfortunately, the suggested solutions either require software which is no longer available or software which costs lots of money.

Anyway, I plan to see if I can persuade disk utility to burn 10.04 to a CD-R tomorrow. Last time I tried this, it said the disk was too small but I'm using a different burner, a different OS and a different CD so hopefully that'll work. (Would try it now even if it is 3am but the disks are in a room with somebody asleep in it!)

---

### Post by cfr42 on 2011-04-14
OK, so I got a CD-R after all. Burnt in Disk Utility at lowest possible speed. Burn failed. Disk Utility complains that the device failed to respond properly.

Log messages while burning:
```

diskimages-helper[10788]: /sbin/fsck_hfs(/dev/disk2s2) failure for 
/Users/<user>/Documents/src/ubuntu-10.10/ubuntu-10.10-desktop-powerpc.iso.

Disk Utility started.

Burning Image “ubuntu-10.04-desktop-powerpc.iso”
    Preparing data for burn
    Opening session
    Opening track
    Writing track
    Closing session
    Finishing burn
    Burn failed
    The device failed to respond properly, unable to recover or retry.
Unable to burn “ubuntu-10.04-desktop-powerpc.iso” - The device failed to respond properly, unable to recover or retry..

```
After it finished, I pushed the CD back in to see if I could get any information about it. From the log (repeats eliminated!):
```

kernel[0]: disk1: alignment error.
retrospectcd.util: [11958]: ...ret = -2\n
retrospectcd.util: [11958]: File system unrecognized; a mount is not possible.\n
SAM Multimedia: READ or WRITE failed, ASC = 0x02, ASCQ = 0x00
kernel[0]: disk1s1s2: I/O error.
diskarbitrationd[85]: unable to mount /dev/disk1s1s2 (status code 0x00000001).

```It is possible that my burner is going to be as picky about CDs as it is about DVDs. In which case, it could take me a long time to find one which will work. Or it could be something altogether different. I'm highly suspicious of the "retrospectcd.util" process, for example...

Should the file system burnt to disk be HFS? Because Disk Utility seems to be using fsck_hfs to verify the filesystem.

---

### Post by Dutch70 on 2011-04-14
I think there is currently something wrong with that download. The whole idea is to make it fit on a cd. 710MB obviously does not accomplish that. 

If you try the 64-bit download, it's 690MB. The alternate cd is 692. There is definitely something wrong with the download itself imho. 
Being too large for a cd kind of defeats the purpose of a file named...Mac (PowerPC) and IBM-PPC (POWER5) [COLOR="Red"]desktop CD[/COLOR]

As Earthpigg said...That may be a bug.

---

### Post by earthpigg on 2011-04-14
anyone want to file the bug report or see if one is already filed? on the netbook atm, small keyboard + bug report = pain in the butt.

---

### Post by Dutch70 on 2011-04-14
Well, it's been reported for 11.04. This isn't the actual bug report, but they're obviously aware of this one.
[[COLOR="Red"]http://hr.archive.ubuntu.com/ubuntu-cdimage/daily-live/[/COLOR]]("http://hr.archive.ubuntu.com/ubuntu-cdimage/daily-live/")

---

### Post by cfr42 on 2011-04-15
Thanks. I'm glad it isn't (just) me.

So I got hold of a different brand of CD and successfully burnt the 10.04 image to CD. At least, Disk Utility verified it.

But the checksums still don't check out. Once again, I've got truncated file names. The only difference appears to be that it affects 16 of 63 files (10.04) rather than 18 of 64 (10.10). So whatever problem there is with the 10.10 download, I'm encountering a further issue.

Any thoughts what I might try next other than giving up altogether?

---

### Post by migs73 on 2011-04-15
Can the ppc version run of a live USB? I haven't looked into it but don't see why not. That would rule out any CD/DVD media problems.

EDIT; can the mac boot from USB???

---

### Post by cfr42 on 2011-04-15
Sadly, no. You can't boot a PPC Mac from USB. (Intel Macs can.)

---

### Post by cfr42 on 2011-04-15
I'm also posting a query in the Apple forum ([http://ubuntuforums.org/showthread.php?p=10680858#post10680858](http://ubuntuforums.org/showthread.php?p=10680858#post10680858)) because I suspect this is either hardware or software related and, either way, that'd be Apple specific.

But I'd obviously appreciate any suggestions here as well!

---

### Post by cfr42 on 2011-04-15
Thought I'd try burning from the command line using hdiutil but got the  same truncated names (although hdiutil verifies the burn just as Disk  Utility did).
 
 Question, when I examine the burnt disk in Disk Utility, what should it look like?
 
 What I'm getting is:
 796.7 MATSHITADVD-R   UJ-835E
   > Session 1
       > Ubuntu_PowerPC_lucid
 
 for the top level, partition scheme is CD_partition_scheme; disk number  is 1; partition number is 0; device tree is mac-io/ata-3@20000/@0:0
 
 for the second level, partition scheme is Apple_partition_scheme; disk number is 1; partition number is 1
 
 for the third level, partition type is Apple_HFS; device tree is  IODeviceTree:mac-io/ata-3@20000; disk number is 1; partition number is  2; Disk Utility thinks it is not bootable
 
 I was surprised that there was a "Session 1" level but never having done  this before, perhaps that is normal when burning this type of image? OS  X mounts it as just /Volumes/Ubuntu_PowerPC_lucid.
 
 If there's any more information which might be helpful, please let me  know. I've googled quite a lot but haven't come up with anything at all  helpful so far.

---

### Post by cfr42 on 2011-04-16
Thinking the problem might be with hdiutil/Disk Utility, I downloaded and compiled cdrtools 3.00. (I used gmake rather than smake but the compilation and installation seemed to work fine and googling suggests it is usually compiled with gmake for OS X.)

I'm having the same problem burning with cdrecord as with Disk Utility and hdiutil, however. The burn seems to go fine. I don't get any fatal errors. But the file names are once again all truncated.

This is the command I used to burn with:
```

cdrecord -dao -v speed=8 dev=1,0,0 ubuntu-10.04-desktop-powerpc.iso 2>&1 | tee cdrecord.out

```
I would be happy to post the contents of cdrecord.out if anybody knowledgeable would be prepared to look at it but hesitate to do so otherwise since it is quite long and I'm not sure what might be relevant.

Am I just being very, very dumb? Or is creating a LiveCD for Ubuntu really only something experts should attempt, at least on my platform? The instructions make it sound so simple but "It just doesn't work!" - and that's part of what's so frustrating about it. If the instructions made it sound like a formidable challenge, I wouldn't be so disappointed when I found myself unequal to the task...

This is probably just my ignorance but is this related in any way to [https://bugs.launchpad.net/unetbootin/+bug/373086](https://bugs.launchpad.net/unetbootin/+bug/373086)? I know that that bug concerns a different version of Ubuntu, a different installation media and a different architecture but it is the first hint I've found concerning the apparent truncation of file names.

---

### Post by cfr42 on 2011-04-16
Maybe "truncate" isn't quite right...
Using isoinfo, here's one of the files listed under ./pool/main/libs/libspe2:
```

LIBSPE2_2_2_2_80_95_3_1UBUN.DEB

```Here's the corresponding file and md5 sum as burned to disk:
```

aff6af4dfdc336157ec84bc592130cf6  pool/main/libs/libspe2/libspe2-2_2.2.80-95-3.1ubuntu4_

```Here's the corresponding line from the list of md5 sums:
```

aff6af4dfdc336157ec84bc592130cf6  ./pool/main/libs/libspe2
/libspe2-2_2.2.80-95-3.1ubuntu4_powerpc.deb

```So the md5 sums match. The file is burnt correctly in some sense  but the name is truncated relative to the intended name. And I'm not  sure what its relation is to the name given by isoinfo.

---

### Post by cfr42 on 2011-04-16
So I figured out that the intended name is given in the "Rock Ridge extensions" in the .iso image and the full list of intended names can be viewed by adding the -R flag to isoinfo.

Any hints as to how I might get these burnt to CD using cdrecord (or Disk Utility or hdutil or...)? Or, rather, how I can prevent them from being truncated?

---

### Post by robsoles on 2011-04-16
Is there anything like furious iso mounter for OS X?

If you could mount the image then you can make sure the filenames aren't truncated in the iso to start with, it is unlikely that burning software is manipulating the iso image before writing it - particularly without alerting you that it is doing so.

You could copy the files from the CD to a directory in your home folder, rename the truncated files there and then use advanced options in a good burning program to grab the boot sector from the original iso and burn the corrected files from the directory - I imagine the program will challenge you to allow it to truncate some filenames to make it valid for the joliet (or is it UDF, I can't think of it for sure right now!) file-system[COLOR=Red]: SELECT NO, it will whinge (perhaps) but ignore it.[/COLOR]

Are the filenames truncated in the original .iso file?

---

### Post by cfr42 on 2011-04-17
> **robsoles said:**
> Is there anything like furious iso mounter for OS X?

I don't think so. I did a quick google but couldn't find anything at all likely looking. .iso images are essentially a foreign format on OS X. Do you know if there's an equivalent on FreeBSD, for example? That might be more likely to have been ported to OS X. (Not necessarily true but possible.) The information I found for furius (furious?) iso mount suggested it is specific to linux but I'm assuming FreeBSD would use .iso images, too?

> 
If you could mount the image then you can make sure the filenames aren't truncated in the iso to start with, it is unlikely that burning software is manipulating the iso image before writing it - particularly without alerting you that it is doing so.

Hmm. My understanding was that it was essential to burn it without mounting it because mounting it could itself damage the image. OS X, on the other hand, complains that mounting it may damage my system. Burn (a free burning programme from, I think, sourceforge) let me mount a copy without any complaint.

> 
You could copy the files from the CD to a directory in your home folder, rename the truncated files there and then use advanced options in a good burning program to grab the boot sector from the original iso and burn the corrected files from the directory...

I'll look into this. Right now I have no idea how to do it and I suspect it is going to be difficult to figure out how to do it on OS X but it is certainly worth a shot if it might work.

> I imagine the program will challenge you to allow it to truncate some filenames to make it valid for the joliet (or is it UDF, I can't think of it for sure right now!)...

It seems not to be joliet (according to isoinfo) but rather iso9960 with rock ridge extensions. When burnt, it appears to be HFS but might it be hfs/iso hybrid? The burnt CD seems to be using Apple's partition scheme etc. but this may be expected since I have a feeling that's necessary to boot a ppc mac. (There's a different partition scheme for Intel macs and it matters which you choose when partitioning a disk intended to boot, as well as mattering which file system you pick for bootable volumes.)

> 
Are the filenames truncated in the original .iso file?
isoinfo -l lists truncated names though they are not the names which get burnt. isoinfo -l -R lists the correct names and it is truncated versions of these which get burnt and which show up when the image is mounted with Burn.

---

### Post by cfr42 on 2011-04-17
One of the (many :)) things which is confusing me is that the image appears to be ISO9660 with Rock Ridge extensions but the CDs which get burnt appear to be HFS. Here's the Lucid CD I burnt with cdrecord listed by diskutil:
```

/dev/disk1
   #:                   type name               size      identifier
   0:    CD_partition_scheme                    *797.0 MB disk1
   1: Apple_partition_scheme                    694.0 MB  disk1s1
   2:    Apple_partition_map                    1024.0 B  disk1s1s1
   3:              Apple_HFS Ubuntu_PowerPC_lucid 693.7 MB  disk1s1s2

```I'm not sure whether this is what's expected or not.

If I mount the corresponding image with Burn, diskutil gives me:
```

/dev/disk4
   #:                   type name               size      identifier
   0: Apple_partition_scheme                    *694.0 MB disk4
   1:    Apple_partition_map                    1024.0 B  disk4s1
   2:              Apple_HFS Ubuntu_PowerPC_lucid 699.5 MB  disk4s2

```
It seems odd the Ubuntu_PowerPC_lucid is listed as larger than the total capacity and that it is of a different size from the version burnt to disk. (Since both truncate the names in the same way, presumably this isn't the issue?)

Thanks to everyone who is trying to help with this (or even who has just bothered to read this far!).

---

### Post by cfr42 on 2011-04-17
The good news is that many of my coasters have turned out to be genuine LiveCDs after all. At least,
```

md5sum -c md5sum.txt

```
from the root level of the burnt CDs/DVDs  verifies the md5 sums of the 63/64 files on the disks.

The catch is that *this only works while booted from the CD/DVD in question* or, more accurately, it does not work if you mount the LiveCD in OS X. I'm not sure if this is because there is something odd about the HFS stuff on the LiveCDs or if it is for some other reason. It seems extremely strange. In Ubuntu, the filenames are not truncated so the md5sums check out. In OS X, they are truncated, so they don't. At least, it strikes *me* as extremely odd but I don't know much about file systems, hybrid (?) disks etc.

So I think I am now back with my original question which is whether it is possible for me to check the debian archive for relevant firmware prior to installation. To do this, I need to know which release of debian corresponds to which release of Ubuntu.

Ubuntu 10.10 seemed somewhat less flaky than the first time I tried it but still really quite flaky. Starting from the LiveCD, the first thing that happens is that I get a message about an application crash and if I say, fine, send a report, I get a complaint that it is the wrong sort of crash for the reporting application to report on. Maverick seems unable to detect my wireless card and I think it is bluetooth that is crashing. My trackpad does nothing whatsoever.

Ubuntu 10.04 seems significantly less flaky. I discovered that my trackpad occasionally works but it is essentially unusable. I can't use desktop effects. I'm not sure whether this is because my graphics card really isn't good enough or whether it is because it can't find a reasonable driver to support it. (nVIDIA GeForce FX Go5200 32-bit color AGP bus 64MB VRAM) I don't care about desktop effects per se but unless Ubuntu uses some really stunning effects, I'd have expected to at least be able to manage the "normal" level. But it at least detects my wireless and it is even possible to activate a driver for it. It also finds bluetooth and it does not crash on startup.

So, anyway, I'd like to know if it is possible that there might be firmware, drivers or other support that would help with some of these issues if I were to install Ubuntu properly. The trackpad issue is a stopper for me. I typically don't carry a mouse and, even at home, I rely on the trackpad very heavily.

Another reason I'd like to know which release of debian corresponds to which release of ubuntu is that a second machine, which I'm also thinking about installing ubuntu on, gets nowhere at all. I tried booting it from the apparently less flaky 10.04 and got a bunch of errors in red about missing firmware which I did not have time to write down. I suspect it is missing firmware necessary for graphics or something to do with that because after that the screen goes essentially blank (at one point there was Ubuntu's equivalent of the OS X spinning beach ball - I don't know what it is called) and I eventually had to pull the plug on it. 

Thanks for reading.

---

