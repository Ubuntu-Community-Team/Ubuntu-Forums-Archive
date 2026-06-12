---
title: "how to partition extra HDD space?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by mr clark25 on 2009-11-12
I have an extra 200GB on my 250 GB hdd, (originally reserved for windows when it crashed, then I realized 9.10 can everything that it can) I have it currently partitioned as FAT32. is that right? i know it is usable, but is that how I'm suposed to have it? (i also patitioned my USB flashdrive as FAT32)

just double checking, i didn't want to miss out some feature or something....

---

### Post by coldReactive on 2009-11-12
install ubuntu to take over the entire disk next time you install so you don't have this issue. ;)

I honestly don't use more than... 11 GB of space on my 500 GB Drive. (I use external flash drives for music and documents.)

---

### Post by alphaniner on 2009-11-12
You'd definitely be missing features if you tried to use a Microsoft partition.  First and foremost, the ability to install Linux. ;)

If you don't have data to save, using the entire drive is a good place to start.

---

### Post by dmillerct on 2009-11-12
> **mr clark25 said:**
> I have an extra 200GB on my 250 GB hdd, (originally reserved for windows when it crashed, then I realized 9.10 can everything that it can) I have it currently partitioned as FAT32. is that right? i know it is usable, but is that how I'm suposed to have it? (i also patitioned my USB flashdrive as FAT32)

just double checking, i didn't want to miss out some feature or something....

You can also just use gparted to format the partition to ext and then use it for storage without reinstalling Ubuntu. 

this will remove all data from the partition.

```
sudo apt-get install gparted
```

---

### Post by mr clark25 on 2009-11-12
I don't have any data to save(from windows).

i used gparted to partition it as FAT32, and am just wondering if that was the right thing to do. i thought that when you altered a partition (even when you exstend it)? i would have done that from the start if i knew that. (i want re-assured on that.) 
just wanted to make sure that i did the right thing and now it sounds like i might do it differently...

---

### Post by coldReactive on 2009-11-12
> **dmillerct said:**
> You can also just use gparted to format the partition to ext and then use it for storage without reinstalling Ubuntu. 

this will remove all data from the partition.

```
sudo apt-get install gparted
```

What if that partition has to be unmounted, but can't because it's part of the drive ubuntu is on?

---

### Post by dmillerct on 2009-11-12
> **coldReactive said:**
> What if that partition has to be unmounted, but can't because it's part of the drive ubuntu is on?

I am not saying it is ideal but he can do it without having to re-install.

---

### Post by dmillerct on 2009-11-12
> **mr clark25 said:**
> I don't have any data to save(from windows).

i used gparted to partition it as FAT32, and am just wondering if that was the right thing to do.

ubuntu uses ext4 by default but will recognize FAT32. Its fine.

---

### Post by DGortze380 on 2009-11-12
I suggest NTFS over FAT32.

There are no files size limits, and it corrupts less easily.

---

### Post by dmillerct on 2009-11-12
> **DGortze380 said:**
> I suggest NTFS over FAT32.

There are no files size limits, and it corrupts less easily.

That is a good point. Dont you need to install something to read/write NTFS drives or is it native in Karmic?

---

### Post by DGortze380 on 2009-11-12
> **dmillerct said:**
> That is a good point. Dont you need to install something to read/write NTFS drives or is it native in Karmic?

Should be installed by default.

If not, the package is ntfs-3g

---

### Post by coldReactive on 2009-11-12
> **DGortze380 said:**
> I suggest NTFS over FAT32.

There are no files size limits, and it corrupts less easily.

*cough*

> Architecturally: 16 exabytes minus 1 KB (264 bytes minus 1 KB)

Implementation: 16 terabytes minus 64 KB (244 bytes minus 64 KB)

From: [http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx)

---

### Post by Ozitraveller on 2009-11-12
try here : [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by sawick61 on 2009-11-12
> **mr clark25 said:**
> I don't have any data to save(from windows).

i used gparted to partition it as FAT32, and am just wondering if that was the right thing to do. i thought that when you altered a partition (even when you exstend it)? i would have done that from the start if i knew that. (i want re-assured on that.) 
just wanted to make sure that i did the right thing and now it sounds like i might do it differently...

The right thing to do?  It all depends what you're trying to do.  If you want to use it for more storage in conjunction with your Ubuntu installation, you'll have to reformat it as "ext'.  If you're trying to use it for Windows, everything after post Windows 98 uses "NTFS".  Also, no kidding you don't have any data to save from windows...you already formatted it.

---

### Post by mr clark25 on 2009-11-13
i am mostly sure you do, because it was formatted as NTFS once and in 9.04 gparted would recognize it as "unknown".

---

### Post by egalvan on 2009-11-13
FAT32 is an older allocation method, never intended for large drives, such as 200,000 megabytes (200GB)

If the machine only has Linux, I would suggest ext3.
As for "features", here are some...
It is stable and safe, with a long history.
It was designed to be extensible.
Journaling keeps data safe.
Linux-style permissions and ownership are maintained correctly.
It's Open and Free.

NTFS is a second choice.
Far second.
Far, far second.
some of its "features...
No real journal.
No Linux-style permissions or ownership.
it's closed-off, and proprietary.

---

### Post by DGortze380 on 2009-11-13
> **coldReactive said:**
> *cough*



From: [http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx)

really now ..?

Ok.

There are no currently practical file size limits.

---

### Post by paynek716 on 2009-11-13
> **mr clark25 said:**
> i used gparted to partition it as FAT32, and am just wondering if that was the right thing to do. 

If your drive is strictly Ubuntu you should format the drive either ext3 or ext4. They are both better than FAT32 for handling large drives.

If you have a dual boot installation and want to share files between Ubuntu and Windows NTFS is the best format. If you have no need to share data with Windows you want ext3 or ext4.

---

### Post by mr clark25 on 2009-11-14
ok, i will partion it as ext3, since almost everyone seems to think it is best.

one more thing: i am making a folder in it visible to another computer on my network, so i hope ext 3 is still the way to go

---

### Post by DGortze380 on 2009-11-14
> **mr clark25 said:**
> ok, i will partion it as ext3, since almost everyone seems to think it is best.

one more thing: i am making a folder in it visible to another computer on my network, so i hope ext 3 is still the way to go

Network shares shouldn't be dependent on file system type.

---

### Post by theozzlives on 2009-11-14
Funny nobody is recommend that this extra space be turned into a /home partition. That's the best way to go.

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by urdrwho on 2009-11-14
Oh, this isn't good news.  My 200 gig HD that I mentioned is FAT32.  It is a Maxtor and that is how it came formatted.  It is also a back drive for a Win98 machine.

The answer is getting to be too difficult.  Maybe Ubuntu will just stay as something I play with once in a while.

---

### Post by mr clark25 on 2009-11-15
i might try just copying my /home folder to the new partition. thanks for the idea. i might down the partition size to 30 GB and use the rest for a different installation... any thoughts on that? it also says that 10 GB are used when i dont ave anything on the drive. it automatically put lost and found on it, but would it take up 10GB? when i right-click and hit properties, it says it has one thing on it and it is only 168KB, but yet it says 10GB are used...

one thing i dont like about ext3 is that it now says that it is owned by root. so, do i just use the command: sudo cp ?   or is there a way to make it so it say that i own the drive? it sure would be a lot easier if i could make it mine...

---

