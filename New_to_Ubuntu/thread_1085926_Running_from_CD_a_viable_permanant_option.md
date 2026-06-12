---
title: "Running from CD a viable permanant option?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Zieb on 2009-03-03
Okay, I used to run Ubuntu until last year (and had been doing so for a couple years).  I loved it, despite not being a very techy guy.  My wife was less fond of it.  Then there was some unpleasantness because I tried to set up both at once, and did something to the drivers in Windows a little after that as well).  Anyway, the long and short of it is that we won't be replacing our current computer anytime soon, my we don't have room for a junker, or budget for another new one, and I am NOT permitted to put Ubuntu on there again.  Divorcing my wife is also not an option (how many attractive women will watch Doctor Who every week I ask you).  

Thus, I'm wondering if a live CD would be a good solution for me?  I don't need a lot of junk, just VLC, Open Office, and Mozilla.  Can I do things in there and put them onto the harddrive (store documents, etc), and use things from the harddrive (movies, music, etc)?  Could it be an option for a guy who hates Windows who is in my situation?  Thanks.

---

### Post by whoop on 2009-03-03
Have you considered a multi-boot install?

---

### Post by st33med on 2009-03-03
You could create a Live USB.  Just boot the Live CD, System -> Administration -> Create a Live USB, mount the partition with ISO image, get the ISO image, and select it on the Live USB installation window...

(IN THEORY)

---

### Post by Het Irv on 2009-03-03
I really don't like the Live CD as a permanent option.  Since every time you boot the computer up, its just like starting over.  For you I would suggest looking to see if your computer will boot to USB, if it can, then you can try installing Ubuntu to an external drive, and that way if the Drive is not plugged in, the computer will boot to Windows, and if it is I will boot to Ubuntu.

I know that you said that you don't have the budget for a new computer and installing it on the current one isn't an option, but if the opportunity ever comes up, you could look into Wubi, or maybe buy one of the new netbooks.

---

### Post by Zieb on 2009-03-03
> **st33med said:**
> You could create a Live USB.  Just boot the Live CD, System -> Administration -> Create a Live USB, mount the partition with ISO image, get the ISO image, and select it on the Live USB installation window...

(IN THEORY)
Is there a tutorial of how to do this anywhere?  It sounds promising.

---

### Post by avtolle on 2009-03-03
Since the OP wants to have some additional apps not a part of the Live CD, he needs to do a persistent USB, IMHO. [http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive) contains a clear (well, to me) explanation of the process. Good luck.

---

### Post by blueridgedog on 2009-03-03
As others suggest, external disk via USB if you motherboard will boot off of USB.  You do not list a location, but I bet there is a LUG near you that can lend a hand if you want some backup.

---

### Post by starcannon on 2009-03-03
I'd probably do a swappable hard drive tray for a long term solution to your particular problem.
Something like [http://www.newegg.com/Product/Product.aspx?Item=N82E16817994020](http://www.newegg.com/Product/Product.aspx?Item=N82E16817994020)
That one is SATA, but I know they make IDE ones as well (i have an old IDE swappable hdd tray set here somewhere in a box from way back.)
The USB option is not a bad one either; though, instead of a usb stick, I'd recommend regular install to the usb drive; then just press the ESC key (may vary from bios to bios) during post, select the device you want to boot from from the list, choose the USB drive, and away you go.
Either of the 2 ways I've reccomended relieves the neccessity for grub and absolutely no disturbance to the Windows partitions.

Heres a bunch more of both IDE and SATA swappable hard drive trays: [http://www.tigerdirect.com/applications/category/category_slc.asp?CatId=285](http://www.tigerdirect.com/applications/category/category_slc.asp?CatId=285)
GL and have fun.

---

### Post by stchman on 2009-03-03
> **Zieb said:**
> Okay, I used to run Ubuntu until last year (and had been doing so for a couple years).  I loved it, despite not being a very techy guy.  My wife was less fond of it.  Then there was some unpleasantness because I tried to set up both at once, and did something to the drivers in Windows a little after that as well).  Anyway, the long and short of it is that we won't be replacing our current computer anytime soon, my we don't have room for a junker, or budget for another new one, and I am NOT permitted to put Ubuntu on there again.  Divorcing my wife is also not an option (how many attractive women will watch Doctor Who every week I ask you).  

Thus, I'm wondering if a live CD would be a good solution for me?  I don't need a lot of junk, just VLC, Open Office, and Mozilla.  Can I do things in there and put them onto the harddrive (store documents, etc), and use things from the harddrive (movies, music, etc)?  Could it be an option for a guy who hates Windows who is in my situation?  Thanks.

We see who wears the pants in the family.  I will be darned if my significant other tells me what I can and cannot install on my PC.  Have you considered getting yourself a laptop?  You can get a cheap Acer Aspire for around $400.  They take up almost no room.

Ubuntu installs don't touch the Windows install.

Yes, you can use the LiveCD as long as you can tolerate slow performance.

---

### Post by w1ll15 on 2009-03-03
I definitly would go with An external harddrive or a usb install ( at least 8gb !)
note>>>> this only works if your bios supports booting from a usb device!

I boot to my usb drive all the time in school..... just pop it in boot from usb and Bye Bye WinDoze

here is a link ... might help you
[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/]("http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/")

---

### Post by the.phantom on 2009-03-03
> I'd probably do a swappable hard drive tray for a long term solution to your particular problem.
Something like [http://www.newegg.com/Product/Produc...82E16817994020](http://www.newegg.com/Product/Produc...82E16817994020)

i would highly recommend that way ;-D

i did it to my xp system and worked great!

a friend of mine was in a similar position as you and he did it that way and he is still happly married ;-D

no fuss to change operating systems, ad can't blow either one !
and you can still use a usb flash to exchange data between the two

---

### Post by redseventyseven on 2009-03-03
Using a LiveCD on a permanent basis is probably not a good idea. For one thing, you'll end up knackering your CD drive.

A USB install is probably a better idea, though still, the durability of USB drives is not as high as hard disks. Be prepared to back up often.

Also, remind your dearly beloved that correlation doesn't equal causation (see the comment by "kimpatsu" in this thread - [http://coppersblog.blogspot.com/2009/02/753-of-statistics-are-nonsense.html?showComment=1233830820000#c4020763902929963978](http://coppersblog.blogspot.com/2009/02/753-of-statistics-are-nonsense.html?showComment=1233830820000#c4020763902929963978)). Windows went wrong because something in Windows went wrong. Not because of Ubuntu interfering.

---

### Post by w1ll15 on 2009-03-03
live cd's are too slow and are damaged too easily ... A pen drive can fit in your pocket ... take it to school ... work... 
1...2...3 ... no more windoze
this might help 

[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/]("http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/")

but i think you neeeed a cheap laptop so you can leave your girl with her precious  Windoze... and have peace...LOL;)

---

### Post by Zieb on 2009-03-03
Thanks guys.  This support is one of the many things I have missed with Windows.

I really like the flash drive solution as it'll let me use that on my work laptop too (which I am not allowed to install new operating systems on).

---

### Post by Zieb on 2009-03-04
My work computer was giving me headaches with the USB live (it won't boot from the USB at all even if I tell it to), so I put something from the pendrivelinux site on there called QEMUPDL.  It's a virtual version of a pendrive linux I guess.  I'm using it right now to type this.  Anyway, as I've said, I'm not very techy, so I'm not clear on what distribution this is emulating, but I was wondering if there was a similar one based around Ubuntu?  I want Ubuntu specifically, and this is nice and all, but it's not Ubuntu.

Also, anyone with any knowledge about this know if it's likely this will screw with my work computer (it lets me make persistent changes while I'm on here, so I'm wondering how those are kept seperate).  I know you guys are Ubuntu specific, but I figure maybe one of you knows what in the world I'm doing.  I sure don't.  It looks awful nice though.

---

### Post by Zieb on 2009-03-04
Not wanting to SPAM the boards, but just an update.  The USB solution works perfectly (I went to pendrivelinux.com for future reference of anyone looking this up).  It is absolutely what I wanted and works perfectly on my home computer.  It's a great solution and well worth the little bit of time it takes.

---

### Post by mlentink on 2009-03-04
> **Zieb said:**
> The USB solution works perfectly (I went to pendrivelinux.com for future reference of anyone looking this up). 


I don't know which solution this is, but it's  perfectly possible to install Ubuntu to a USB-harddisk, and have it completely separate (ehh. you might be able to mount the internal NTFS-disk to share files) from your windows install. I use this method all the time to try out new Ubuntu releases or other distro's.
Nice thing is you can do it all with a Ubuntu LiveCD and a bit of attention...

---

### Post by kansasnoob on 2009-03-04
Look at either Puppy or Damn Small:

[http://www.puppylinux.com/](http://www.puppylinux.com/)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

I've used Puppy enough to know I can easily store my "stuff" on a flash drive.

I like Damn Small because of the abilty to use it to install Debian to the Hard Drive.

Ahhhhhhhhhh, I like 'em both!

---

### Post by anjilslaire on 2009-03-04
The "create a usb startup disk" thats builtr into Intrepid 8.10 creates a persistent usb Ubuntu installation image that also saves your settings (hence the "persistent" refernce)

It's not just for creating ain installer image. It can save your docs, settings, etc.

Download the 8.10 ISO, burn & Boot it live CD, run the tool from the menu, point it at the ISO on your Windows drive, pick your usb stick as the destination, and you're done.

Remove the CD, reboot from usb stick, and you're off.

---

### Post by sloggerkhan on 2009-03-04
I've been running my desktop from a live CD for several days. It gets kinda laggy if you let it sit, but otherwise is fine. (I do have 4 gigs of RAM and it's using swap on my hard disks, though.) I don't think I'd choose to do so long term.

(I've got a screwed up bootloader I don't want to try fixing until I back up, which I can't do until I reinitialize my RAID, which I had to wipe because I somehow formatted it with way too few inodes. So yeah, I'm an idiot.)

Like others have said, USB or Wubi are probably good options.

---

### Post by redseventyseven on 2009-03-05
> My work computer was giving me headaches with the USB live (it won't boot from the USB at all even if I tell it to), so I put something from the pendrivelinux site on there called QEMUPDL. It's a virtual version of a pendrive linux I guess. I'm using it right now to type this. Anyway, as I've said, I'm not very techy, so I'm not clear on what distribution this is emulating, but I was wondering if there was a similar one based around Ubuntu? I want Ubuntu specifically, and this is nice and all, but it's not Ubuntu.

Sounds like your IT guys at work have (understandably) prevented people from booting operating systems other than the one that they support.

As for the type of Linux used by QemuPDL, the distribution it is emulating is, well, PDL, or PenDriveLinux. It's similar(ish) to Ubuntu insofar as both are based on Debian. Why do you want Ubuntu specifically? What's missing from PenDriveLinux that you need? Try to answer those questions, then maybe you'll be able to find and install packages that address those needs.

---

