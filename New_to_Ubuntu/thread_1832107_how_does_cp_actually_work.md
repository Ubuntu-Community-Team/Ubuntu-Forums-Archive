---
title: "how does cp actually work?"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by blackest_knight on 2011-08-24
i'm not asking about the syntax but the actual way the command functions 

mv is fast since it doesn't have to copy the file it just says file x is now in folder y


however with copying the file is copied byte for byte to a new location  creating a second file.

now the bit i'm interested in my external sata drive is connected via usb to my netbook. I'm using find to locate all my mp3 files on my drive and put a copy of them in another location on the same drive prior to sorting them to a new folder structure also located on the same drive.

the question really is do all the bytes i am moving have to transfer by the usb cable to my laptop then go back to the drive or is the drive smart enough just to copy from one hard drive sector to another ?

usb is going to be a horrible bottle neck if the transfer speed is tied to the speed of the usb bus ...

---

### Post by androssofer on 2011-08-24
> **blackest_knight said:**
> i'm not asking about the syntax but the actual way the command functions 

mv is fast since it doesn't have to copy the file it just says file x is now in folder y


however with copying the file is copied byte for byte to a new location  creating a second file.

now the bit i'm interested in my external sata drive is connected via usb to my netbook. I'm using find to locate all my mp3 files on my drive and put a copy of them in another location on the same drive prior to sorting them to a new folder structure also located on the same drive.

the question really is do all the bytes i am moving have to transfer by the usb cable to my laptop then go back to the drive or is the drive smart enough just to copy from one hard drive sector to another ?

usb is going to be a horrible bottle neck if the transfer speed is tied to the speed of the usb bus ...

did a quick test for ya. copied a video file from my comp to my external HD with cp. then used cp again to move it into a sub folder on the external HD. it seemed the moving it to a sub folder was slightly quicker, perhaps cus the file was still in memory, but i think they are about the same speed, so i'd guess that yes, it bottlenecks at the USB if u use cp on the external drive

---

### Post by 3rdalbum on 2011-08-24
My understanding is that it sends the data to your computer, then back out to the drive. The disk itself isn't smart enough to be able to perform the copy, and the disk doesn't understand a filesystem anyway so it wouldn't be able to store the file correctly.

On a similar note, if you mount a network drive from your server on your client computer, then copy a file from one folder to another on that same drive, the data will go to the client and then back to the server. I've never understood why the designers of SMB, Appletalk, NFS etc never had some function where you can say to the server "Do this copy" rather than clogging up the network sending the data to the client and then back to the server again.

---

### Post by aeiah on 2011-08-24
on the same filesystem, mv just dereferences the file and creates a new reference elsewhere (x is now y), as you understand. cp by default will duplicate the data, as you understand. in relation to this part of your post, there may be something of interest to you though:

> **blackest_knight said:**
> I'm using find to locate all my mp3 files on my drive and put a copy of them in another location on the same drive prior to sorting them to a new folder structure also located on the same drive.



you can create a hard link of your file(s) with cp -al. that is, your data now has two references, pointing to the same data. on the surface it seems like a symlink, but its really more similar to mv, except it doesnt remove the initial reference (x). now, your file exists at both x and y. you can 'delete' x, and y will still exist, and vice versa.

so instead of copying all your mp3 files to a new location and sorting through them, you can just create a new set of references to your mp3s. this will be pretty much instant and not take up any additional drive space. when you've moved the files around, you can delete the old references

---

### Post by The Cog on 2011-08-24
Note that hard links and symlinks can only be stored on linux/unix filesystems. If the external hard drive is formatted with NTFS or FAT, you won't be able to create hard links or symlinks on it.

---

