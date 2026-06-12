---
title: "Help with buying an external hard drive"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-06-17
I want to buy an external hard drive (500MB or 1TB) and was wondering if you have any suggestions on which I should get?

My laptop and desktop are both running ubuntu so I need something that works with 8.10 and 9.04. Also what about FAT32 vs NTFS? Does the difference matter?

Thank you!

---

### Post by jenkinbr on 2009-06-17
Most external hard drives that interface via USB are recognised as USB mass storage class devices, meaning nothing special is needed. It should work strait away if this is the case.

If you are going to be using the drive exclusively with ubuntu, I'd recommend formating it to a Linux file system (i.e. ext3), but fat32 or NTFS should be fine.

---

### Post by ZackM on 2009-06-17
They're selling the MyBook's for lik $120 or something at Best Buy. The TB that is. Also, NTFS will allow you to have a bigger allocation, thus reading 1TB instead of scaling it down, like FAT32 would, to around 400 or so Gbs.

---

### Post by sylvainrb on 2009-06-18
Oh ok. I would keep it formatted as FAT32 or NTFS since I might use it with a Windows machine in the future. Can I format it using gparted or do I need another program?

@ZackM: When FAT32 scales it down to 400GB or so, what happens to the rest of the memory? Does it expand as you need it or just can't use it?

---

### Post by jenkinbr on 2009-06-18
> **sylvainrb said:**
> Oh ok. I would keep it formatted as FAT32 or NTFS since I might use it with a Windows machine in the future. Can I format it using gparted or do I need another program?

@ZackM: When FAT32 scales it down to 400GB or so, what happens to the rest of the memory? Does it expand as you need it or just can't use it?
If you use fat32 and it only uses 400 GB or so, it will just leave the rest of the space unallocated.

I would probably leave the partioning intact when it comes, though (I tend to delete the preinstalled software on it though - but back that up first!) If you do need to format, gparted should work, but I'd use a windows box to be safe.

---

### Post by Therion on 2009-06-18
Holy cow... Western Digital Element 1TB, external 3.5" HDD **[COLOR="Red"]$99[/COLOR]** on NewEgg... FREE SHIPPING!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321)

---

### Post by jenkinbr on 2009-06-18
> **Therion said:**
> Holy cow... Western Digital Element 1TB, external 3.5" HDD **[COLOR="Red"]$99[/COLOR]** on NewEgg... FREE SHIPPING!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321)
/me drools

---

### Post by AoSteve on 2009-06-18
Good call Therion!   I was about to post that!   I also have to say, the WD My Book drives will take one HECK of a beating.  I accidentally dropped mine (250GB version) off of my friend 12' high deck.  The casing broke but the drive has been running for six months since it happened!    I finally broke it down and attached it into my 3.5" bay in this system when the case became.. well too sharp on that crack to handle.

---

### Post by Therion on 2009-06-18
> **jenkinbr said:**
> /me drools
must... Stop... Clicking on... Newegg... Dot com...

---

### Post by AoSteve on 2009-06-18
No kidding!  I'm addicted..   I build a "wish list" machine once a week LOL!   I built a Skulltrail this week for $2000 in my wish list! :)

---

### Post by Therion on 2009-06-18
> **AoSteve said:**
> No kidding!  I'm addicted..   I build a "wish list" machine once a week LOL!
Totally unrelated but... Dude... Your system specs are scarily similar to my own:

E8400@3.6Ghz vs my E8400
4GB Hyper X 1066mhz vs my 4GB of Corsair 1066Mhz
RaptorX 150gb vs my Raptor 150gb
GF 8800GTS (G92) vs my GF 8800GTS
320GB extra storage vs my... Well I *have* a WD Blue Cav' 320GB, it's just sitting on the shelf in the pile right now with... (looks over) oh, it's got an install of Jaunty 64-bit on it currently (while I tame the wild Koala).  Currently installed slave drive is WD 160GB if memory serves.



/End of Thread Jack...

---

### Post by joshedmonds on 2009-06-18
> **jenkinbr said:**
> I'd recommend formating it to a Linux file system

If you are going to use this as a general backup drive, I would definitely format so you have some separate partitions. The benefits include faster file manager load times (due to less folders to load), separation of important data from other data, differing permissions, the ability to hide data from windows users (not a foolproof method, but better than nothing).

I have a 750GB external hard drive, and partitioned it:
p1 10GB ext4 - /
p2 10GB ext4 - /home
p3 2GB swap
p5 extended
  p6 200GB fat32 - windows accessible
  p7 200GB fat32 - windows accessible
  p8 200GB fat32 - windows accessible
  p9 remainder~100GB ext4 - unable to be seen in windows without third party software

This way you can use your drive as a portable Ubuntu install (just copy over your desktop install every so often and install grub the first time), keep your data separate and hide some things from windows.

---

### Post by ZackM on 2009-06-18
> **sylvainrb said:**
> Oh ok. I would keep it formatted as FAT32 or NTFS since I might use it with a Windows machine in the future. Can I format it using gparted or do I need another program?

@ZackM: When FAT32 scales it down to 400GB or so, what happens to the rest of the memory? Does it expand as you need it or just can't use it?

Like Jenkinbr said. It'll show you 400gigs available, and the rest would be unallocated. However, you wouldn't be able to see, or use, that space. I would just keep it with ntfs myself, especially if you are going to be using it for Windows as well.

---

### Post by sylvainrb on 2009-06-18
> **joshedmonds said:**
> If you are going to use this as a general backup drive, I would definitely format so you have some separate partitions. The benefits include faster file manager load times (due to less folders to load), separation of important data from other data, differing permissions, the ability to hide data from windows users (not a foolproof method, but better than nothing).

I have a 750GB external hard drive, and partitioned it:
p1 10GB ext4 - /
p2 10GB ext4 - /home
p3 2GB swap
p5 extended
  p6 200GB fat32 - windows accessible
  p7 200GB fat32 - windows accessible
  p8 200GB fat32 - windows accessible
  p9 remainder~100GB ext4 - unable to be seen in windows without third party software

This way you can use your drive as a portable Ubuntu install (just copy over your desktop install every so often and install grub the first time), keep your data separate and hide some things from windows.

I will use it as a back up but I want to use it mainly to store media (movies, pictures, music) and other files that I can access when I need to. Not on a regular basis but if I need to I can just get them without too much trouble. Another person pointed that I should reformat using a Windows machine but what program can I do that with or is it included with the Windows utilities? And then I can build the partitions using gparted?

Thanks for the help (and the link) everybody! And I'll do some more research on partitioning and such...

---

### Post by joshedmonds on 2009-06-18
The formatting can be done within Ubuntu. On the liveCD/USB you will find System>Administration>Partition Editor. On an installed system you will have to install the gparted package, then find it in the same place.

I personally prefer to use the liveCD/USB as you are less likely to freeze your system (in my experience, YMMV) however you do have to either disconnect your internal drive or BE VERY CAREFUL that you don't affect your internal drive.

GParted may not be able to create NTFS filesystems, however it will be able to delete them and create new filesystems of FAT, EXT3/4 etc. NTFS would not be a recommended for a shared partition anyway.

My partitions only reflect my needs, you might find 3 separate media partitions unsuitable, and may not want to have the backup Linux install (but it can be very handy).

Remember that you can only have 4 primary partitions, including the extended partition - you can then have up to 15? logical partitions within the extended partition. I believe in GParted you don't need to explicitly create the extended partition, just create a logical partition and it will be done for you.

EDIT: I've only ever had problems with freezing with the 750GB USB drive - this may be because of it's size or other reasons, but the liveCD was the best for partitioning safely for me.

---

### Post by TeoBigusGeekus on 2009-06-18
I wouldn't buy an external hd now.
If you can wait, in half a year usb 3.0 will be out and everything about hardware connections (inside or outside the pc) will be changed.

---

### Post by joshedmonds on 2009-06-18
> **TeoBigusGeekus said:**
> I wouldn't buy an external hd now.
If you can wait, in half a year usb 3.0 will be out and everything about hardware connections (inside or outside the pc) will be changed.

I guess that is true, and you may get better mileage from buying the drive now (if you need it now) and buying a SATA HDD -> USB2.0 enclosure, rather than a brand name product (e.g. MyBook etc), then you can just upgrade the enclosure at any time.

The other consideration is that even the brand name stuff is now only $100 or so, and USB3.0 will require a hardware upgrade to your PC to take advantage of it.

Personal view - don't buy the brand name stuff anyway, buy a good standalone drive and a good enclosure, it will take up less space, you'll get more storage for your dollar and may even be more reliable (I've not heard great things about the quality of some of these cheap brand name products, especially with Seagate drives in them).

---

### Post by jenkinbr on 2009-06-18
USB 3.0???

Oh God why am I still stuck on 1.1!

---

### Post by TeoBigusGeekus on 2009-06-18
[http://news.cnet.com/8301-17938_105-9780794-1.html]("http://news.cnet.com/8301-17938_105-9780794-1.html")
[http://www.everythingusb.com/superspeed-usb.html]("http://www.everythingusb.com/superspeed-usb.html")
...and of course...
[http://www.neowin.net/news/main/09/06/11/linux-is-first-os-to-support-usb-30]("http://www.neowin.net/news/main/09/06/11/linux-is-first-os-to-support-usb-30")

---

### Post by jenkinbr on 2009-06-18
> **TeoBigusGeekus said:**
> [http://news.cnet.com/8301-17938_105-9780794-1.html]("http://news.cnet.com/8301-17938_105-9780794-1.html")
[http://www.everythingusb.com/superspeed-usb.html]("http://www.everythingusb.com/superspeed-usb.html")
...and of course...
[http://www.neowin.net/news/main/09/06/11/linux-is-first-os-to-support-usb-30]("http://www.neowin.net/news/main/09/06/11/linux-is-first-os-to-support-usb-30")
/me drools some more...

---

### Post by TeoBigusGeekus on 2009-06-18
> **jenkinbr said:**
> /me drools some more...
Me too!
I want to buy a new pc but I'll make do with what I have until usb 3.0 comes out.
Sata2 speed:3Gbits/sec
Usb 3.0 speed:5Gbits/sec
In a year, all pcs will be 1.5 times faster from today'a pcs just from the change of the connection type...
I won't even comment about usb 2.0 external hds' speed...

---

### Post by sylvainrb on 2009-06-19
Thanks for the different advice. All that is good to know. I also plan to build a computer (one that I will be proud of!) but I need more money, time and actual knowledge about hardware haha!

I'll check out the hard drives and enclosures. I don't really need it now but will in the future.

As for USB 3.0, it'll probably be for the computer I build. My laptop and desktop are too old.

Thanks again!

---

