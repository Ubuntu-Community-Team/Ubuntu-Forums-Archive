---
title: "Linux on USB - Only works on certain vendors USB  flash drives"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by frankiebaby on 2009-09-14
--------
[COLOR=red]**[COLOR=black]Edit note:[/COLOR]** Solution posted @[/COLOR]
[http://www.uluga.ubuntuforums.org/showpost.php?p=8004221&postcount=22](http://www.uluga.ubuntuforums.org/showpost.php?p=8004221&postcount=22)
------
 
I am a complete newbie to Ubuntu, but familiar with running portable window's software on USB flash drives. 
 
I am stuggling to understand why certain USB flash drives, with Ubuntu installed, do get recognised during boot, such as the Busbi brand, but others like Imitation do not, even though Ubuntu will recognise them as removable drives, once it is up and running but just will not boot Ubunutu from.
 
It seems that whilst Unbuntu and Windows seems to recognise all USB drives as removable storage, but only a few (e.g Busbi) can be used to boot Ubuntu direct from the flash drive during boot.
 
I would appreciate any guidance on this topic and details of any way of knowing exactly which specific USB flash drive vendor products can boot Ubuntu? This will save me wasting money on USB flash drives that just don't work. OF course I am assumming the computer BIOS can be set to boot from a USB flash drive (memory stick), mine can so that is not a problem.
 
I must say, this is my first foray into using Ubuntu and I am impressed by it's potential, but having only certain vendors USB flash drive to boot from must be effecting many users.
 
Thanks
Frank

---

### Post by earthpigg on 2009-09-14
some thumb drives include 'features' that are actually windows firmware that will mess with any non-Windows mojo. 

if you see a thumb drive that includes any sort of 'Windows power user features' or other crap, avoid it.

generic thumb drive:

USB connector jack - user storage space

stupid feature-packed thumb drive that costs $10 more:

USB connector jack - **stupid feature crap** - user storage space



that stupid feature crap physically separates the jack from where you install ubuntu... so, when the computer tries to boot from the thumb drive the stupid feature crap tells the computer "nope, nothing bootable here" without even giving the computer a chance to talk to where you installed Ubuntu.

---

### Post by earthpigg on 2009-09-14
i can't remember the brand, but one thumb drive i had gotten my hands on could have the stupid feature crap disabled --- but it could only be done using Windows software you downloaded from the thumb drive manufacturer's website.

---

### Post by philinux on 2009-09-14
See here :-

[http://www.pendrivelinux.com/recommended-usb-flash-drives/](http://www.pendrivelinux.com/recommended-usb-flash-drives/)

---

### Post by earthpigg on 2009-09-14
> ...others like Imitation do not work...

[http://www.amazon.com/Imation-USB-Pocket-Flash-Drive/dp/B000I83FC4/ref=sr_1_1?ie=UTF8&s=electronics&qid=1252921172&sr=8-1](http://www.amazon.com/Imation-USB-Pocket-Flash-Drive/dp/B000I83FC4/ref=sr_1_1?ie=UTF8&s=electronics&qid=1252921172&sr=8-1)

> _Imation 4 GB USB 2.0 Pocket Flash Drive_

Product Description
With a compact, professional design, the Imation Pocket Flash Drive makes it easy to manage and transfer digital files. This lightweight, yet durable drive easily slips into your pocket, onto a keychain, or around your neck with the included lanyard. _***Combined with password protection and drive partitioning software***_, the Pocket Flash Drive is an affordable way to safely transfer data, music, photos or video.

---

### Post by niteshifter on 2009-09-14
> **earthpigg said:**
> i can't remember the brand, but one thumb drive i had gotten my hands on could have the stupid feature crap disabled --- but it could only be done using Windows software you downloaded from the thumb drive manufacturer's website.

The name for that crapware is U3. USB key drives that have it usually sport the U3 logo. If one has choice between a U3 drive and a non-U3 drive - pick the non-U3 drive, even if it's a few dollars more.

As to removing it: Some drives can be done using the "generic" removal tool available from U3.com. Other drives (Sandisk in particular) can't be "de-U3'd" with the generic tool, one has to hunt for it on the manufacturer's web site. 

So which tool to use? Google is your friend in this. "U3 removal tool" will take you close - currently links toward the U3.com tool is at the top of the returns. Not sure or that tool didn't work? Same search, but then search within results with the manufacturers name.

In either case you'll need windows to run that software, either a real windows install or as a virtual machine - for VirtualBox that means the PUEL version from Sun's website.

---

### Post by earthpigg on 2009-09-14
> **niteshifter said:**
> The name for that crapware is U3.

yup, that was it.

grrr

---

### Post by Mighty_Joe on 2009-09-14
Some vendor's USB drives may not be set up to play nice with Ubuntu.  For example, there's a known bug with the USB Creator if the drive does not have a [partition table]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865").  It's easy enough to fix.  Fire up Gparted and create one.
I've only run into one drive (Imation) that had the problem above.  The others I've used, Transcend, Sony, Sandisk (with U3 removed, of course), all worked.

---

### Post by frankiebaby on 2009-09-21
Thanks for the tips, I am following up on them. It does seem obvious that many USB drives cannot be used as LiveUSB's for Ubuntu. Even if one vendors product does work, another model does not. E.G: Busbi
 
Damn SMall Linux works on a SD card, but not for Ubuntu. 
 
These sort of problems are damn frustrating and I don't want to waste money and time trying to figure out which USB flash models work and which don't.
 
This webpage highlights how to find the Vendor ID (VID), the flash drive that works has a USB flash (Busbi) has a VID of 1307, so there seems to be a connection with the type of chip set on the drive and it's compatibility  as a Compact Disk File System and hence the BIOS might be treating the drive as a virtual CD drive.
[http://blog.usboffice.kr/?p=146](http://blog.usboffice.kr/?p=146)
 
I have tried to get Ubunutu to work via the the integral USB start up disk function and Unebootin, but both don't work.

---

### Post by earthpigg on 2009-09-21
> These sort of problems are damn frustrating and I don't want to waste money and time trying to figure out which USB flash models work and which don't.

find a brand that works, and stick with it.

---

### Post by frankiebaby on 2009-09-22
USB flash drives I tried to create a LiveUSB Ubuntu installation on:
 
**Kingston**: Data Travellor - [COLOR=red]**Does not work **[/COLOR]
 
**Bubsi **from Argos.co.uk model  675/9197 - Result=[COLOR=red]**Does not work **[/COLOR]
_[COLOR=#0066cc][http://www.argos.co.uk/static/Product/partNumber/6759197/Trail/searchtext%3EBUSBI.htm](http://www.argos.co.uk/static/Product/partNumber/6759197/Trail/searchtext%3EBUSBI.htm)[/COLOR]_ []("http://www.argos.co.uk/webapp/wcs/stores/servlet/ProductDisplay?storeId=10001&catalogId=1500001801&productId=1500515959&langId=-1&engine=froogle&keyword=Busbi+2GB+USB+Flash+Pen&_$ja=tsid:11527|cc:|prd:6759197|cat:Usb+Memory+Sticks")
Although this **Busbi** Argos model 675/7876 [COLOR=darkgreen]**does work **[/COLOR]:
[http://www.argos.co.uk/static/Product/partNumber/6757876/Trail/searchtext%3EBUSBI.htm](http://www.argos.co.uk/static/Product/partNumber/6757876/Trail/searchtext%3EBUSBI.htm) + @ [http://www.busbi.eu/archives/22](http://www.busbi.eu/archives/22)

 
**SanDisk** Cruzer **[COLOR=#ff0000]Does not work[/COLOR]**
**[http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&parentCategoryID=11442900&categoryID=20127100](http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&parentCategoryID=11442900&categoryID=20127100)**
**[COLOR=#ff0000][/COLOR]** 
**[COLOR=#ff0000][/COLOR]** 
[COLOR=red][COLOR=#000000]**SanDisk:** SD Card Ultra II (USB)  [/COLOR][/COLOR][COLOR=#ff0000]**Does not work**[/COLOR]
**[COLOR=#ff0000][/COLOR]** 
[COLOR=#ff0000][COLOR=black]**Imtation: **Atom[/COLOR]** Does not work**[/COLOR]
[http://www.imation.com.au/products/flash_drives/atom.htm](http://www.imation.com.au/products/flash_drives/atom.htm)
**[COLOR=#ff0000][/COLOR]** 
[COLOR=black]Therefore relying on a specfic brand does not mean all or maybe any of it's particular models with work. I cannot see anything in the Unbuntu website that highlights that many if not most USB flash drives simply don't work. [/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]It cannot be my BIOS, as one of the Busbi models does work. [/COLOR]
[COLOR=black][/COLOR] 
[COLOR=black]If only certain USB flash drives do work it would be nice if unbuntu.com or another would create an uptodate list, giving exact details of the working models, with URL's, as a brand name and model name like PNY's Attache, covers lots of different models, all under the Attache name, so one PNY model might work but another with the same 'name' may not.....[/COLOR]
 
Anyway I will plod on

---

### Post by t0p on 2009-09-22
> **frankiebaby said:**
> It does seem obvious that many USB drives cannot be used as LiveUSB's for Ubuntu. Even if one vendors product does work, another model does not. E.G: Busbi
 
I've bought a lot of usb sticks in my time, and I've never found a model that won't boot ubuntu.  Note that I only buy proper usb sticks, not the "U3" type crap mentioned in this thread, and I've tended to buy inexpensive sticks.  And they've all seemed to work fine for whatever I've needed them for, including use as live usb.  So my advice is: buy cheap generic usb sticks.

> **frankiebaby said:**
> 
Damn SMall Linux works on a SD card, but not for Ubuntu.

I've successfully used SD cards to boot ubuntu from.  Specifically, cards from Fujifilm and those marketed as Boots The Chemists own label.  I'm curious to know which SD cards *don't* work with ubuntu.  I'd also like to know *why* they won't work for ubuntu but will work for Damn Small Linux.  I can't think of a reason for this.

---

### Post by gordintoronto on 2009-09-22
> **frankiebaby said:**
> USB flash drives I tried to create a LiveUSB Ubuntu installation on:
 
**Kingston**: Data Travellor - [COLOR=red]**Does not work **[/COLOR]
 


It works for me.  Did you use parted/gparted to mark it bootable?

---

### Post by Mighty_Joe on 2009-09-23
[QUOTE=frankiebaby;7990703] 
**SanDisk** Cruzer **[COLOR=#ff0000]Does not work[/COLOR]**
**[http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&parentCategoryID=11442900&categoryID=20127100](http://shop.sandisk.com/DRHM/servlet/ControllerServlet?Action=DisplayCategoryProductListPage&SiteID=sdiskus&Locale=en_US&Env=BASE&parentCategoryID=11442900&categoryID=20127100)**
**[COLOR=#ff0000][/COLOR]** 


Works for me.  Did you remove U3?  Did you create a primary partition using GParted as I suggested in my earlier post?

---

### Post by 3rdalbum on 2009-09-23
Try using Unetbootin; then it's not vendor-specific or BIOS-specific, and it should always work.

---

### Post by frankiebaby on 2009-09-24
Thanks, I have tried GParted within Ubuntu and as a separate ISO/OS. I created a new partition table making the flash-drive 'unallocated', then created and formatted it to Fat32.  I had also done the same using Window's EASEUS partition manager. 
 
I used the Unebootin and Unbuntu's own Make a USB start up disk.
 
[COLOR=red]None of the above worked.[/COLOR]
 
Also trying to format/partition, remove the U3 function has caused the flash to brick up and I have been unable to re-format in Ubuntu or Window's.
 
As I have said I did get only one flash drive to work, so I conclude that it must be that certain Vendor's flash drive just don't work full-stop.
 
Maybe I am using GParted wrongly, so if anyone can give a brief step by step guide I would be most appreciative.

---

### Post by Mighty_Joe on 2009-09-24
> **frankiebaby said:**
> Also trying to format/partition, remove the U3 function has caused the flash to brick up and I have been unable to re-format in Ubuntu or Window's.

How did you try to remove it?  Most vendors provide a [tool]("http://kb.sandisk.com/app/answers/detail/a_id/2550").  Not using the tool would probably brick it.

> **frankiebaby said:**
> 
As I have said I did get only one flash drive to work, so I conclude that it must be that certain Vendor's flash drive just don't work full-stop.


Actually, since no one else can reproduce your problem, it points to the problem either being with your procedure or hardware.  Have you tried using different computers?

---

### Post by frankiebaby on 2009-09-24
Thanks, I managed to unbrick it. The SanDisk Cruzer (U3 Smart) has an inbuilt removal function, which I used. I then formatted all to Fat32 and installed a LiveUSB, but no joy. I will have to try another PC to see what happens. But as I said one flash disk does work, so not sure what the overall issue is.

---

### Post by dummy910 on 2009-09-24
> I then formatted all to Fat32 and installed a LiveUSB, but no joy.
I just solved _this very same issue_ yesterday and posted on it [**via this link**]("http://ubuntuforums.org/showthread.php?t=1273928").

Here's my post:
> I followed just about every how-to on the net, yet the only one that would boot via the instructions was the PendriveLinux flavor, all well and good, but I really wanted either 9.04 or the 9.10 flavored Ubuntu-Gnome to boot as an install medium for clients machines, as well as a troubleshooting tool.

To make a very long story short, I laid finally ended up formatting a "fat16" partition on the "1st" 4gb of this 16gb drive(the rest whatever layout ya need to use), then ran Unetbootin to install the given( in this case, 9.10alpha .iso)and bam!, Houston, we now have a drive that boots!

Finally, and just about every how-to I ran across on the net states to format the partition as fat32. Well not in this case mission control, **it's fat16**

Note:
For anyone running across a drive with the miserable "U3" , it lies on as an "isofs" boot partition, and MUST be removed. Just go to the sansdisk site and download the windoze-only tool named the **U3 Launchpad Removal Tool** that will allow you to wipe all the partitioning off that thumb-drive your trying to get to boot. _The thumb-drive WiLL NOT boot until this tool-wiper is run_, period.

Worked for me ;)

---

### Post by LewRockwell on 2009-09-24
Cheerios Mates!

[http://en.wikipedia.org/wiki/Dd_(Unix)](http://en.wikipedia.org/wiki/Dd_(Unix)))

we were sure we posted this once before

must have been a glitch in the matrix

Good Day Mates!

.

---

### Post by Spiffworks on 2009-09-24
> Try using Unetbootin; then it's not vendor-specific or BIOS-specific, and it should always work.

Slightly off topic, but no matter what I tried, no USB boot method worked on computers with AwardBIOS on their motherboards(every Intel motherboard I encountered). I found the zip method of doing it, but a live usb without persistence is no better than a live cd, so i didn't give that a try.

Does anyone know of a list of motherboards which have the buggy version of AwardBIOS, so that one can avoid those in the future?

---

### Post by frankiebaby on 2009-09-25
[COLOR=red]**Eureka... :P**[/COLOR]
 
I managed to get the SanDisk Cruzer to work, by a bit of trial and more error.
 
I gave up and decided to install Ubuntu on a USB Hard Disk, then when I booted up and changed the BIOS option so the USB Hard Disk was the first choice. On startup I noticed the Cruzer drive was active and it turned out that Unbuntu was working from the Cruzer disk.
 
Oh well, very good to get things going. I had just taken the BIOS options too literally and always gave priority to the 'USB memory stick' option, without realising that it would work on the 'USB Hard Disk' option instead.
 
Thanks to everyone for suggesting tips and not giving up on this situation. This situation helped me use and understand some of the BIOS options for the first time, as well as GParted, Unebootin, Persistence etc, so these trial(s) and error(s) have helped my learning, so once again thanks for bearing with me as a newbie. I was also impressed by the speed of the responses to my help requests and how many people got involved.
 
Working from a LiveUSB is so, so much better than a CD/DVD and it is possible to set up a persistence option to retain documents and changes through restarts.
 
I did dip my toe into the U3 (smart) facilities, but not sure how useful they are when compared to all the portable apps that work on a standard (stupid) USB flash drive.

---

### Post by dummy910 on 2009-09-25
> I did dip my toe into the U3 (smart) facilities, but _not sure how useful they are_ when compared to all the portable apps that work on a standard (stupid) USB flash drive.I found the [COLOR=Red]**[U3 Launchpad Removal Tool]("http://u3.sandisk.com/launchpadremoval.htm")**[/COLOR] was a crucial part in the process as I couldn't get **Gparted** to do anything with that "isofs" partition that was installed, although I am not an expert in Gparted. 

Again, once I got **wrid of that "isofs"** on the drive and reformatted the drive with Fat16(with Gparted), ran **Unetbootin** to burn the .iso install image, the thumb now boots-installs perfectly.

---

