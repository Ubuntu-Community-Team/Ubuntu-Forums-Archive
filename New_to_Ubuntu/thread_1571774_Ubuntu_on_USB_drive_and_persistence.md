---
title: "Ubuntu on USB drive and persistence"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by rforte62 on 2010-09-10
Hello Everybody,

I've just joined this forum having started to experiment with Ubuntu installed on a USB drive. I'm a "Windows refugee" fed up with Windows shortcomings and I am evaluating Ubuntu before installing it onto the hard drive. So far I am very impressed. Everything works first time, no fuss and no problems. The only thing I got wrong was not selecting a persistence option during the creation of the "Ubuntu on a stick" USB drive. I would like to keep using Ubuntu from the USB drive for a few more days before tackling the installation on the hard drive, but without the persistence option, Ubuntu now "forgets" every change I make every time I log out. So, the dumb question is: Is there a way to modify the USB copy of Ubuntu and make it persistent?

Many thanks in advance for any assistance.

Best regards

Ren

---

### Post by garvinrick4 on 2010-09-10
> **rforte62 said:**
> Hello Everybody,

I've just joined this forum having started to experiment with Ubuntu installed on a USB drive. I'm a "Windows refugee" fed up with Windows shortcomings and I am evaluating Ubuntu before installing it onto the hard drive. So far I am very impressed. Everything works first time, no fuss and no problems. The only thing I got wrong was not selecting a persistence option during the creation of the "Ubuntu on a stick" USB drive. I would like to keep using Ubuntu from the USB drive for a few more days before tackling the installation on the hard drive, but without the persistence option, Ubuntu now "forgets" every change I make every time I log out. So, the dumb question is: Is there a way to modify the USB copy of Ubuntu and make it persistent?

Many thanks in advance for any assistance.

Best regards

Ren I do believe you have to make your USB flash drive with persistence when it is produced. You can make them with up to 4 gig of total persistence using the
fat32 formatted drives now. You can have a nice little system at 4 gig. I think we all use
them as Live CD's and keep them around. Download iso file to desktop of Ubuntu and BURN at slowest speed possible to a CD. Boot off of CD and use startup disk creator
to make your flash drive. You can format it while in the program. Take maybe 45 minutes for whole project. Keep the CD for future Live CD. Just choose Try Ubuntu instead of install when it asks. Link below.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by beew on 2010-09-10
**garvinrick4**

> I do believe you have to make your USB flash drive with persistence when  it is produced. You can make them with up to 4 gig of total persistence  using the
fat32 formatted drives now. You can have a nice little system at 4 gig. I think we all use
them as Live CD's and keep them around. Download iso file to desktop of  Ubuntu and BURN at slowest speed possible to a CD. Boot off of CD and  use startup disk creator
to make your flash drive. You can format it while in the program. Take  maybe 45 minutes for whole project. Keep the CD for future Live CD. Just  choose Try Ubuntu instead of install when it asks. Link below.Huh?? He is using windows there is a much easier way to do it. [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)  Takes 10 minutes tops if he uses a 4 g usb pendrive and creates 3g of persistence. I bet that is how he made the one he is using now :)  I wish there is something like this for Linux. 
[B]
rforte62[/B]

Just a warning, you can update end user applications in a USB with persistence but don't try to update any system features like kernel, drivers, Xorg and the like, it will break your system as live usb doesn't support that kind of update.

---

### Post by mr_luksom on 2010-09-10
Would recommend pendrivelinux.com, much easier than burning the iso to a cd.

Also, if you do choose to create a live cd by burning the iso, make sure you are burning the iso contents to the cd, and not the iso file! most burning software has an option for this.

---

### Post by garvinrick4 on 2010-09-10
It is nice to have so many options. I have had flash drives just go dead on me and it is nice to have Live CD around as back-up to USB flash. Again options are nice to have are they not. I am staring at a dead unmountable, unreadable, Centon 4 gig that I was goofing
around with remix on last night. On sale at Fry's for $7.99 the grey one. Grey ones seem to stink. Black or Red Centons boot everytime and seem to last. Hope I did not jinx myself.
Any which way I did relize that Netbook iso has option of using desktop or netbook at login and if you fix one up the other one gets the packages also. I used auto login so never really noticed when goofing around with remix. Like a huge phone with benefits, if you haven't tried it do kind of nice to use for cruising around net. Used 475 meg of RAM at full gallop. Have to keep playing around with has a little different way of its own.

---

### Post by C.S.Cameron on 2010-09-10
You can add a persistent file or partition, (casper-rw), to an existing CD image install but it is easier to just make a new persistent install using startup disk creator from the Live CD.

Create a 1.5 GB ext3 partition using gparted label it "casper-rw". (ext2 and ext4 also work).
Run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

---

