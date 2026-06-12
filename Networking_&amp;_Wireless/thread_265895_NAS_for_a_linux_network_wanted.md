---
title: "NAS for a linux network wanted"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by aiv on 2006-09-26
Hello, i'm searching for a chip NAS that can be used without Samba, just mount like a linux partition.

---

### Post by Iowan on 2006-09-26
both [FreeNAS]("http://www.freenas.org/") and [NASLite]("http://www.serverelements.com/naslite.php") have NFS versions available.

---

### Post by fernando_lopes_jr on 2006-09-26
I'am building a home NAS from a old pc for my home network to make backups and store data. I haven't made up my mind on witch software I'am going to use I was thinking of using ubuntu server but mayby I'll use FreeNas.Has anyone used it before? How good is it? With you advise samething else?
I read there web page and It says they format the disk's with UFS file system I've never heard of this system before does ubuntu recognize this system if I take out the drive and pop it in another system.
I would really like same advice on this because I want to make a nice backup system that is realiable.

---

### Post by mips on 2006-09-27
I would go the FreeNAS route.

I would not use the USF file system as you won't be able to acces it from amny other OS's. FreeNAS also supports Ext2/Ext3 which I would use.

---

### Post by Zeek00 on 2006-10-30
So whats the advantage of using FreeNAS verses the Ubuntu Server?

---

### Post by mips on 2006-10-31
> **Zeek00 said:**
> So whats the advantage of using FreeNAS verses the Ubuntu Server?
The first thing I can think of is it's small size (32MB) and based on Freebsd/m0n0wall.

NASLite is even smaller.

---

### Post by Jussi Kukkonen on 2006-11-01
> **aiv said:**
> Hello, i'm searching for a chip NAS that can be used without Samba, just mount like a linux partition.
You mean an appliance, something that you buy, plug in the network and just let it serve files? Sorry, but there's no such thing -- I've been searching for it myself. It's really strange since many of the boxes actually run linux, they just don't support NFS...

There are some interesting DIY possibilities though:
[http://linkstationwiki.net/index.php?title=Main_Page](http://linkstationwiki.net/index.php?title=Main_Page)
[http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)
[http://kurobox.com/](http://kurobox.com/)

EDIT: prodded by seeing this thread, I decided to search again. It seems there are NFS-NAS boxes (at least one):
[http://www.theinquirer.net/default.aspx?article=23586](http://www.theinquirer.net/default.aspx?article=23586)

---

### Post by AzureCerulean on 2007-07-28
> **Jussi Kukkonen said:**
> You mean an appliance, something that you buy, plug in the network and just let it serve files? Sorry, but there's no such thing -- I've been searching for it myself. It's really strange since many of the boxes actually run linux, they just don't support NFS...
]

There is in fact such a device.
avalible from Clarinet Systems, Inc

USBShare - EB-214A

[http://www.clarinetsys.com/en/product-eb214a.htm](http://www.clarinetsys.com/en/product-eb214a.htm)

Yes, it is USB based but it does support SMB and EXT2 and EXT3 filesystems.

It has a web interface and works quiet well, one drawback is that it requires Internet Explorer to administrate  but once setup you can access the shares from and SMB capable system.

---

### Post by netztier on 2007-07-28
> **mips said:**
> The first thing I can think of is it's small size (32MB) and based on Freebsd/m0n0wall.


...and HORRIBLY slow! (at least in my case)

My current "NAS" is a P-III 500 with 512MBytes RAM and an 80GByte system disk; two 120GByte Data drives (not mirrored or striped, just simple disks). It has an intel gigabit PCI card. Occasionally, I also hook up an external SCSI Box with 6x36Gig ultra2 wide disks (LVD, 40MB/sec) to a Adaptec 2100S raid controller with 128MBytes of cache and a RAID10 setup (a stripe set of 3 RAID1-Pairs).

With Ubuntu server 6.06, I get 30MBytes/s (sustained) **NFS** reads from that array and can write to it at 5-8MBytes/s. When reads come from the controller's cache, the even go beyond 60MBytes/sec. Why writes are so slow is still a mistery to me - I'm not quite sure if my SCSI bus is in perfect electronical shape (cable length, termination)  - will have to debug.

**Samba** (mounted via /etc/fstab with CIFS) gives me 14-15MBytes/s reads and 15-16MBytes/s writes, from/to the same array.

To test FreeNAS, I unhooked all the Linux drives and put an old 40Gig IDE in for FreeNAS to boot from. It boots very fast and even recognised the Adaptec Controller and found the single 108Gig "drive". 

But performance was miserable - NFS reads at 7-8MBytes/s, writes a bit lower, and Samba  crawled along at ~3MBytes/s - it felt like the old Samba 2.x days.

I think that FreeNAS has potential; the GUI is good, it boots stunningly fast and is very straightforward to set up and configure. But like almost all NAS boxes I have been looking at these last few weeks, performance is just not good enough. Most of them lack NFS anyway.

For example: found a Thecus N4100 on ricardo.ch (a local simile to ebay)  and went to search reviews for it - Gigabit Ethernet and internal 1-5GBit SATA disks make it very promising, but then Samba goes crawling around at barely beyond 10MBytes/s. How disappointing! And even worse when running RAID-5!

I'd understand if these boxes were built as general-purpose jack-of-all-trades tools - but they're meant to be NAS's, so they can be optimised for one thing: I/O !

I feel intrigued to try a **Intel-based Mac Mini** atop a stack of LaCie disks (those that have the same form factor as the Mac Mini) as my next NAS - running Ubuntu, of course. It won't come cheap, but I'm almost ready to bet that it'll outperform most of the "dedicated" SOHO-NAS boxes that are on the market - all while still remaining a general-purpose server, of course.


best regards

Marc

---

