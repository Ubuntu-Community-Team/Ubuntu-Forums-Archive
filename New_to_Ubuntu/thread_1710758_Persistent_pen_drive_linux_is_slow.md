---
title: "Persistent pen drive linux is slow"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by GoldenAxe on 2011-03-20
I've installed Maverick Meerkat on a USB stick. It works fine - but is really, really slow. Updates take an hour at least to install.

Is running Ubuntu from a USB normally so slow? Or should I invest in a faster USB stick? 

I'm using a SanDisk Cruzer 16GB.

My install was done through the tool on PenDriveLinux.com. 

Any tips on how to boot faster from a USB?

---

### Post by kn0w-b1nary on 2011-03-20
Use a lighter Desktop Enviroment, like LXDE. USB 2.0 is much slower than SATA for example. You could try an SD card or USB 3.0, but USB 3.0 is pricey. So yes, USB linux is slower. If changing your DE isn't enough, then there are other distros like puppy that might work.

---

### Post by 5149.5 on 2011-03-20
I had the same results using a kingston USB thumbrive.

---

### Post by GoldenAxe on 2011-03-20
Hmm, thanks. Good advice!

I'm trying Ubuntu Netbook to see if that makes a difference.

---

### Post by kn0w-b1nary on 2011-03-20
I like puppy linux and tinycore for running Linux on USB. Fast enough for me.

---

### Post by GoldenAxe on 2011-03-20
Will USB 3.0 offer similar boot up speeds as SSDs?

---

### Post by kn0w-b1nary on 2011-03-20
Not that fast, but a lot faster than USB 2.0. Note that USB 3.0 does not work on USB 2.0 ports, so you might need to buy a PC card if you decided to go the USB 3.0 way.

---

### Post by 5149.5 on 2011-03-20
> **GoldenAxe said:**
> Hmm, thanks. Good advice!

I'm trying Ubuntu Netbook to see if that makes a difference.

That won't be any faster than the normal desktop version. I think the main difference is just the desktop limitations of netbook remix.

---

### Post by GoldenAxe on 2011-03-20
Tinycore is a new one on me. Will take a look. 

And I'm running Netbook Ubuntu right now. Doesn't seem to be much different. 

Would it help if I bought a more up-to-date USB stick? Do the speeds vary much?

---

### Post by GoldenAxe on 2011-03-20
Or maybe an SSD USB stick. I didn't know they existed.

[http://cgi.ebay.co.uk/Kingspec-16GB-USB-SSD-MLC-Flash-Hard-Disk-Drive-Laptop_W0QQitemZ220747777405QQcmdZViewItem?rvr_id=219414045660&rvr_id=219414045660&cguid=d470933112e0a47a2f9642f6ffd10543](http://cgi.ebay.co.uk/Kingspec-16GB-USB-SSD-MLC-Flash-Hard-Disk-Drive-Laptop_W0QQitemZ220747777405QQcmdZViewItem?rvr_id=219414045660&rvr_id=219414045660&cguid=d470933112e0a47a2f9642f6ffd10543)

Are they going to be useful for linux pen drive action?

---

### Post by kn0w-b1nary on 2011-03-20
I don't think so, because of transfer speeds. SD cards, can be faster if your computer can boot from them. And they aren't that expensive.

---

### Post by Hedgehog1 on 2011-03-20
A faster USB stick does help a lot.  My first USB install was also on a SanDisk Cruzer 16GB.  I died of boredom waiting for it.

The RageXTs are fast USBs; but I have found a fast enough & cheaper alternative: Kingston DataTraveller 100 G2 16 Gig

I run Ubuntu 10.10 on this and have freed up my more expensive RageXT for bulk data transfers.

***The Hedge***

:KS 

p.s. I actually install Ubuntu on the USB stick from the CD.  It is a real install rather than a 'pen-drive with persistence'; it *seems* to run faster truly installed, but I cannot prove that with hard figures.  But the faster USB is a must.

---

### Post by Hedgehog1 on 2011-03-20
As a side note, if your USB has one FAT/NTFS partition, you can still use of for transfers to/from Windows PCs.

Also, having a DOS/NTFS partition on the USB keep windows from offering to format for you when you plug it into a PC running windows.

Here is how mine looks in gparted:

[IMG]http://img197.imageshack.us/img197/6631/gparteduaos.png[/IMG]

***The Hedge***

:KS

---

### Post by MooPi on 2011-03-20
Your install will be limited by the speed of read and write to the flash drive. I have utility usb drives that function fine but the write speed is horrible.  Otherwise they work great.

---

### Post by C.S.Cameron on 2011-03-20
I understand running Ubuntu from a flash drive but running in RAM is faster than SSD or SATA.

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by Hedgehog1 on 2011-03-20
I was just booting a laptop off of **Ubuntu-On-A-Stick!** since I removed it's bad hard drive.  Load time for Ubuntu off the USB was about the same as load time for Vista off the Hard drive.  Running, the only noticeable delay was loading an application.

I was playing music in Bashee and it was working good.

It's not perfect, but it is workable.

***The Hedge***

:KS

---

### Post by migrate from windows on 2011-03-21
Ubuntu is excellent with HDD...but for pendrive  +1 for Puppy linux.

---

### Post by CVGH on 2011-03-21
I just started running 10.10 off a PNY 16GB and the speed seems fine.
I think I'm going to boot the CD and shrink casper-rw down a bit and make a FAT32
partition at the end to swap files around.
The only thing I don't like about running Ubuntu like this is that every time I boot, a window pops up asking if I want to try or install Ubuntu. My system was made using the 
usb-creator-gtk after booting from the CD.
Is there a fix for this?

---

### Post by beew on 2011-03-21
If you want speed (and full functionality) you should install into an external hard drive ( a full install using ext3 or ext4, not FAT and casper -rw) Live usb with persistence is slow and also tends to freeze if you do anything intensive (like updating and watching youtube at the same time)

---

### Post by 5149.5 on 2011-03-21
> **beew said:**
> If you want speed (and full functionality) you should install into an external hard drive ( a full install using ext3 or ext4, not FAT and casper -rw) Live usb with persistence is slow and also tends to freeze if you do anything intensive (like updating and watching youtube at the same time)

I agree. I ran from a pen drive for a few days and it was fine for a test drive but I got tired of the lagging performance and installed to hard drive. There was quite a difference.

---

### Post by C.S.Cameron on 2011-03-21
> **CVGH said:**
> I just started running 10.10 off a PNY 16GB and the speed seems fine.
I think I'm going to boot the CD and shrink casper-rw down a bit and make a FAT32
partition at the end to swap files around.
The only thing I don't like about running Ubuntu like this is that every time I boot, a window pops up asking if I want to try or install Ubuntu. My system was made using the 
usb-creator-gtk after booting from the CD.
Is there a fix for this?

Windows can only see the first partition on a flash drive, you can expand this partition.

When booting this flash drive you will find data that is stored on this partition under Filesystem/Cdrom.

An Unetbootin install does not have as bad an opening screen, but is not persistent out of the box. You can make a casper-rw partition or copy a casper-rw file from a usb-creator install.
Edit the syslinux.cfg file as follows:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- [B]persistent
[/B]

---

### Post by Hedgehog1 on 2011-03-22
> **CVGH said:**
> I just started running 10.10 off a PNY 16GB and the speed seems fine.
I think I'm going to boot the CD and shrink casper-rw down a bit and make a FAT32
partition at the end to swap files around.
The only thing I don't like about running Ubuntu like this is that every time I boot, a window pops up asking if I want to try or install Ubuntu. My system was made using the 
usb-creator-gtk after booting from the CD.
Is there a fix for this?

To stop the 'pop up', you need to do a real install of Ubuntu onto the USB stick.

***The Hedge***

:KS

---

### Post by I2k4 on 2011-03-22
I've been experimenting since January with various versions "Live" on a 2GB (1GB Persistence) and a 4GB (2GB Persistence) USB 2.0.  (I keep DropBox and all data files on the HDD, and access it through the OS running from USB.)

I've pretty much settled on Lubuntu 10.10 for speed, light resource use and reliability (though I'm glad I started with the full-featured Ubuntu Desktop to get a bit of a "feel" for Linux.)

I found the Netbook Remix to be a complete dog for speed, much slower on USB than plain old Desktop (and don't like the screen hogging GUI on a 9" netty).  I don't recommend general system updates, or installing more than one or two packages at a time, on Live USB - the system just starts to trip over itself.

I'm unsure about how much drive space should best be allocated to the OS versus the "Persistence" or Casper file - up to 8GB or so I would go 50/50 split right now.  You don't indicate exactly how you've allocated your 16GB.  I have to say, I've been toying with whether a "faster" USB 2.0 flash drive would be a good idea - I've seen them advertised but don't know how much better they are.

One final tip: if you know one of your applications writes to the USB, see about changing that cache or whatever.  I've notably improved FireFox by using about:config to limit it to RAM cache, and set GIMP swap and cache to the HDD instead of the USB, via its preferences.  The USB is a real drag if it's constantly being read/written.

---

### Post by 86themachine on 2011-09-08
Im running 10.10 on a Kingston DT Ultimate GT 3.0 16gb drive with full encryption and it rocks. Buy 2 identical drives and do regular backups especially if your about to make major changes. I tried an Adata USB 3.0 16gb drive and it's slow, I mean pull your hair out slow. I dd the Kingston over to the Adata for a backup. I can dd (clone) the drives back and fourth but the Adata sucks for actual use other than backup. 

Possibilities: There are several possible explanations for this.
Ubuntu was not originally written to the Adata drive.
Adata drive is a cheap knock-off and not truly USB 3.0 as advertised.

Conclusion: Spend the money on a top notch high-speed drive. Keep backups I have 2 plus my original. Saved my butt more than once. I no longer use HD for my system I just plug this beauty into any computer I want and away I go. 
Get the same drives so they format out the same this will make it easier for you when you clone. Otherwise you have to mod the partition. The Kingston formats out to 16gb NICE. 

Good Luck and Happy Ubunting

---

