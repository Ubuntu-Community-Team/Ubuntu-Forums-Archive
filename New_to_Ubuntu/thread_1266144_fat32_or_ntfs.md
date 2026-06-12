---
title: "fat32 or ntfs"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by rabbi burns on 2009-09-14
I want to place my films on a hard drive some have 6X 1gb  VOB   files is it possible to play/download these back uninterrupted using fat 32?   I have heard it is faster.Thanks.

---

### Post by stim on 2009-09-14
The only thing you should need to worry about is if you have files over 4gb. FAT32 will not be able to store these files (as it is a 32 bit filesystem and therefore 2^32 ~= 4 billion).

Ntfs should present you with no problems.  I have a 1tb ntfs external drive and a 500gb internal ntfs drive that I access from within ubuntu, with no problems.

---

### Post by rabbi burns on 2009-09-14
> **stim said:**
> The only thing you should need to worry about is if you have files over 4gb. FAT32 will not be able to store these files (as it is a 32 bit filesystem and therefore 2^32 ~= 4 billion).

Ntfs should present you with no problems.  I have a 1tb ntfs external drive and a 500gb internal ntfs drive that I access from within ubuntu, with no problems.

 yes but as I have a terminally slow usb dongle will fat 32 deliver faster download speeds.thanks

---

### Post by scorp123 on 2009-09-14
Those are Micro$oft formats ... Given that you are on a Linux forum I'd assume you're a Linux user too? So why not use a Linux filesystem then? They are vastly superior.

---

### Post by halitech on 2009-09-14
the USB connection will be the bottleneck as a hard drive is faster (format doesn't really matter) then the USB will allow data to be transfered.

---

### Post by stim on 2009-09-14
As halitech said, the bottleneck will be usb, so there is nothing to be gained over one filesystem or another.  


If you ever need to use the usb dongle on a windoze based pc, keep it ntfs, otherwise i would suggest ext3 or reiserfs.

---

### Post by rabbi burns on 2009-09-14
> **scorp123 said:**
> Those are Micro$oft formats ... Given that you are on a Linux forum I'd assume you're a Linux user too? So why not use a Linux filesystem then? They are vastly superior.

 How? Please explain what is the linux file system in formating the hd ie dos fat32 fat 16 ntfs. ex2 ex3  etc I dont know which one to pick I use Ubuntu almost exclusively now.but obviously struggle with the learning curve.

---

### Post by rabbi burns on 2009-09-14
> **stim said:**
> As halitech said, the bottleneck will be usb, so there is nothing to be gained over one filesystem or another.  


If you ever need to use the usb dongle on a windoze based pc, keep it ntfs, otherwise i would suggest ext3 or reiserfs.

 thanks whats the advantage of reiserfs over ext3.

---

### Post by JDShu on 2009-09-14
Note that FAT32 will work well with OSX, Windows, and Linux, so it is the best choice if you want to be able to move data between all types of computers.

---

### Post by rabbi burns on 2009-09-14
> **halitech said:**
> the USB connection will be the bottleneck as a hard drive is faster (format doesn't really matter) then the USB will allow data to be transfered.

 Thanks I suppose theirs no way to bypass the usb on a laptop with an express card adapter or similar.

---

### Post by halitech on 2009-09-14
> **rabbi burns said:**
> Thanks I suppose theirs no way to bypass the usb on a laptop with an express card adapter or similar.

If you have a spare PCMCIA slot, you could look at see if you can find a USB 2.0 card but the connection will still bottleneck at the USB connection but USB2.0 will be faster then USB 1.1

---

### Post by 3rdalbum on 2009-09-14
Reading from fat32 or NTFS will be fine. Writing to NTFS will be slow, and writing to fat32 means that you can't write files over 4 gigabytes.

If you don't want to use your USB drive with Windows, then just format it as ext3. I don't think you'll see any advantage to ReiserFS. Ext3 is fine.

---

### Post by scorp123 on 2009-09-14
> **stim said:**
> As halitech said, the bottleneck will be usb, so there is nothing to be gained over one filesystem or another. One word: Fragmentation.

I don't know how you use your USB sticks ... but I use mine to transfer data from system A to system B and so on. So you'd copy stuff, remove stuff, put on more stuff, remove stuff again, put on more stuff ... remove stuff again. Move stuff around, and so on.

A USB harddisk or a USB stick with FAT32 will fragment fast like hell. NTFS does a better job ... but it's still not perfect. It still fragments pretty fast causing I/O operations to slow down over time.

Besides that the default block sizes that FAT, FAT32 and NTFS choose are guaranteed to waste space. Example: You put a 4K file into a 10K block ... Taddaaa! The entire 10K block will be marked as being "used". You lose 6K worth of data. Talking about 4K and 10K and so on may sound ridiculous. But if we start talking about transferring your collection of DVD movies or home videos where files easily reach sizes of 4 GB and beyond those lost sectors add up!! Sure: Advanced users know this and will tweak their disks and USB sticks and what not to use better sector sizes ... But "Average Joe" and "Grandma Annie" don't know that and so they won't bother with the tweaking (they probably even don't know how to do that ...). On Linux: No such problems. At all. Ever.

Besides: FAT32 can't cope with files beyond 4 GB in size. So that alone should keep anyone away from using this 8-bit relic (FAT32 is based on the ancient 8-bit MS-DOS filesystem ... yuck!).

So yes, the USB is going to be a bottleneck. Sure. But not the only one. As end-user there's little I can do against the USB bottleneck. But I can do a lot against the filesystem bottleneck by sticking to filesystems that were not designed in Redmond.

My fanboyism and bias aside: Using Linux filesystems only makes sense if you are going to exchange data with other Linux systems.

If you intend to exchange data with Windows systems then you unfortunately have no choice but stick to those inferior Microsoft filesystems. Microsoft Windows operating systems are not able or capable to read any Linux file system "out of the box" and asking the owners of the Windows system you want to exchange data with to first install some Ext3 driver and what not might be perceived as being rather rude ....

So in that case ... yes, you'll have to stick to NTFS or FAT32.

Back to fanboy mode:
If however you only exchange data with Linux systems then there is absolutely no point in using any alien non-Linux filesystems that are inferior by design anyway.

---

### Post by zerhacke on 2009-09-14
I can only in good faith suggest using NTFS on the external drive.  Why not EXT2/3/4?  The user is obviously new to *nix and will have a tough time trying to mount the drive with fstab and get the right permissions and device node and and and and and.

ntfs-3g and ntfs-config will do all the work for him.

---

