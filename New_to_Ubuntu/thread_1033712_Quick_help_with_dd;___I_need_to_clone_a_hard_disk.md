---
title: "Quick help with dd;   I need to clone a hard disk"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by egalvan on 2009-01-07
I did a quick search for "dd" postings, but came up confused.


Scenario:

I have a customer's computer with a 250Gb hard drive.
Her husband did a format and re-install of XP. Wife very un-happy.

I need to return the computer as quickly as possible, so...
I have a 250Gb drive that I want to "clone" the customer drive onto,
then I can try recovering any document and jpg files that may have been left (doubtful, I know, but he's paying the piper.)

1st question
is it possible to set the original drive to "read-only" to reduce any problems? Original drive must remain un-touched.

2nd question
does the destination drive need to be formatted?
my understanding is; no format needed. True?

3rd question
what is the SIMPLEST way to simply clone the drive from one 250gb drive to another?
Are there any options that would help in increasing SAFETY?
SPEED is secondary... the original MUST remain untouched by ME.

I have two more days to return the computer, so the clone/copy operation can take up to 48hrs (safety first, speed second).

The original drive has approx 150gb used on it.

And then I can take whatever time I wish to invest in running file recovery software on the clone.

Again, I do not want to touch the original drive.

Thanks

Any pointers to SIMPLE examples will be most appreciated.
Most examples I've seen have been too complicated

Again, thanks.

ErnestG

---

### Post by JoshuaRL on 2009-01-07
I would suggest using a Live CD, and gparted.  You can either mount the hard drive to the Live CD and pull files off, or you can use gparted to copy the partition to the other drive.

---

### Post by egalvan on 2009-01-07
> **JoshuaRL said:**
> I would suggest using a Live CD, and gparted.  You can either mount the hard drive to the Live CD and pull files off, or you can use gparted to copy the partition to the other drive.

sounds reasonable,

question..
will this copy EVERYTHING, including "empty", "unused" sectors?

I know dd will do a "byte-for-byte" copy, whether it's in use or not, empty or not.

I need to find erased/deleted/removed files, remember.

---

### Post by AndyCee on 2009-01-07
I'm not sure how you have the drives connected, but say the customer's HD is /dev/sda and yours is /dev/sdb. Browse the filesystem to make sure you know which is which.

1) Yes.
When you mount the customer's HD, use the 'readonly' option. The disk will not be touched in this mode.

ie.
```
sudo mount /dev/sda /where/you/want/to/mount -o readonly
```

If you're not sure if this worked, just look for a safe place on the HD and try to save 'blank.txt' or such.

2) The destination does not have to be formatted. The easiest & safest way IMO to do it is to make an iso file.

The dd command will be:

```
dd if=/where/you/mounted/HD of=/where/you/want/backupfile.iso
```
So the HD will be backed up to an iso file, which you can mount in any filesystem and look over in any operating system.

It could take a long time, and dd gives no status messages.

---

### Post by kestrel1 on 2009-01-07
For cloning you could try Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)
But if the drive has been formatted & you are wanting to recover files using some sort of file recovery software you would need the original drive, as I don't think that the data would transfer well for recovery.
Why such a short time to get the machine back & why can't you touch the drive? I know, mind your own business :lolflag:

---

### Post by AndyCee on 2009-01-07
I'll just mention, for absolute byte-for-byte accuracy you might need to clone the partition directly.

ie. dd if=/dev/sdX of=/wherever/backup.iso

The command works like this:

**if=somewhere**
Where data is read from. I use it to back up cd's or DVD's using dd if=/dev/dvd

**of=somewhere**
Where data is put to
You can probably do that straight to another device, though I've not tried it myself, the documentation suggests it will work for that purpose. It's just an issue if you have existing data on that drive, as it will overwrite everything including the MBR.

I'm not sure if the first way will preserve everything, and this way while /dev/sdX will remain untouched, if you get it wrong you'll corrupt the data on the partition.

[http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/](http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/)

---

### Post by caljohnsmith on 2009-01-07
Hi Ernest, I just wanted to mention that if you use gparted to copy the Windows partition to another drive, you will just get a copy of the partition without copying the MBR or any unused disk space on the original drive. If you want to use dd to clone the entire drive, I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress, unlike dd where you have no idea how much data has been copied while it runs. You could do the following:
```

sudo apt-get install dcfldd
sudo dcfldd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] of=/dev/[COLOR="Blue"]<destination drive>[/COLOR] statusinterval=10 bs=10M conv=notrunc
```
The "statusinterval" times the "bs" or blocksize is how many bytes dcfldd copies before it updates its progress, so in the above example the progress will be updated for every 10M X 10 = 100 MB of data copied. Using a blocksize of 10 MB works well, because that means dd copies 10 MB chunks at one time, rather than the default which is only 32 kB. That means the copying goes alot faster. Also, to try and answer your questions, I don't know of any way to set your source drive as read-only, but if you are careful with the above command you should be fine. In addition, you don't have to format the destination drive since you will cloning the source drive byte-for-byte. Good luck and let us know how it goes. :)

---

### Post by egalvan on 2009-01-07
> **kestrel1 said:**
> For cloning you could try Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)
But if the drive has been formatted & you are wanting to recover files using some sort of file recovery software you would need the original drive, as I don't think that the data would transfer well for recovery.
Why such a short time to get the machine back & why can't you touch the drive? I know, mind your own business :lolflag:

Clonezilla is not an option.

Forensic analysis of hard drives is often done on a copy.
Law-enforcement-level copies can be done with 'dd', as courts have held this a valid technique to assure a complete, legitimate copy.

I have a friend who does this kind of stuff for a living.
and no, I can't ask him to do this for me...in this case...

As for the short time-frame, the lady needs the computer back at the start of her class-work.

And I can't touch the drive, so as to be able to certify that I did not damage, delete, erase or remove any data on that drive.

Normally, I would sub-contract this out, but this is a "special" exception.

It's called "pro bono" work.

---

### Post by eatberrys on 2009-01-07
If u have ever read 2600 the most recent relase has a very good data recovery tutorial useing a live cd the dd command and foremost its very simple and effective for what your doing.

O btw since he didnt only format he reinstalled he wrote over the data so you probley wont be able to recovery every thing

---

### Post by kestrel1 on 2009-01-07
Fair enough.

---

### Post by egalvan on 2009-01-07
> **caljohnsmith said:**
> Hi Ernest, if you use gparted to copy the Windows partition to another drive, you will just get a copy of the partition without copying the MBR or any unused disk space on the original drive.

Yeah, that's what I've been told...

>  If you want to use dd to clone the entire drive, I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress, unlike dd where you have no idea how much data has been copied while it runs. You could do the following:
```

sudo apt-get install dcfldd
sudo dcfldd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] of=/dev/[COLOR="Blue"]<destination drive>[/COLOR] statusinterval=10 bs=10M conv=notrunc
```
The "statusinterval" times the "bs" or blocksize is how many bytes dcfldd copies before it updates its progress, so in the above example the progress will be updated for every 10M X 10 = 100 MB of data copied. that means the copying goes alot faster.

As long as it finishes in less than 48 hours.


>  to try and answer your questions, I don't know of any way to set your source drive as read-only, but if you are careful with the above command you should be fine. In addition, you don't have to format the destination drive since you will cloning the source drive byte-for-byte. Good luck and let us know how it goes. :)

Well, as always, a well-spring of information from caljohn...

On the machine I will be using (Core2Duo with 8gig RAM, overkill)

I will only have a cd drive, and the two SATA drives.

and I will use terminal off of a ubuntu 8.04.1 LiveCD.

So I'm going out on a limb here and making an assumption, caljohn...


<source drive>
 and
<destination drive>

refer to sda and sdb?


Correct so far?

And many thanks.

ErnestG

---

### Post by egalvan on 2009-01-07
> **eatberrys said:**
> If u have ever read 2600 the most recent relase has a very good data recovery tutorial useing a live cd the dd command and foremost its very simple and effective for what your doing.

I am not familiar with "2600"

> O btw since he didnt only format he reinstalled he wrote over the data so you probley wont be able to recovery every thing

Worse, he not only formated and reinstalled, but he used the machine for some two weeks before his wife found out about it...

---

### Post by bumanie on 2009-01-07
dd as caljonsmith has said would be the best method as far as I'm concerned. You could also use dd_rescue. This will try to copy bad sectors whereas, dd will just fill them with zeroes. If you are sure there are no bad sectors, use dd. If there is a chance of bad sectors dd_rescue would be the better choice. For file recovery, one of the best tools is photorec - it recovers 100+ file types and is filesystem independent. Foremost, scalpel and sleuth kit/autopsy are also other possibilities along with magicrescue.

---

### Post by caljohnsmith on 2009-01-07
> **egalvan said:**
> 
So I'm going out on a limb here and making an assumption, caljohn...


<source drive>
 and
<destination drive>

refer to sda and sdb?


Correct so far?

And many thanks.

ErnestG
Before using dcfldd, I would first do:
```
sudo fdisk -lu
```
And then looking at the drive sizes and partitions listed, it should hopefully be clear which are the source and destination drives. I would use that info, because I don't think it is safe to assume the source drive of your client will necessarily be sda, and as you've all ready expressed concern for, it would be quite devastating to mix the source and destination drives in the dcfldd copy.

---

### Post by egalvan on 2009-01-07
> **caljohnsmith said:**
> Before using dcfldd, I would first do:
```
sudo fdisk -lu
```
And then looking at the drive sizes and partitions listed, it should hopefully be clear which are the source and destination drives. I would use that info, because I don't think it is safe to assume the source drive of your client will necessarily be sda, and as you've all ready expressed concern for, it would be quite devastating to mix the source and destination drives in the dcfldd copy.

The drives are basically identical 250gb drives.

The only difference, 

her drive has XP installed on one partiion, and lots and lots of files.
Hooked up to the first SATA port

My drive will be thoroughly wiped, fully empty (oxymoron alert :))
Hooked up to the third SATA port.

---

### Post by egalvan on 2009-01-07
> **bumanie said:**
> dd as caljonsmith has said would be the best method as far as I'm concerned. You could also use dd_rescue. This will try to copy bad sectors whereas, dd will just fill them with zeroes. If you are sure there are no bad sectors, use dd. If there is a chance of bad sectors dd_rescue would be the better choice. For file recovery, one of the best tools is photorec - it recovers 100+ file types and is filesystem independent. Foremost, scalpel and sleuth kit/autopsy are also other possibilities along with magicrescue.

As far as errors on the original drive, there seem to be none.
As far as non-writable techniques could tell me...

And I'll start across that forensic-work bridge when I get a good copy...
no need for me to jump the gun:o

---

### Post by caljohnsmith on 2009-01-07
> **egalvan said:**
> The drives are basically identical 250gb drives.

The only difference, 

her drive has XP installed on one partiion, and lots and lots of files.
Hooked up to the first SATA port

My drive will be thoroughly wiped, fully empty (oxymoron alert :))
Hooked up to the third SATA port.
OK, how about unhooking one of the drives, say your destination drive for example, and then run "sudo fdisk -l" and look for the "Disk Identifier" of the source drive:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
[COLOR="Blue"]Disk identifier: 0xab030901[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81920159    40960048+   7  HPFS/NTFS
/dev/sda2        82043955   123620174    20788110   83  Linux
/dev/sda4       123620175   156296384    16338105    5  Extended
/dev/sda5       123620238   154240064    15309913+  83  Linux
/dev/sda6       154240128   154272194       16033+  83  Linux
/dev/sda7       154272258   154336454       32098+   7  HPFS/NTFS
/dev/sda8       154336518   156296384      979933+  82  Linux swap / Solaris
```
Then you should know for sure which is the source drive by identifying it with its disk signature as shown above, because your destination drive should have a different disk signature. Would that maybe help?

---

### Post by egalvan on 2009-01-07
> **caljohnsmith said:**
> 
Then you should know for sure which is the source drive by identifying it with its disk signature as shown above, because your destination drive should have a different disk signature. Would that maybe help?

Again, exactly the information I need...

Very helpful...

Thanks

ErnestG

---

### Post by egalvan on 2009-01-07
> **kestrel1 said:**
> Fair enough.


Fair?:confused:

First I have to spend hours learning this method of forensics analysis...:(

Then I have to spend more hours actually trying to recover something from this quagmire...:neutral:

all with not one cent of compensation...:cry:

What do you think I am?:shock:

A Ubuntu Forum Administrator?\\:D/

A Moderator?:P


Absolutely ):P

---

### Post by egalvan on 2009-01-07
Seriously folks,

I want to say "many thanks" for all the ideas posted in answer to my questions....

I think (hope?) I have enough ammunition to tackle this project.

I will post back in a few days with the results of the "clone" project...if anyone is still interested by then.

Thank you, Ubuntu Forum Members.

ErnestG

---

### Post by handydan918 on 2009-01-07
Oh, we're intersted! We really want to know what kind of files you're looking for!

:popcorn:

---

### Post by honeybear on 2011-08-20
and the command line PARTX (from partimage), would it be faster than his 48 hours he said with dd like?

---

