---
title: "Seeking File Server Advice"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by macguy918 on 2007-01-24
Hello.

I am a relatively new Ubuntu user, and I have ubuntu working on an old P-III 1 Ghz PC.  I would like to use that machine as a file server for a home network that consist of multiple macs and a PC.

I have samba set up and working and I can access the shares on the ubuntu box from both the PC and the Macs. 

I plan to expand the disk space in the ubuntu box by adding a second internal hard drive, and I have multiple external hard drives (both USB 2.0 and Firewire) that I can hook up to the ubuntu pc via USB 2.0 and/or Firewire.

Now that i have the basic networking in place, I am getting ready to go live with this setup.  My main question is what kind of disk format should I use on the various drives on the ubuntu pc? Right now, one of the drives is formatted partially in FAT32 and partially as a MACOS Extended Drive.  The other external drive is formatted exclusively as a MACOS Extended Drive.

I want to use the drives on the ubuntu box as the primary location for some 22 GB of iTunes music and video files, and then the rest of the space on the various drives would be used for various backups from both the Macs and the PC.

I would appreciate any advice, suggestions, pros, cons, etc. of different disk formats on those networked drives, both the second internal drive and the external drives.  I can reformat them all now if need be and would rather do this as I start this process.  I wouldn't want to get very far down the road and find out I should have chosen different disk formats.

Thanks

---

### Post by dannyboy79 on 2007-01-24
have you gogled this yet, I found tons of info. just spending about 5 mins, I found people that have said:
FWIW, I spent hours on this about a month ago, trying to share a Firewire drive between a journaled ext3 SuSE box and a 10.4 Server box. I gave up and went the network route.
posted by waldo at 8:14 PM PST on August 24 

and others that have said:
I mount an ext3 linux volume via OS X's NFS support. It works fine. But that won't work for you, but I bring it up because of the following. When OS X uses this drive it backs up all the metadata that HFS+ has that NFS doesn't support as ._[file_name] files (I think it does resource forks, too). This, while better than losing the information, is a pain, as these files seem to be always marked dirty, and thus waste time in backups. I also think it was only in Tiger that the command line file utilities such as cp, mv, and rsync became aware of this metadata, so it is discarded in pre-Tiger OSs if a file is copied via command line to a non-HFS+ filesystem.

I think the same thing happens if copy HFS+ files to FAT16 or FAT32. So that is something to keep in mind with non-HFS+ filesystems.

I didn't realize that there was no EXT2 support in Tiger. Maybe I should donate some time getting the driver ported.

I'd probably be tempted to try the HFS+ Linux driver.
posted by teece at 3:31 PM PST on August 24 



Is there a way to -not- copy the resource fork data when using rsync? I don't want it on the backup, if that's possible.
posted by odinsdream at 3:38 PM PST on August 24 



In the version that comes with OS X, just leave off -E to discard metadata and resource forks. The GNU version of rsync (say from Fink) would discard it by default, as it has no idea what it is.

I am not a long-time Mac user, so I am not entirely clear on what all things use resource forks and metadata, but I think at the very least a font file is trashed if you don't copy the resource fork. And certain icon packages I have seen are really just empty files, with the actual icon as a resource fork. So make sure you'd not be throwing away stuff you need (also, Spotlight can be based heavily on filesystem metadata, so if you use keywords and labels and such, that would all be thrown away in your backup).
posted by teece at 3:47 PM PST on August 24 

If your files are under 4GB than I would sugest using FAT32. I am in a similar boat as you. I just bought a 500GB eSATA drive and wasn't sure to go the ntfs route and install ntfs-3g in linux or go the ext3 route and install the fs-driver in winxp? i figured since the drive was going to used within the linux box more (my movie, music, and backup server) that I owuld go the ext3 Filesystem route and if I needed to get a file from winxp, I would either use samba first and if I need to actually connnect it to winxp, I would install the 3rd party driver called fs-driver, which allows read access to ext3 partitions. you lose permissions though! good luck.

---

