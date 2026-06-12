---
title: "Is there an alternative program to PHOTOREC?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-11-29
In order to recover data from a crashed hdd.
Photorec does some job but bit poorly.

Is there other or better evtl.?

---

### Post by bumanie on 2009-11-29
There are a number of tools available, although if photorec is not doing well, I'm not sure the others will be any better. However if you want to try some others there are magicrescue ; foremost and scalpel (and there may be others) - they are all available in the repositories and if you do a search on the internet, you will find tutorials for all of them. I assume you read the photorec tutorial before starting with it. There are also tools such as dd and ddrescue that you can use to clone the crashed hard drive, allowing you to recover from a stable drive, once the clone is made. The advantage of ddrescue over the 'standard dd' is that it tries to copy data with read errors, these will be skipped with the 'standard dd'.

---

### Post by frenchn00b on 2009-11-29
> **bumanie said:**
> There are a number of tools available, although if photorec is not doing well, I'm not sure the others will be any better. However if you want to try some others there are magicrescue ; foremost and scalpel (and there may be others) - they are all available in the repositories and if you do a search on the internet, you will find tutorials for all of them. I assume you read the photorec tutorial before starting with it. There are also tools such as dd and ddrescue that you can use to clone the crashed hard drive, allowing you to recover from a stable drive, once the clone is made. The advantage of ddrescue over the 'standard dd' is that it tries to copy data with read errors, these will be skipped with the 'standard dd'.

the  problem with dd and ddrescue is that they have a limitation in size. 
I have a terabyte, and those stop at 250gb soemthing. it is their maximum. :(

---

### Post by lkraemer on 2009-11-29
Search the forum for info in the GNU release of gddrescue.  It looks
like it might be another good choice.

Also, different Hard Drive controllers may produce different results.
Same for trying a USB to IDE/SATA interface, or a different drive positions
(Upside Down, On Either Side, On a Cooling Source to keep the temperature
down) etc.  Just don't FREEZE the Drive.

There are also several RESCUE software packages for sale.  Use Google to
search for them.  Your DATA should be worth $70-$100.

lk

---

### Post by Mark Phelps on 2009-11-29
If your drive was formatted NTFS or FAT32, the best data recovery software in my experience is from GetDataBack.  They cost $80 (US) each (separate version for each filesystem), but they have never failed to recovery all my data.

---

### Post by Christophe Grenier on 2009-11-30
> **frenchn00b said:**
> In order to recover data from a crashed hdd.
Photorec does some job but bit poorly.

Is there other or better evtl.?

 What is the problem ? software: ie. corrupted filesystem (ext3, fat, ntfs ?), deleted files, hardware: ie. bad sectors ?  If there are bad sectors, you should use GNU ddrescue first to create a copy of the disk. [http://www.cgsecurity.org/wiki/Damaged_Hard_Disk](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

TestDisk can be used to recover deleted files from

[LIST]
[*]NTFS [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS) and
[/LIST]

[LIST]
[*]FAT [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT)
[/LIST]
  If the filesystem is too damaged to be repaired, PhotoRec is a good option but you may want to use latest version
```
wget [http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2)
tar xjf testdisk-6.12-WIP.linux26.tar.bz2
sudo ./testdisk-6.12-WIP/photorec_static
```

---

### Post by frenchn00b on 2009-11-30
> **Christophe Grenier said:**
> What is the problem ? software: ie. corrupted filesystem (ext3, fat, ntfs ?), deleted files, hardware: ie. bad sectors ?  If there are bad sectors, you should use GNU ddrescue first to create a copy of the disk. [http://www.cgsecurity.org/wiki/Damaged_Hard_Disk](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

TestDisk can be used to recover deleted files from

[LIST]
[*]NTFS [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS) and
[/LIST]

[LIST]
[*]FAT [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT)
[/LIST]
  If the filesystem is too damaged to be repaired, PhotoRec is a good option but you may want to use latest version
```
wget [http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2)
tar xjf testdisk-6.12-WIP.linux26.tar.bz2
sudo ./testdisk-6.12-WIP/photorec_static
```

Salut Christophe! Merci !

---

### Post by pandion on 2010-03-27
Hi,

I just read your post and thought I'd reply. I've done what you are trying to accomplish (somoene else's PC) for a PC with Windows XP (NTFS). The hard drive was failing badly and would no longer boot. The person had tried to boot repeatedly, which only made matters worse. The file system was dirty (needed a CHKDSK) as a result of using it while it was failing, prior to it becoming un-bootable (pay attention to those BSODs and clicking noises). It was clicking badly but would still spin up, and was also not always recognized by the PC's BIOS Setup. Diagnostics from the hard drive manufacturer confirmed over 100 bad LBAs. Basically the drive and filesystem were a mess.. But I was able to recover the complete drive using the tools I'll mention below, with of course the exception of what was no longer readable due to very bad LBAs, which aren't recoverable anyway.

That being said, if it's a hardware problem, remove the hard drive from the PC case. This is necessary in order to keep it very cool while attempting recovery. I connected the drive outside the PC (with the case open and the cable running out to the drive), and placed it on top of an anti-stat pad (circuit board up), which was in turn on top of a freezer gel pack wrapped in a towel. Due the the number of hours required (approximately 18+ hrs in this case), the gel pack had to be swapped with another as it warmed up. The idea is to keep the drive cool, which improves the chances of being able to read the data. For those that have heard of putting a hard drive in a freezer for a few minutes to quick get that data off.. it's the same idea.. and it works.

Next, use the **GNU version of ddrescue** (for the same reasons others mentioned). As for an image size limit, they are incorrect. I have imaged a 1TB drive using GNU ddrescue. A potential problem is not having enough space on a separate hard drive to hold the image, so you need a drive that's as large or larger. Although, there is also a way around this as well (which I used). If you have a current version of GNU ddrescue, there is a command line option to create the image as a sparse file (ext3 supports sparse files and I think NTFS does also). This comes in handy if the bad drive has a lot of empty space, and will reduce the size on disk of the final image file (search Wikipedia Sparse File).  I used a copy of Ubuntu Rescue Remix on bootable CD. It includes the tools/utilities you need, and you can also add others using "sudo apt-get install package-name".

What you do next depends on the status of the bad drive. If the filesystem is dirty (needs a CHKDSK), you shouldn't mount the image in linux (it actually will complain and not mount anyway, and I wouldn't recommend forcing it). The best option is this case is to use another drive as a scratch drive, and restore the image to it instead.

Next, if it's NTFS, connect the scratch drive with the restored disk image to a PC with Windows as a secondary drive (Don't boot from it!). Boot up the working copy of Windows (or boot from a Windows CD). If you can access the drive, browse the drive with Windows Explorer and copy off the data to another drive (flash drive, usb drive, etc.)

Next open a command prompt and force a CHKDSK to run on the drive by using the FSUTIL DIRTY SET drive letter: command. Then shutdown and restart. This will force a more thorough CHKDSK to run at boot before Windows starts. If it's a mess, it will take a long time, and should be run more than once until it's clean. Don't worry about losing data, since this is the scratch drive and you still have the GNU ddrescue disk image. 

After you've cleaned up the filesystem, you might actually be done and not need additional recovery tools. Boot the Windows PC, and browse the scratch hard drive with Windows Explorer. Yes, if the filesystem was a mess there will be recovered FOUND.### folders etc., and some files may be damaged (due to bad LBAs), and some folders may also be in the wrong place, but you will have ALL of the data that was readable off of the drive. If you can't find a file, just do a search by filename, extension, etc. The intent with this was to get the data, not to get a working Operating System. Yes, this seems redundant to browse the drive before and after running CHKDSK, but CHKDSK can sometimes make a mess of things as well, so it's better to get what you can both before and after running it on the drive.

If it's not a Windows PC and is Linux/BSD or something else, similar methods apply. Just access the recovered data on the scratch drive from a working operating system and copy off the data. An fsck/file system check may be necessary as well in order to access it.

As for other tools like Photorec for example, they can also be used on the GNU ddrescue image. The disadvantage of Photorec is that you have to be specific with the type of files you want to recover, and when it does recover them (again, to a different scratch drive), they won't have any recognizable filenames or directory structure.. so you have to pick through them. If you can use the method I described above, you'll get the filenames and the folder structure as well so you'll actually be able to find the files you need. It does however require another hard drive, but if your fixing the PC you need one anyways, and even if you're not you still need a place to put the data.

Hope this helps, and good luck with the recovery.

---

