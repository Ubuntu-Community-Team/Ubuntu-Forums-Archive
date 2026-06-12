---
title: "External hard drive formatting question"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by 11010110 on 2009-01-05
Hi everyone, 

my new 1TB western digital external hard drive just came today and i had a few questions regarding it. First off do i have to format it? I want it to work just like a usb thumb drive. it has some software for mac and windows on there already (i assume that its the backup software that came with it) and i was wondering if i needed that stuff to use it on a wondows system (i have a wubi dual boot and i would like it to work for both). How would i format it to work with both linux and wondows then? 

Thanks a lot in advance everyone!

---

### Post by jbrown96 on 2009-01-05
You will probably need to format it. Since its so big (1TB), you should use NTFS if you want to also be able to use it in Windows. Fat32 has volume limitations (can't remember exactly, but way less than 1TB). You don't "need" any of the software that it came with to use it, but you may find it useful. There's no requirement for it to use it in Windows. I would recommend formatting it in Ubuntu since you will probably need to get some new software anyways, and I think the Ubuntu method is more straight forward. 
1) get the software ```
sudo apt-get install ntfs-3g gparted
```

2) format the disk. This will delete the software that is on the disk. 
Open the Partition Editor (System-->Admin-->Partition Editor). On the top right, select your device from the drop-down menu. Select any existing partitions and delete them. Then click apply. Now create a new NTFS partition and apply.

---

### Post by Paqman on 2009-01-05
One thing to watch out for on an external NTFS drive is unclean shutdowns. Make sure you always unmount the drive cleanly before shutting the machine down.

If an NTFS volume doesn't shut down cleanly, Ubuntu won't mount it when you boot next. The solution is a simple boot and clean shutdown of Windows, but it's a hassle you can avoid by simply unmounting properly.

---

### Post by 11010110 on 2009-01-05
alright that sounds good. ill reformat into ntfs but if it is limited by fat32 then how is it that it is already using the "vfat (fat32)" system?


Thanks everyone

---

### Post by jbrown96 on 2009-01-05
I'm glad I looked into this. It appears as though my original post was incorrect. You will be fine using fat32; Windows just can't create it during setup (i.e. you can't install Windows to it with fat32). 
Here's the relevant section from Wikipedia > On Windows 95/98, due to the version of Microsoft's SCANDISK utility included with these operating systems being a 16-bit application, the FAT structure is not allowed to grow beyond around 4.2 million (< 222) clusters, placing the volume limit at 127.53 gibibytes.[14] A limitation in original versions of Windows 98/98SE's Fdisk utility causes it to incorrectly report disk sizes over 64GiB.[15] A corrected version is available from Microsoft, but it cannot partition drives larger than 512GiB [16]. These limitations do not apply to Windows 2000/XP except during Setup, in which there is a 32GiB limit.[17] 

And as Paqman said, NTFS is a pain to use because it will get "unclean" if you don't unmount, and then you have to mount it in Windows or force-mount it in Ubuntu

---

### Post by SunnyRabbiera on 2009-01-05
Normally it should be fine with any filesystem,Ubuntu can handle pretty much any FS out there.

---

### Post by 11010110 on 2009-01-05
ok... so i think i get it... it would be just fine to leave it in vfat (fat32) as it came? also about the software on it... how would i get rid of it without reformatting (to save myself some time and  trouble) since there is no os i assume that it is not "installed" per se so would a simple highlight delete suffice (its over 300mb of data) or could there be some hidden away safe from that measure?. 

thanks all!

---

### Post by jbrown96 on 2009-01-05
There may be some hidden files. You can show hidden files in the file browser. Note that Windows always creates .trash folders on the drive, so you will constantly see those if you show hidden files. It also create .thumbsdb files where there are media files, especially pictures (these are the preview icons) and can be deleted but will be recreated. 

No need to change the filesystem.

---

### Post by 11010110 on 2009-01-06
also, it was mentioned earlier that caution must be taken when shuting down the computer using an ntfs formatted drive. is this the same with fat32? or would just shutting down without unmounting suffice?

thanks again everyone

---

### Post by Carl Hamlin on 2009-01-06
> **jbrown96 said:**
> And as Paqman said, NTFS is a pain to use because it will get "unclean" if you don't unmount, and then you have to mount it in Windows or force-mount it in Ubuntu

I may be having this problem. Can you elaborate a little on 'force-mount', please? My SimpleTech drive is having trouble being properly detected after working fine when I first got it.

---

### Post by jbrown96 on 2009-01-06
11010110: Fat32 doesn't support fancy features like knowing whether it's "clean", so no you don't need to worry about it being removed unsafely as far as being able to mount it again. However, it's always a good idea, because Ubuntu may have not finished writing to the device or may have delayed a write for some reason.

> **Carl Hamlin said:**
> I may be having this problem. Can you elaborate a little on 'force-mount', please? My SimpleTech drive is having trouble being properly detected after working fine when I first got it.

You will need to mount it from the command line. 1) find the device with ```
sudo fdisk -l
``` you are looking for the /dev/sda1, where the a and 1 might be different. you need this for step three. 2) create a mount point. This can be anywhere, but for this example I will use /media/external ```
sudo mkdir /media/external
``` 3) mount the drive ```
sudo mount -t auto /dev/sda2 /media/external -0 force
``` change /dev/sda2 to what you found in step 1.

---

### Post by Carl Hamlin on 2009-01-06
> **jbrown96 said:**
> You will need to mount it from the command line. 1) find the device with ```
sudo fdisk -l
``` you are looking for the /dev/sda1, where the a and 1 might be different. you need this for step three.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Well, drat. The drive doesn't generate a device file.

I got it for Christmas, mounted it on my laptop, and formatted it ext3. Everything went smoothly at that time.

Then, I packaged it back up and brought it home to setup on my home file server, at which time it began exhibiting the faulty behaviour. When I connect the drive via USB, it does *nothing* except generate the following lines in my message log:

```

Jan  1 13:55:57 &#12415;&#12407; kernel: [ 1150.872161] usb 5-1: new low speed USB device using uhci_hcd and address 22
Jan  1 13:55:57 &#12415;&#12407; kernel: [ 1151.548159] usb 5-1: new low speed USB device using uhci_hcd and address 23
Jan  1 13:55:58 &#12415;&#12407; kernel: [ 1152.116196] usb 5-1: new low speed USB device using uhci_hcd and address 24
Jan  1 13:55:58 &#12415;&#12407; kernel: [ 1152.640167] usb 5-1: new low speed USB device using uhci_hcd and address 25

```

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklkKnkACgkQyLm4ydrABvcxkgCdFbbxNAOS5E9cFRMUG8K65viK
vAYAnitQ3Y1s0nIJvjuL3n0OTItu84BV
=Cm5G
-----END PGP SIGNATURE-----

---

