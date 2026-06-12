---
title: "using dd to image drive takes long time"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by HunkirDowne on 2009-02-15
Not exactly an absolute beginner, but probably made an error (at least in judgment) that might be helpful for beginners.  For the record, this is the first time I've tried to image a hard disk from the linux command line so it probably fits nonetheless.

dd if=/dev/sda | bzip2 -9 > backup.sda.img

This started at about 5 AM this morning and it's now 9 PM (or close to it).

This is on a 250 GB drive with two primary partitions and no extended partition.  The drive is less than 10% full (~23.5 GB; new laptop).

The time it is taking and the size of the file (so far) has me baffled.  After 16 hours and 24.2 GB so far, I would think I would be close, but am I?  Should I let this go?  Will it go to 250 GB?  I have the disk space but not the patience if this is going to take five more days to finish.

Maybe I should have done 'dd' without piping to 'bzip2' and did 'bzip2' on the resulting dd output.  Ideas?

---

### Post by supersonicdarky on 2009-02-15
It reads the drive, byte by byte, it doesn't matter how filled it is. And I doubt it would be faster if you didn't pipe it. Also you'd probably run out of space.

---

### Post by Dr Small on 2009-02-15
From reading the manual, you can specify a byte size with BS=n, so you can use something like this which should help speed it up:
```
BS=1M
```

---

### Post by MarblePanther on 2009-02-15
> **Dr Small said:**
> From reading the manual, you can specify a byte size with BS=n, so you can use something like this which should help speed it up:
```
BS=1MB
```

BS=4M

will be faster   4M not 4MB asfaik

---

### Post by HunkirDowne on 2009-02-15
> **supersonicdarky said:**
> It reads the drive, byte by byte, it doesn't matter how filled it is. And I doubt it would be faster if you didn't pipe it. Also you'd probably run out of space.

Byte-by-byte, yes, but compressed by bzip2 -- I expected to have a smaller compressed file than one larger than the equivalent uncompressed data.  Perhaps I am wrong?

Also, I said that I had the space but failed to mention how much: 300 GB.  Although this will allow for the full 250 GB image, I don't know if it would allow for the creation of an additional compressed file not knowing how large this thing is going to turn out to be.


Thanks!

---

### Post by HunkirDowne on 2009-02-15
> **MarblePanther said:**
> BS=4M

will be faster   4M not 4MB asfaik

How much faster?  In other words, should I stop what I am doing now and apply this switch?  

Or should I let my painstakingly slow process continue because it's almost done?  In yet other words, when does bzip2 compress?  At the end of the job or during?  Given that the filename that is being created is the one with the expanding byte count, I would have thought 'during'.  But given that the filesize is greater than the sum of the part(ition)s... me not so sure.

So I guess I'm clueless as to how long to expect this thing will take in either time or bytes.  If I knew either I could make a judgment call.  Not knowing either, I'll probably kill it and not even bother with the 4M since I have no gauge how fast it is running now.  I can't afford the time to do this a second time.  I've backed up entire hard disks (same size) in a tenth of the time this is taking but I wanted to stay away from the commercial stuff.


Thanks.

---

### Post by MarblePanther on 2009-02-15
> **HunkirDowne said:**
> How much faster?  In other words, should I stop what I am doing now and apply this switch?  

Or should I let my painstakingly slow process continue because it's almost done?  In yet other words, when does bzip2 compress?  At the end of the job or during?  Given that the filename that is being created is the one with the expanding byte count, I would have thought 'during'.  But given that the filesize is greater than the sum of the part(ition)s... me not so sure.

So I guess I'm clueless as to how long to expect this thing will take in either time or bytes.  If I knew either I could make a judgment call.  Not knowing either, I'll probably kill it and not even bother with the 4M since I have no gauge how fast it is running now.  I can't afford the time to do this a second time.  I've backed up entire hard disks (same size) in a tenth of the time this is taking but I wanted to stay away from the commercial stuff.


Thanks.

It might save you an hour...don't know if its really worth killing the process over or not...

---

### Post by cjv8888 on 2009-02-15
I suggest using partimage from a system rescue CD.  Usually takes only an hour or so to back up a partition.

---

### Post by HunkirDowne on 2009-02-16
well it's done.  19 hours.  I've already done the partimage thing but at the time was concerned with the message I got from fdisk, "Partition 1 does not end on cylinder boundary" but have that one answered now so I have two backups.  I will keep this dd/bzip2 backup for emergencies but figure it will probably take as long to deploy as it did to create.

Thanks for the help.  If I'm ever possessed to try this again I'll be sure to use the block size switch as previously suggested.

Now that the job is done, I've mounted the partitions and they total 21,810 MiB and the backup is 21,666 MiB.  The total disk size is reported as 238,474 MiB.

So I figure the reason it took so long is the byte-by-byte nature of 'dd' at whatever default block size it uses over the entire disk.  The filesize is determined by the strength of the compression algorithm so 'bzip2 -9' is apparently not as compressed as gzip with defaults.

Thanks again for the help.  If by logging this here I've helped someone know that 'dd' takes a long time and 'partimage' is quicker, then I've both learned my lesson and helped someone else out as well.

---

### Post by hyper_ch on 2009-02-16
well, what is the transfer speed of the harddisk? And where do you save it to? If you save it onto a usb drive it will be slow...

---

### Post by HunkirDowne on 2009-02-17
> **hyper_ch said:**
> well, what is the transfer speed of the harddisk? And where do you save it to? If you save it onto a usb drive it will be slow...

Good questions to which I do not have immediate answers for, but I used partimage earlier and that took a few hours tops.  'dd /dev/sda | bzip2 -9 > sda.img' took about 19 hours.  Even if you consider the overall size of /dev/sda (238,474 MiB) this would make a transfer rate of 3.5 MiB/s.  But the compressed size was much smaller so the actual transfer would have been like 360 KiB/s.  Mighty slow even for USB.

I think the issues are:
(1) Using 'dd' to backup a large file (in this case a 250 GB HDD)
(2) Not assigning a block size

My reason for using 'dd' in the first place was one of ignorance and caution as I was concerned about the LBA-induced message about the CHS geometry in 'fdisk'.  But since I had already started the job (and had thought, for hours, "it's almost done" ;-), I let it continue on into the night.

So my take-away from this is that 'dd' is great for small files (like the MBR) but partimage is more appropriate for partition-sized files.

Now that I know how long it takes, I may try doing one more 'dd' of the '/dev/sda' and this time use the block size switch ('bs=4M' or 'bs=4MB', the former is "real" megabytes and the latter the SI revision).  Shouldn't take much longer than 24 hours once I have everything configured and ready for my second round of backups.  (I still use partimage initially).


Thanks!

---

### Post by hyper_ch on 2009-02-17
dd truly makes a 1:1 disk image, partimage doesnt :)

USB 2.0 has transfer speeds of about 40 MB/s. If you take a a 1000 GB drive (actually only 953 GB) that would still take 6 3/4 h to transfer it all and USB 1.1 is much slower (I think 1.5 MB/s).

---

### Post by caljohnsmith on 2009-02-17
Just for future reference, you might want to consider using "dcfldd" instead of dd to clone your HDD; dcfldd is the same as dd except with more features, and one of the best features is it displays its progress as it copies. To use it, just do:
```
sudo apt-get install dcfldd
sudo dcfldd if=/dev/sda statusinterval=10 bs=10M conv=notrunc | bzip2 -9 > backup.sda.img
```
When you use a block size larger than one sector, it is important to use the "conv=notrunc" option, because that makes sure you copy every single sector of your HDD even if your HDD size is not an exact multiple of the block size you choose. And with a "statusinterval" of 10 and a block size of 10 MB as shown above, dcfldd will update its progress every 10 X 10 MB = 100 MB. You could use statusinterval=100 to get the progress for every 1 GB copied for example. Anyway, that's how I would do it if I were in your shoes. :)

---

### Post by HunkirDowne on 2009-02-17
Many thanks!  I prefer 1:1 (all things being equal) for a complete backup of drives.  The status monitor will come in handy as well.  Also, good catch with notrunc -- I hadn't considered that.

Not all my disks are this way, but I have one that is exact in it's byte and cylinder counts.  That is, it has 7296 cylinders where each cylinder is 8225280 bytes AND the total bytes is the exact multiple.  In that case, should I not be able to use block sizes anywhere from 7296 bytes to 8225280 bytes (if I were so bold as to make it that big)?

---

### Post by caljohnsmith on 2009-02-17
> **HunkirDowne said:**
> 
Not all my disks are this way, but I have one that is exact in it's byte and cylinder counts.  That is, it has 7296 cylinders where each cylinder is 8225280 bytes AND the total bytes is the exact multiple.  In that case, should I not be able to use block sizes anywhere from 7296 bytes to 8225280 bytes (if I were so bold as to make it that big)?
Actually, the number of cylinders your HDD has is irrelevant, because that is just an arbitrary number based on whatever geometry your partitioning program originally assumed when it partitioned your HDD. In other words, physical CHS geometry (Cylinders, Heads, Sectors) is not relevant to today's modern drives since the technology outgrew that many years ago. Therefore, partitioning programs are free to assume whatever CHS geometry they please, but at least for linux, the standard is usually 255 heads, 63 sectors/track geometry (but that's still an arbitrary standard). So the bottom line is, choose whatever block size you want, but just remember to use the "conv=notrunc" option so you will always copy every single byte of the source drive no matter what block size you choose.

---

### Post by HunkirDowne on 2009-02-18
> **caljohnsmith said:**
> Actually, the number of cylinders your HDD has is irrelevant, ... So the bottom line is, choose whatever block size you want, but just remember to use the "conv=notrunc" option so you will always copy every single byte of the source drive no matter what block size you choose.

Good enough for me.  I'll be sure to **always** use the *notrunc* option as above so I don't get disappointed should I actually have to use the backup.

Thanks again!

:popcorn:

---

### Post by jerome1232 on 2009-02-18
Another tip to get better compression of the image file is to zero out free space before starting, this makes for better compression because free space actually still has the old data in it, for example just use dd to write an image file containing zeros which fills up the drive, then delete the image file.

```
dd if=/dev/zero of=/anywhere.zeros bs=4M conv=notrunc
rm /anywhere.zeros
```

---

### Post by HunkirDowne on 2009-02-18
> **jerome1232 said:**
> 
```
dd if=/dev/zero of=/anywhere.zeros bs=4M conv=notrunc
rm /anywhere.zeros
```

What kind of object is /dev/zero?  'ls -l' shows "crw-...".  What be 'c'?

(and what are you doing up this late/early? ;-)

So, if I get this right, the first command would fill the remaining free space of my drive with the 'of' and then delete that file taking me back (essentially) where I was but only cleaner.

I think I'll do this with no other apps open and I may even just exit X and do it from text.  Wouldn't want /tmp or any user directories to get populated at the time, or do I worry needlessly?

---

### Post by jerome1232 on 2009-02-18
It's a character device file, it just spits out zeros. There's also /dev/random which generates random data, useful for prepping a drive for encryption.

> Devices are divided into two types: character devices and block devices. The difference is that block devices have a buffer for requests, so they can choose by which order to respond to them. This is important in the case of storage devices, where it's faster to read or write sectors which are close to each other, rather than those which are further apart. Another difference is that block devices can only accept input and return output in blocks (whose size can vary according to the device), whereas character devices are allowed to use as many or as few bytes as they like. Most devices in the world are character, because they don't need this type of buffering, and they don't operate with a fixed block size. You can tell whether a device file is for a block device or a character device by looking at the first character in the output of ls -l. If it's `b' then it's a block device, and if it's `c' then it's a character device. 

---edit---

I might ask you the same question! Actually I was about to go running :)

---

### Post by Keermalec on 2009-10-31
clonezilla 1m 30 seconds to restore an image of 25Gb of data from a 320Gb drive.

---

