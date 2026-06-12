---
title: "Iomega USB 250 GB Desktop Hard Drive"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by a.v.l on 2010-08-28
I have an Iomega USB 250 GB hard drive which I'd like to format and partition so that I can install XP and Ubuntu 10.04 on. The serial number of the drive is J4AG260309 and the Part number is 31641200. Photo of the drive is attached.

My problem is that it will not allow me to format/partition it at all in gparted in Ubuntu or an XP computer. The documents I've read on the Iomega website suggests its presently formatted as FAT 32. 

Is it likely this will not format in any other format? The drive shows up on an Ubuntu and an XP computer but is very unpredictable when it does and accessing the disc content is a hit and miss affair and the reason for me wanting to start afresh with a clean formatted drive, can someone help please.

---

### Post by sharathcshekhar on 2010-08-28
Are you sure it was unmounted when you tried to partition it in Gparted? What was the error message you got when you tried to partition it in Gparted?
Did you try fdisk/cfdisk to format it?

---

### Post by coffeecat on 2010-08-28
Agreed about the need to unmount it before you can format with Gparted. A USB drive will be automounted in Ubuntu as soon as you plug it in. You can unmount it from within Gparted and then you should be able to reformat it.

However, you say you can't format it in Windows and that its behaviour is unpredictable. That sounds as though there may be a hardware problem. In Ubuntu, open System > Administration > Disk Utility. See if you can do a SMART test on it.

With Windows, is that the basic inbuilt formatting tool you are trying, or 3rd party software? Because with either you *should* be able to format an external USB drive without problems. I think you need to exclude the possibility of a failing drive.

---

### Post by a.v.l on 2010-08-28
> **coffeecat said:**
> Agreed about the need to unmount it before you can format with Gparted. A USB drive will be automounted in Ubuntu as soon as you plug it in. You can unmount it from within Gparted and then you should be able to reformat it.

However, you say you can't format it in Windows and that its behaviour is unpredictable. That sounds as though there may be a hardware problem. In Ubuntu, open System > Administration > Disk Utility. See if you can do a SMART test on it.

With Windows, is that the basic inbuilt formatting tool you are trying, or 3rd party software? Because with either you *should* be able to format an external USB drive without problems. I think you need to exclude the possibility of a failing drive.

Thanks for the replies. I'm beginning to question if this drive has a fault as its becoming more unpredictable by the day. Sometimes it won't show up in gparted and other times it does. Anyway for what its worth, these photos show some of the errors I'm getting when trying to unmount or format the drive in ubuntu/gparted. Smart test is not supported in disk utility and I've tried using the built in formatting tool in XP without any luck too.

---

### Post by a.v.l on 2010-08-28
Images I left out from my last message.

---

### Post by coffeecat on 2010-08-29
I see your drive appears variously as fat32, ntfs and ext3, so I assume you did manage to reformat it in Gparted but that it still behaves unpredictably. The only other thing I can suggest is to recreate the partition table, but it's a long shot.

In Gparted - so long as it's seeing the drive - go to Device > Create Partition Table. Click on Advanced to ensure that msdos type table is selected and OK that. That will have the effect of removing all partitions. Now create a new partition, formatted with whichever filesystem you require, and see if that makes any difference.

---

### Post by a.v.l on 2010-08-29
> **coffeecat said:**
> I see your drive appears variously as fat32, ntfs and ext3, so I assume you did manage to reformat it in Gparted but that it still behaves unpredictably. The only other thing I can suggest is to recreate the partition table, but it's a long shot.

In Gparted - so long as it's seeing the drive - go to Device > Create Partition Table. Click on Advanced to ensure that msdos type table is selected and OK that. That will have the effect of removing all partitions. Now create a new partition, formatted with whichever filesystem you require, and see if that makes any difference.

Thanks, we seem to be getting somewhere now. I created a partition table as suggested and then selected NEW then formatted as NTFS but had a error message and could not do it. Then I tried formatting as an ext 3 and it worked as the photo shows. 

Now when I open the Iomega drive in gparted it appears there every time - great stuff. When I open the Iomega USB drive by clicking on it, there is a lost and found file in there, which I don't understand the reason for and at the moment I'm having a problem saving a TEST File to this drive, as the error message show. 

I've had this error with an unrelated problem before and cannot remember how I fixed it, but I did. Any advice how to do this would be appreciated. Your help is much appreciated.

---

### Post by sharathcshekhar on 2010-08-29
> 
When I open the Iomega USB drive by clicking on it, there is a lost and found file in there, which I don't understand the reason for

A lost+found directory will be created by default on ext partition. During System recovery if Linux finds any unsaved files will put those files in this directory from where you have to manually take it. So this is normal.
> 
at the moment I'm having a problem saving a TEST File to this drive, as the error message show.

This looks like permission problem. Either the folder onto which you have mounted, or the mounted drive itself. You can give write permissions to the folder on to which it is mounted and check. If this does not work, unmount the drive and mount it manually with
```

$ sudo mount /dev/sdb1 /mount/path/

```
By default Linux gives r/w permissions. If you want to specify explicitly, try giving "-o rw" as flag.

---

### Post by coffeecat on 2010-08-29
> **a.v.l said:**
> then formatted as NTFS but had a error message

What was the error message, and have you the package ntfsprogs installed? It's a pity that you haven't been able to format it NTFS because you won't get the permissions problems you are having with ext3.

> **a.v.l said:**
> there is a lost and found file in there, which I don't understand the reason for and at the moment I'm having a problem saving a TEST File to this drive, as the error message show. 

As sharathcshekhar said, the lost+found folder is normal in an ext partition.

The error message is because the ext3 partition is mounted by root. Unfortunately, whether you let it automount or mount it manually as sharathcshekhar describes, it will still be owned by root and you will get an error unless you use a root nautilus. But you don't want to do that. There is a better way.

Plug the drive in and let it be automounted. Let the Nautilus (file browser) window open showing the contents of the ext3 partition. Now press ctrl-L and the breadcrumb location trail will change to the location shown as a path: something like /media/whatever. Make a note of the whatever. It'll either be the partition label (which I don't think you've applied) or the UUID which is a long string of alphanumeric characters.  Let's assume the string is 'd310e646-fe54-4e92-913c'. (It'll be much longer.) Now open a terminal and:

```
sudo chown yourusername: /media/d310e646-fe54-4e92-913c
```Substitute your login name for yourusername (don't forget the trailing colon) and substitute your UUID string for the d310-etc. This will change the permission of the mountpoint /media/whatever to your ownership and allow you to write to the partition. The mountpoint is a folder in /media created when the drive is automounted but deleted when unmounted. But, here's the magic bit. The system "remembers" the ownership of the mountpoint and when you plug the drive in again, /media/d310e646-fe54-4e92-913c is re-created but owned by you and not by root. I discovered this by accident. So long as the mountpoint doesn't change you don't have to do anymore chown-ing.

---

### Post by a.v.l on 2010-08-29
> **coffeecat said:**
> What was the error message, and have you the package ntfsprogs installed? It's a pity that you haven't been able to format it NTFS because you won't get the permissions problems you are having with ext3.



As sharathcshekhar said, the lost+found folder is normal in an ext partition.

The error message is because the ext3 partition is mounted by root. Unfortunately, whether you let it automount or mount it manually as sharathcshekhar describes, it will still be owned by root and you will get an error unless you use a root nautilus. But you don't want to do that. There is a better way.

Plug the drive in and let it be automounted. Let the Nautilus (file browser) window open showing the contents of the ext3 partition. Now press ctrl-L and the breadcrumb location trail will change to the location shown as a path: something like /media/whatever. Make a note of the whatever. It'll either be the partition label (which I don't think you've applied) or the UUID which is a long string of alphanumeric characters.  Let's assume the string is 'd310e646-fe54-4e92-913c'. (It'll be much longer.) Now open a terminal and:

```
sudo chown yourusername: /media/d310e646-fe54-4e92-913c
```Substitute your login name for yourusername (don't forget the trailing colon) and substitute your UUID string for the d310-etc. This will change the permission of the mountpoint /media/whatever to your ownership and allow you to write to the partition. The mountpoint is a folder in /media created when the drive is automounted but deleted when unmounted. But, here's the magic bit. The system "remembers" the ownership of the mountpoint and when you plug the drive in again, /media/d310e646-fe54-4e92-913c is re-created but owned by you and not by root. I discovered this by accident. So long as the mountpoint doesn't change you don't have to do anymore chown-ing.

Thanks for both of your replies. Before trying any of your latest advice I decided to try and create an NTFS partition again. So I created a new partition table and then tried to reformat the drive as NTFS, surprisingly it worked perfectly and I now have access to the drive. It appears that my problem has been resolved, thanks very much again.

---

### Post by coffeecat on 2010-08-30
I'm glad to hear formatting as NTFS worked for you at last. Just a few comments about NTFS. The reason you are not getting the permission error that you got with ext3 is that NTFS, being a Windows filesystem, does not support Unix/Linux permissions. But this does lead to one oddity. If you automount a NTFS drive, copy a file to it and right-click > Properties > Permissions, it seems to be owned by root. That's only because root does the mounting. It's just a quirk. There is no Linux ownership as such on a NTFS drive. You'll sometimes come across people posting, "Help. All my NTFS files are owned by root and I can't chown them." You don't have to. Don't worry about it.

The other thing is that if you get a filesystem corruption you need to use Windows chkdsk for repair. There are Linux ntfs tools, but they are not as comprehensive as the Windows ones.

Good luck!

---

### Post by a.v.l on 2010-08-30
> **coffeecat said:**
> I'm glad to hear formatting as NTFS worked for you at last. Just a few comments about NTFS. The reason you are not getting the permission error that you got with ext3 is that NTFS, being a Windows filesystem, does not support Unix/Linux permissions. But this does lead to one oddity. If you automount a NTFS drive, copy a file to it and right-click > Properties > Permissions, it seems to be owned by root. That's only because root does the mounting. It's just a quirk. There is no Linux ownership as such on a NTFS drive. You'll sometimes come across people posting, "Help. All my NTFS files are owned by root and I can't chown them." You don't have to. Don't worry about it.

The other thing is that if you get a filesystem corruption you need to use Windows chkdsk for repair. There are Linux ntfs tools, but they are not as comprehensive as the Windows ones.

Good luck!

Many thanks, you've been a real help.

---

