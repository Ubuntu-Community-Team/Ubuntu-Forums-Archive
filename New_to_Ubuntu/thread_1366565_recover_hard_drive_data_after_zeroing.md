---
title: "recover hard drive data after zeroing"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2009-12-28
So I did something really really stupid.

Trying to create a usb startup disk as described here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I had a problem which the above noted may be solved by:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334)

The workaround given in that link was to zero the usb stick:
perseus:[~/iso] sudo dd if=/dev/zero of=/dev/sdb bs=1M count=1
perseus:[~/iso] sudo blockdev --rereadpt /dev/sdb


I ran that code as is without thinking.  Too dumb for words.

sdb is (was) my data drive not my usb stick!!!

A lot of very important stuff seems to have been wiped out.

Is there any way (I'm willing to go to great lengths) to recover the data?

---

### Post by phillw on 2009-12-28
> **NewbuntuUser777 said:**
> So I did something really really stupid.

Trying to create a usb startup disk as described here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I had a problem which the above noted may be solved by:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334)

The workaround given in that link was to zero the usb stick:
perseus:[~/iso] sudo dd if=/dev/zero of=/dev/sdb bs=1M count=1
perseus:[~/iso] sudo blockdev --rereadpt /dev/sdb


I ran that code as is without thinking.  Too dumb for words.

sdb is (was) my data drive not my usb stick!!!

A lot of very important stuff seems to have been wiped out.

Is there any way (I'm willing to go to great lengths) to recover the data?


Hi,

 ....... Holy fish-cakes... or words to that effect.

I've looked at data recovery before - I'll go have a dig at what i have - In the meantime - do NOT write any data to the drive !!!

I'll be back presently. Hopefully not empty handed.

Regards,

Phill.

---

### Post by tom4everitt on 2009-12-28
Ouch, easily done. the dd command is really short for data destroyer...

There are certainly ways to recover files though, here's a guide that might help:

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

EDIT: Yes, as the previous poster said, do not write to the hard drive! Do not even try to mount it.

---

### Post by natravis on 2009-12-28
Good luck. I'm not aware of the implications of those particular commands and can't look them up at the moment, but I know that zeroing a drive is one of the surest ways to make data hard to recover. DoD hard drive wipes use zeroing as the first step of 7 to securely wipe their drives. I wouldn't get your hopes up.

Do not take the following as anything other than advice for the future: always have a backup of anything that is not losable and always know what a command does entirely before you use it.

---

### Post by tom4everitt on 2009-12-28
> **natravis said:**
> Good luck. I'm not aware of the implications of those particular commands and can't look them up at the moment, but I know that zeroing a drive is one of the surest ways to make data hard to recover. DoD hard drive wipes use zeroing as the first step of 7 to securely wipe their drives. I wouldn't get your hopes up.

Do not take the following as anything other than advice for the future: always have a backup of anything that is not losable and always know what a command does entirely before you use it.

Looking at his dd line, he had bs=1M and count=1. I think this means that he only destroyed the first megabyte. I don't know what the second command does.

---

### Post by DGortze380 on 2009-12-28
> **NewbuntuUser777 said:**
> So I did something really really stupid.

Trying to create a usb startup disk as described here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I had a problem which the above noted may be solved by:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458334)

The workaround given in that link was to zero the usb stick:
perseus:[~/iso] sudo dd if=/dev/zero of=/dev/sdb bs=1M count=1
perseus:[~/iso] sudo blockdev --rereadpt /dev/sdb


I ran that code as is without thinking.  Too dumb for words.

sdb is (was) my data drive not my usb stick!!!

A lot of very important stuff seems to have been wiped out.

Is there any way (I'm willing to go to great lengths) to recover the data?

You got VERY lucky.

> 
As a workaround, I tried zeroing out the first megabyte of the stick:


It appears as though you may have only overwritten the partition table.

Try test disk to restore it. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

For everyone else in the thread. If data is over written (yes, just 1 pass is sufficient), it is practically unrecoverable. 

Recovery rates are slightly better than 50% (per bit), i.e. you're just as likely to correctly GUESS each and every bit on the drive as you are to recover the data forensically.

---

### Post by Raistlin355 on 2009-12-28
One other thing I would like to add, if you run out of hope and are just gonna reinstall (which I don't recommend) you can dump the entire drive to another drive with photorec, it comes with testdisk.  It is really good at piecing together files that have been obliterated, but you end up with an incoherent mess of files.  They won't have the same names instead they will have a name that corresponds to where it was found on the disk.  It will be a pain to go through all that data, but at least you might have it accessible.

---

### Post by phillw on 2009-12-28
>  For everyone else in the thread. If data is over written (yes, just 1 pass is sufficient), it is practically unrecoverable. 

Practically, being the operative word - After even just one pass, you require a rig that can read the residual magnetism left before that pass - That's serious kit. The other alternative is a specialist recovery company - and that option is not cheap, either.

Phill.

---

### Post by jbrown96 on 2009-12-28
> **phillw said:**
> Practically, being the operative word - After even just one pass, you require a rig that can read the residual magnetism left before that pass - That's serious kit. The other alternative is a specialist recovery company - and that option is not cheap, either.

Phill.

There's no way that the drive can recovery data that has been overwritten. You can have companies take it apart and analyze it, hopefully they can read the residuals, but there's not a chance that the drive heads can. If they could, then hard drives would never work because they couldn't tell what was deleted. 


It does look like it was your partition table plus some. It really depends on how your partition table was configured. If it was one partition, then you may have a decent chance. The problem if you had multiple partitions is that you have to know the exact block where each began and ended. The other concern is that file system information is stored at the beginning of a partition; all this infor for the first partition will be deleted. There are spare superblocks stored throughout the partition (at least for extX), so it may be possible to recover with them, but other file system info may be lost. 

Good luck.

---

### Post by NewbuntuUser777 on 2009-12-28
So I installed testdisk, and ran the analyze feature.

The drive I damaged had ubuntu 9.4 on it and nothing else.  It was 650GB.

The analyze feature found the linux swap partition but nothing else.

I have the option to change the swap's characteristics to one of these:
* primary bootable (it's defualt)
p primary
l logical
e extended
d deleted

And the following actions:
a add partition
l load backup
t change type
or enter to continue

I'm wondering if I should just continue with the swap labeled as the primary bootable?

I've looked through the testdisk documentation but it's not too clear.

---

### Post by NewbuntuUser777 on 2009-12-28
I went ahead and continued and then did the second 'deep' scan.

This seemed to find another swap area before the other one, but it was damaged and so only could be set to D for delete, so for now at least 
I'm stuck.

Does anyone know of any other forums that may be able to walk me through this?

---

### Post by ScottinSoCal on 2009-12-28
> **NewbuntuUser777 said:**
> I went ahead and continued and then did the second 'deep' scan.

This seemed to find another swap area before the other one, but it was damaged and so only could be set to D for delete, so for now at least 
I'm stuck.

Does anyone know of any other forums that may be able to walk me through this?

You don't have the tools to do this, and even if you did, you don't have the knowledge you'd need to do it. You might be able to find someone who could edit the disk manually, but if you knew someone who could do that, I'm guessing you'd know that and you'd be talking to him/her, instead of posting here.

My experience of data recovery services isn't good. Even after spending well over $1K, we got less than 20% of the data back off the disk. And this was a perfectly operational disk that had only been reformatted - an operation very similar to what has happened to your hard drive.

I don't suppose you back up your data?

---

### Post by NewbuntuUser777 on 2009-12-28
> **ScottinSoCal said:**
> You don't have the tools to do this, and even if you did, you don't have the knowledge you'd need to do it. You might be able to find someone who could edit the disk manually, but if you knew someone who could do that, I'm guessing you'd know that and you'd be talking to him/her, instead of posting here.

My experience of data recovery services isn't good. Even after spending well over $1K, we got less than 20% of the data back off the disk. And this was a perfectly operational disk that had only been reformatted - an operation very similar to what has happened to your hard drive.

I don't suppose you back up your data?


That's a pessimistic post, but it may well be accurate.  

I don't know what is meant by someone "who could edit the disk manually".
Do you mean edit the partition table or the mbr or something?

FWIW, the majority of the data was my music collection; about 500GB of 
mp3, flac, etc...  Most of the other stuff (important documents, family 
photos, etc...) is probably backed up piecemeal on various CDs, DVDs, 
backup drives, old emails, relatives and friends computers, etc...  


And in terms of backing up you are completely right.  Dropping $100 on a 
second drive to mirror the music collection seemed excessive before this 
happened.  Now a massive raid array (I use to tease a friend about just 
such a setup) seems obviously prudent.  

You live you learn as they say....

---

### Post by DGortze380 on 2009-12-28
> **NewbuntuUser777 said:**
> That's a pessimistic post, but it may well be accurate.


Maybe, but not necessarily. We've determined that the data has likely not been over written, just the partition table and some surrounding data.

TestDisk would have been the easiest and fastest solution, but clearly there isn't enough left to rebuild.

My next suggestion would be to go buy a second hard drive (You'll want it for backups anyways after all this), and try photorec ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)). This is slightly more low level than TestDisk and will attempt to find and reconstruct individual files, not the partition information.

There are even more options, depending of course on how much time effort and possibly money you want to throw at the problem.

---

### Post by ScottinSoCal on 2009-12-28
> **NewbuntuUser777 said:**
> That's a pessimistic post, but it may well be accurate.

Unfortunately, I think it's accurate. I pondered for a while before posting it, but finally decided to.

> I don't know what is meant by someone "who could edit the disk manually".
Do you mean edit the partition table or the mbr or something?That's exactly what I mean. If you have detailed information about exactly what your partitions were, and if you have access to an identical drive that can be set up the same way, there's a chance the MBR could be reconstructed. I've seen it done, but it's a crap shoot whether it would work. And, of course, if you don't have all of that, then....

> Dropping $100 on a 
second drive to mirror the music collection seemed excessive before this 
happened.  Now a massive raid array (I use to tease a friend about just 
such a setup) seems obviously prudent.  

You live you learn as they say....I did the same thing, and thought I'd lost almost 15 years worth of data. Turned out I still had an old hard drive stored in a static bag, and I got back all but about 6 months worth. I bought another 1TB drive and mirrored my setup before I restored the data off the old drive. 

The drive I sent off for restoration came off the sales manager's computer at my last job. After he told me "Woops, I think I reformatted my drive" he went on to say "Oh, and all our sales contracts are on there. Maybe I should have copied them to the network." As I said, it cost us the other side of $1K, and we got less than 20% of the data back. And none of the sales contracts.

---

### Post by mechro on 2009-12-28
> **NewbuntuUser777 said:**
> 
FWIW, the majority of the data was my music collection; about 500GB of 
mp3, flac, etc...  Most of the other stuff (important documents, family 
photos, etc...) is probably backed up piecemeal on various CDs, DVDs, 
backup drives, old emails, relatives and friends computers, etc...  


+1 for **photorec** in this situation. It should recover mp3's, flac and most photo filetypes.

I've just done a test run of deleting the MBR and partition table on an SD card and Testdisk can't rebuild anything, but Photorec works.

---

### Post by fibercode on 2009-12-28
@ NewbuntuUser777

Rule number one in Data Forensics is to never work on the original.

Most of the recovery tools can do more damage than produce actual results.

First thing you want to do is find another drive of the same or larger size.
Then use ddresque (GNU ddrescue not dd_rescue, there is a difference).

Install the GNU ddrescue:

```
sudo apt-get install gddrescue
```

Then to make an exact copy of your drive to the new one:

```
sudo ddrescue -v /dev/sda /dev/sdb
```

Again... MAKE SURE YOU KNOW WHICH ONE IS THE ORIGINAL AND WHICH ONE IS THE TARGET!

I have done a step by step how to do this:

[http://www.dimitar.me/?p=660](http://www.dimitar.me/?p=660)

---

### Post by markp1989 on 2009-12-28
photo rec is good, i used it to recover my sisters photography work after her colleges computer froze, and corupted the partition table i used dd to make an image of the drive to my hard drivve,, that ran photorec on the image..

---

### Post by NewbuntuUser777 on 2009-12-30
Photorec was able to pull about 20,000 files off the old hard drive so 
far.

Didn't work very well at all for movies/videos, but seems to have worked 
great for the music files (flac, ogg and mp3 at least, looks like I lost 
all the shn and wav files).


Now I just have to figure out what to do with 20,000 unnamed mp3s!

Thanks for everyone's advice.

---

### Post by mechro on 2009-12-30
> **NewbuntuUser777 said:**
> 
Now I just have to figure out what to do with 20,000 unnamed mp3s!


Assuming your mp3's have "tags", **EasyTAG**, available via synaptic, can read and rename files from tag.

---

### Post by Raistlin355 on 2009-12-31
> **NewbuntuUser777 said:**
> 
Now I just have to figure out what to do with 20,000 unnamed mp3s!

Thanks for everyone's advice.


I hear ya been there done that, but at least you HAVE them.
And you welcome always here to help!

---

