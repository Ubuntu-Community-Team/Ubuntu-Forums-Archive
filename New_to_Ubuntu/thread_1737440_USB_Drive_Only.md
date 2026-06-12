---
title: "USB Drive Only?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Glkanter on 2011-04-23
People give me older, no longer being used PCs that I give to 'needy' people that need to start using the internet.

But I'm short on hard drives. But since these are brand new, low expectation users, they don't need a lot of disk space.

The PCs have the boot sequence option for booting from a USB device. And since Ubuntu 10.10 only needs 2.6 GB, why not a USB flash drive?

So, can Ubuntu 10.10 be installed onto a USB flash drive, and can the computer be run without any hard disk at all?

I'm not asking about copying the Live CD to the USB drive, but booting the computer and running Ubuntu as if the USB was an internal hard drive.

Thanks!

---

### Post by satman-ga on 2011-04-23
You should be able to. My concern would be lifespan. Flash drives can only handle so many read/write cycles before they fail. Running as OS off of one will put a considerable load on that drive resulting in premature failure. How soon will it fail? No idea, but it will be considerably faster than a harddrive.

---

### Post by Rex Bouwense on 2011-04-23
Booting from a flash drive probably will result in failure eventually, but I have been saving documents to a 4 Gig flash drive for over two years daily with no indication of failure.  Since flash drives are so cheap, go for it.  Puppy is made to be booted from a CD or flash drive and I haven't read about any complaints of early failure from that.

---

### Post by oldfred on 2011-04-23
Full install to USB is a little slow both due to USB port speed and particularly slow writes on flash. You can reduce writes with some parameter changes.

Suggest at least 8GB as 4GB is tight and I just saw another thread where with Natty they want 5.2GB even though it will install in a lot less. Many try to install in 4GB and run updates and use 3.8GB.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by tordeu on 2011-04-23
I can confirm that USB flash drives are extremely slow. Booting into a live "CD" does take some time. If you want to use a flash drives than I agree that you should go with 8GB. Because of the limited write-cycles a bigger flash drive should enhance the life span, because of the way the flash drives work.

But I would highly suggest cheap hard drives instead. In online shops you can find hard drives for about $20 and given the improved performance, this would - in my opinion - be a better option when it comes to usability.

---

### Post by JustinR on 2011-04-23
Although flash drives have a limited life span, more expensive ones, like Sony Flash Drives, can last past 3,000,000 read/write cycles, instead of 100k and such. There kind of expensive but I've used mine with Ubuntu on it for over two years as my main OS and it still works.

A [8 GB flash drive]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921666128198&tab=featuresTab") from Sony is usually 35$ (but on sale for 20$)

A [16GB Sony one]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921666128182&tab=featuresTab") is 60$ but on sale for 40$

[A 32GB Sony is 90$]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921666232793&tab=featuresTab")

In the end you should consider prices, an HDD from NewEgg.com thats 500GB, was only $50!

---

### Post by tordeu on 2011-04-23
That's exactly the problem. Flash drives which last longer (like the ones you posted) costs as much as a new hard drive. On newegg.com I found hard drives for less than $20. With a budget of $30-$40 (below the 16GB Sony flash drive), you already have several options for a hard drive.

I don't think usb flash drives this is a viable option, yet. Especially with "older" PCs and a limited budget. USB3+expensive usb flash drive might be a different story, but in this case I would vote for a cheap standard hard drive.

---

### Post by snowpine on 2011-04-23
I've been running CrunchBang Linux from an 8gb USB flash drive on a laptop with a failed hard drive. It's not my everyday computer, but it's seen occasional use for about 2 years with no sign of failure. Speed is fine, not fast but it is not a fast computer.

---

### Post by C.S.Cameron on 2011-04-23
If you do the math even a USB drive that is only good for 10000 writes will last years booting Ubuntu, I've never actually heard of anyone wearing one out that way.

Puppy Linux should be as fast running from flash drive as from hard drive as it runs from RAM. 
(Ubuntu is a little slow from flash drive but I find it acceptable).

---

### Post by migs73 on 2011-04-23
> **C.S.Cameron said:**
> 
Puppy Linux should be as fast running from flash drive as from hard drive as it runs from RAM. 
(Ubuntu is a little slow from flash drive but I find it acceptable).

+1 for that. As it runs in RAM the number of read writes to USB should be minimised.
Makes my works XP machines look unbelievably sluggish!!

Mike

---

### Post by tordeu on 2011-04-23
A small distribution like Puppy linux who his able to run from RAM is certainly a good idea if it has to be a usb flash drive. 

"Normal" sized systems like Ubuntu are more problematic, though, because random access on cheap flash drives results in painfully slow performance and that makes the startup significantly in most cases a lot longer than from a hard disk.

I have to disagree with C.S.Cameron, though, that even the 10,000 writes will last years. This can be true, but there are a lot of variables to consider.
First, of course, it depends on how much data is written to the stick every day. Depending on the usage, this can be a great problem.

Some other aspect which is often overlooked: If you have a 4 GB flash drive and 3.5 GB are used for OS+programs+data, then only 0.5 GB remain. That means that 87,5% of the blocks are used and only 12,5% of the blocks are free.
If the data of those 87,5% rarely of maybe never change, then those blocks are "blocked" by the data and all the new/updated data will be written somewhere to those 12,5% remaining free blocks.
That means that the life span is only 1/8th of which it could be, because all the writes are distributed over 12,5% of the blocks instead of 100% of them. The less free blocks remain the more extreme the situation becomes. If the usb flash drive is almost completely full of data, there are only a few blocks left, so the 10,000 write cycles might be achieved fairly fast.

This is a problem particular to usb flash drives and should not occur on ssds (at least on most), because ssds will intelligently move more or less static data from "fresh" blocks to used blocks, so that in the future data is written to those fresh blocks instead of blocks which have been heavily used before. I am not sure if there are usb flash drives which support static wear leveling, but I would suspect that at least all cheap ones do at most offer dynamic wear leveling techniques. 

Therefore, if the os+programs+data barely fit on a usb flash drive, one should consider using a bigger flash drive instead, because those few remaining blocks might be worn out a lot faster, because they will be used more almost all writes.

But of course, a cheap and small usb flash drive with Puppy Linux is a true alternative and Glkanter should definitely consider this.
I just wanted to make the point that hard drives can be pretty cheap and comparible in price at least with usb flash drives >=16GB, so a cheap hard drive is an option as well.

Which way to go depends on several factors. If Puppy Linux is sufficient in this case and there is no demand for space besides maybe a few documents, then a small usb flash drive (2GB/4GB) would be the cheapest option.
If it should be a "bigger " distribution (like Ubuntu), then the performance of a cheap usb flash drive might not be sufficient the the boot time too long. But maybe you should just try it out and see how it works out for you.
Maybe there even would be the possibility of getting your hand on cheap used hard drives. Sometimes, companies give away components or old machines for just a few bucks. Or you can get them on eBay or something. Might be another possibility.

---

### Post by Plumtreed on 2011-04-23
Lubuntu can be installed to 4GB flash drive with room to add a few additional things as desired.

4GBs are going cheaply now....in Aus about AUD5 probably similar in the US

Lubuntu on USB is fast but the speed relates primarily to size of RAM..on a freebee nobody will complain!!!


(BTW...I don't know if USB drives ever breakdown, I haven't lost one yet!!!)

---

### Post by earthpigg on 2011-04-23
> **C.S.Cameron said:**
> If you do the math even a USB drive that is only good for 10000 writes will last years booting Ubuntu, I've never actually heard of anyone wearing one out that way.


This. There will come a time that solid state storage eventually ceases to work if you run an unmodified/stock Operating System (such as vanilla Ubuntu) on it -- but if that time is long-after the rest of the hardware on the system can be expected to have failed, who cares?

---

### Post by FormatSeize on 2011-04-23
> **satman-ga said:**
> You should be able to. My concern would be lifespan. Flash drives can only handle so many read/write cycles before they fail.
This may be a little off topic, but why is this? I had a USB die on me last night when I was making a boot stick for Ubuntu 10.04, and I knew that I had it around for a year or so, but didn't understand why it just all of a sudden died on me.

---

### Post by tordeu on 2011-04-23
> **earthpigg said:**
> This. There will come a time that solid state storage eventually ceases to work if you run an unmodified/stock Operating System (such as vanilla Ubuntu) on it -- but if that time is long-after the rest of the hardware on the system can be expected to have failed, who cares?

I think the problem in this case is that it's hard to predict when a flash drive might fail. There are too many variables which can influence this (the write cycles, the amount of data written, the free space, the wear leveling used, just to name a few), so life span could be anywhere from days to decades.
 
Far more important - in my opinion - is the fact that not many people boot their main system (or a system they really use) from a flash drive, so there is too little real world data. The long term experiences with solid state drives might be somewhat useful for that, though. But it will take years until there is enough long time experience and by that time it might not be possible to compare modern solid state drives to the ones the experience was gathered with.

> **FormatSeize said:**
> This may be a little off topic, but why is  this? I had a USB die on me last night when I was making a boot stick  for Ubuntu 10.04, and I knew that I had it around for a year or so, but  didn't understand why it just all of a sudden died on me.

The blocks on the flash drive just wear out, so they don't work anymore. But in most cases, if you have a usb flash drive for a year, this should not be the reason why it stops working. I would go so far argue that in most cases a flash drive stops working, is not the flash technology that's the problem, but some other part of the flash drive, low quality memory or no/bad wear leveling.

---

### Post by earthpigg on 2011-04-24
> **tordeu said:**
> in most cases a flash drive stops working, is not the flash technology that's the problem, but some other part of the flash drive, low quality memory or no/bad wear leveling.

the 'wear leveling' is specific to the USB thumb drive in question? my understanding is that the thumb drive presents itself to the computer as a radial hard-drive and translates back and forth as needed?

---

### Post by Glkanter on 2011-04-24
I went ahead and loaded Ubuntu 10.10 on a 4 GB usb flash drive (the only one I own).

After a warning, and a 'restart', it went fine. Slowly, for sure.

Actually running from the flash was a little slower than I'm accustomed to, but I was testing on a lesser machine.

So, I'll try my give-away project on a couple of 8 GB drives, and monitor the situation. I'm just not sure what the down side is, if any, for a novice PC/internet user. Even if the flash drive fails.

Those inexpensive hard drives at Newegg are 'recertified'.

Thanks for all the responses. I learned something from each of them.

---

### Post by 3rdalbum on 2011-04-24
I ran my server off an 8GB flash drive; a Corsair Voyager (one of the better known flash drives, basically). It turned into junk after about 6-8 months with big filesystem damage, and it got so bad that you can't even format the drive anymore.

I reckon you'll be replacing those flash drives with HDDs before long. My server's been running on a laptop HDD 24/7 for about 18 months, serving files off a desktop HDD that's been in use since 2007.

---

### Post by LewRockwellFAN on 2011-04-24
For what it is worth, my own limited experience with used hard drives is 100% good. Could be because the used ones were older drives. I've had several drives fail on me but those were ALL drives I bought new. I haven't seen any stats but I have a very strong impression that as hard drives get more capacious and the magnetic domains get smaller, and the spin speeds get higher, durability has gone way down. I don't remember ever having a drive less than 500 gB fail. Could just be the pattern of usage. We tend to use newer bigger drives in applications that put more demand on them maybe. I could just as well characterize my experience as being I never had a SMALLER drive fail while I've had several larger drives fail. So maybe it is just that all the used drives I bought or scrounged were small, under 50 gB. I even have a working (at least when I last connected it) 10 mB mfm hard drive. Yes, that is mB with an M.

---

### Post by Glkanter on 2011-04-24
[https://www.facebook.com/photo.php?pid=1720459&l=9e4f902732&id=1455816639](https://www.facebook.com/photo.php?pid=1720459&l=9e4f902732&id=1455816639)

Oh, I know all about 10 MB Hard drives. They hold 3 MP3s. Maybe.

And most of us didn't have them at work. Because that IBM 8088 with 256K RAM, mono monitor and uni-directional dot matrix printer set the company back about $6,000. "You'll get a second floppy drive, and like it!!"

As for these flash drives failing, well, the user community doesn't even use computers today. These folks are the opposite of high capacity, high volume users. Still, I'll buy one of those Newegg.com drives and give it a spin.

Thanks!!!

---

### Post by tordeu on 2011-04-24
@Glkanter:
Those recertified drives should still work ok. The cheapest new drive on NewEgg is $35, so depending the price you want to pay this might be an option. But as already mentioned, those recertified drives aren't necessarily more prone to fail. Drives can get pretty old and the available recertified one for $18 is a 160 GB drive, so it is pretty old, but not ancient.
I still have some 160GB drives which work great and have been for I don't know how many years now. And they have been used pretty heavily during the first years. 

> **earthpigg said:**
> the 'wear leveling' is specific to the USB thumb drive in question? my understanding is that the thumb drive presents itself to the computer as a radial hard-drive and translates back and forth as needed?

Well, it does present it self as a hard drive. But on a hard disk, when you have data saved in a specific (e.g. a small file) and it needs to be changed/updated, then the data is in general written to the exact same location.
On the flash drive, however, because the blocks can only take so many erases, wear leveling is used. If you change data, the updated data is not written to the same block. Because if you would do it like that and you update the file which is saved in that block very often, the limited number of cycles are over pretty soon. 
This wear leveling effectively changes which address translates to which physical block of the flash memory. So, after an update, the seemingly same "block" of the file system is in reality a different block on the flash chip. But this is done transparently "inside" the flash drive. The system does not notice that at all.

It's just like a storage space with a manager where all your stuff is put in cardboard boxes. You can go to the storage manager and check out your photos and maybe add new ones of throw some away and then check your updated photo collection back in by giving it to the storage manager.
The storage manager, however, will not necessarily put the photos in the same box every time. This is because over time, a cardboard box will break and be unsuable if it is used too much. Therefore, when you check your photos back in, he will use on of the newest looking boxes. This way all cardboard boxes will "wear out" pretty much at the same rate.
If you would always use the same box, then the box of things you often check out and back in will more quickly get broken than the box of things you rarely check out.
The problem is that the number of new boxes in the storage room, which could replace a broken box, are limited. So, if too many boxes break, you have a real problem.
That's why it is important to try to avoid that boxes break as long as possible.

---

### Post by earthpigg on 2011-04-24
thanks, tordeu.

---

### Post by tordeu on 2011-04-24
You're very welcome.

---

### Post by Glkanter on 2011-04-25
I've run into some of the 'real world' issues you guys mentioned.

I interrupted the download of the Ubuntu updates, and ruined the 4 GB flash drive. I had to use DBAN to make it usable again.

I picked up an 8 GB drive, and it seems to run Ubuntu a lot faster than the 4 GB.

I've got a PC from 2006, a Compaq Presario, that doesn't allow usb devices in the boot sequence. That will be the real show stopper for most of these, by definition, older machines, I'm afraid.

But the Compaq is my personal old PC, so I'd like to keep at it. Do bios upgrades ever include enhanced boot sequences? I've never done a bios update. Am I wishing for things that don't exist?

Thanks!

---

### Post by tordeu on 2011-04-25
The performance if usb flash drives varies greatly. Most really cheap only offer very low performance with sequential reading speed often below 10MB/s and writing speed most certainly way below 10MB/s. There are additional reasons for the low performance, but these numbers alone explain a lot. If you spend some extra bucks, flash drives should easily reach 20MB/s for sequential read and well over 10MB/s for sequential write.
Especially when the numbers are that low, a few MB/s extra can greatly enhance the experience.

As for the possibility of booting from a usb device with the help of a BIOS update, I can't speak from own experience. I think it greatly depends on the age of the mainboard and on the brand. But I would not have much hope of getting this feature via a BIOS update if it isn't already there in the beginning or shortly after.
After all, they would really like you to buy a newer product which offers this feature. But maybe someone has had the experience of getting such a feature with an update. But it most certainly would only be the case for some products.

---

### Post by oldfred on 2011-04-25
Several have posted that this works, I think one or two did have problems. Not used plop myself. It boots some other way CD or floppy then uses USB. 

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by Glkanter on 2011-04-25
I just *had* to kick this around yesterday, and my only choices at WalMart were a Sandisk and a PNY. Thinking it would be better, I paid the extra couple of $ for the Sandisk.

How do I determine the throughput speed, either before or after buying a flash drive?

I also figured this idea could be a good emergency backup for a user. Instead of being dead in the water, if they can boot from USB, they're on the internet.

And for those people who prefer to keep their PC running, rather than shutting down each night (I am one of those people), the 'extra wear from booting' issue isn't a great concern.

I'll look at that link very soon oldfred, thanks.

Otherwise, I just started reading Ubuntu For Non-Geeks, so hopefully I'll have fewer questions.

Thanks, guys!! You're the best!

---

### Post by tordeu on 2011-04-25
Booting itself is not the problem when it comes to usb flash drives, because reading data does not wear the blocks out. Writing is more of a problem. But you will only be able to if this really is an issue from long term experience.

When looking for flash drives, you could try to google for reviews or look for reviews from customers on amazon or something like that. 
To measure the speed afterwards, you can choose from a lot of ways. 

A very easy way is to just copy a large file from a hard disk to the flash drive and then copy it back to a hard disk. The "File Operations" window which will open why you copy the file, will eventually display the speed.

Another possibility would be to do pretty much the same thing in command line:
```
time cp <source> <destination>
```will copy a file from source to destination and the time command will then show you how long it took (time outputs 3 times. You would be interested in the "real" time). 

And of course there are probably a lot of benchmark scripts or programs out there. Just one I found (but have not used yet):

[http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.htm](http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.htm)

---

### Post by Glkanter on 2011-04-25
Sure, I read a lot of stuff about these drives. There was an informal speed 'standard' based on cd 'X' measurements, you know, like '32X'.

But now there is a 'standard' referred to as 'class'. The higher the number, the faster the throughput, and the number correlates to the throughput somehow. I saw the 'class' number on 2 drives from 1 website so far.

And I will add your speed test link to oldfred's link on my list of  links I need to get to very soon.

Absent any other information with which to make an evaluation, would you agree Sandisk is a reputable, quality manufacturer? In comparison, say, to a store brand usb stick?

Thanks.

---

### Post by tordeu on 2011-04-25
I have not had any problems with SanDisk products, yet, so from my experience I would recommend there products (I have some sd cards which are are a lot faster than the cheapest ones, while still being pretty cheap themselves; I am very happy with them). 

Same as with Transcend, from which my latest flash drive is. And Verbatim. Thinking of it, I did not have any problems with usb flash drive as far as I can remember. Even when I by very cheap ones (although they are pretty slow).

But you can buy slow drives from any one of these. They all offer several lines. One of my drives is a Transcend JetFlash 600. It's surely not the fastest one you will be able to find, but it certainly is a lot faster then very cheap ones and I am very happy with it. But this is just one example. There are numerous good ones out there.

I don't think there are a lot of flash memory manufacturers, so a store brand might have more or less the same quality (or even be manufactured by companies like SanDisk; but I am speculating here). I have no experience with store brands, but they probably try to be very cheap and that is a problem when it comes to performance.

When it comes to the speed ratings ("...X" or "Class ..."), I am always a bit sceptical, because sometimes these numbers are a little higher than what the product can deliver in real life. But as a general indicator of the speed these numbers should work. Just check some reviews. Sometimes people already did some speed tests, so you know what you're getting into. This is probably the safest way.

---

### Post by wilee-nilee on 2011-04-25
> **Glkanter said:**
> Sure, I read a lot of stuff about these drives. There was an informal speed 'standard' based on cd 'X' measurements, you know, like '32X'.

But now there is a 'standard' referred to as 'class'. The higher the number, the faster the throughput, and the number correlates to the throughput somehow. I saw the 'class' number on 2 drives from 1 website so far.

And I will add your speed test link to oldfred's link on my list of  links I need to get to very soon.

Absent any other information with which to make an evaluation, would you agree Sandisk is a reputable, quality manufacturer? In comparison, say, to a store brand usb stick?

Thanks.

Sandisks have been a problem at times for people, it has a built in firmware that can only be removed with a MS computer. This is anecdotal evidence but I would look in this area for more info.

Personally I had no problems with a sandisk 4 gig thumb after reformatting it enough times. But I did give it to a friend that I installed W7 for as the thumb was loaded with the W7 install media, I didn't want to have to mess with it.

---

