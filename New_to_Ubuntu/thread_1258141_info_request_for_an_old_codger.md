---
title: "info request for an old codger"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by alan70years on 2009-09-04
[SIZE=4][CENTER]Info request
[/CENTER]
At the moment my computer set-up consists of an AMD Duron running Windows 2000 s/p4 with 256 RAM and a Maxtor 40gb hard drive.
If I save my hard drive (Avanquest disc copy &clean perhaps) with my OS, settings, and files, then upgrade the RAM to 1gb (as advised by Crucial) and the hard drive to say 250gb and then reload Windows: -
[LIST=1]
[*]Will windows still think it has 256 RAM and 40gb hard disc? And
[*]If I then load Ubunto Linux will I be able to use all the new space for Linux
[/LIST]Also … my ISP is (or was NTL) now Virgin media. Just recently I had cause to ask for assistance from them with regards my modem while talking to their technician I mentioned that I planed to build a Linux PC and asked what I would need to do to get it up and running via their ISP
To my surprise I was told they did not support Linux, any one out there running Linux on Virgin media? And how did you get it done?
Lastly I have checked for drivers for my Epson printer and found that I need RPM to LSB or DEB to LSB, 3.1 or 3.2. I assume DEB stands for Debian but what is the rest? I also cannot find the drivers for my Epson perfection V100 scanner! Any idea’s :confused:
[/SIZE]

---

### Post by NoaHall on 2009-09-04
Windows will be able to tell the different ( although you'll have to reinstall on the 250GB hard drive if you want to use it as primary) You'll be able to use the space not used by windows with linux. Deb is the file you want on Ubuntu. ( although you can convert RPM if needs must)

---

### Post by mike555 on 2009-09-04
Sounds very do-able , if you have highspeed internet through a modem with an ethernet cable it should be OK , 1 GB  Ram is more than enough for Ubuntu Linux , good luck!

---

### Post by Old_Grey_Wolf on 2009-09-04
The memory and HDD upgrades seem good things to do. As far as I have been able to determine, the AMD Duron processors seem to be single core 1 to 1.8 GHz processors. If that is what you have, it may be a little slow. If you have more specs for the computer, please post them. 

I would give it a try. You can always try it with the Live CD in order to determine if the other hardware is compatible. The computer will defiantly run slower from a Live CD rather that from an installed OS.

Edit: I don't know of any ISP that claims to support Linux. However, I haven't had problems getting my Linux machines to work with several ISPs.

After you try the Live CD you can install it. It will provide the ability to allocate any disk space for Ubuntu Linux that you do not need for your Microsoft Windows OS.

There is a fair chance that Ubuntu will detect and use the appropriate drivers for your Epson printer and scanner.

---

### Post by CatKiller on 2009-09-05
> **alan70years said:**
> Also … my ISP is (or was NTL) now Virgin media. Just recently I had cause to ask for assistance from them with regards my modem while talking to their technician I mentioned that I planed to build a Linux PC and asked what I would need to do to get it up and running via their ISP
To my surprise I was told they did not support Linux, any one out there running Linux on Virgin media? And how did you get it done?

If anyone says "we don't support Linux" it generally means that they have no idea what they're talking about, and just want you to go away.

Virgin are my ISP. You don't need to do anything specific. Plug your cable "modem" into your network card (or router if you have one) and go.

---

### Post by QIII on 2009-09-05
What your ISP supports is traffic configured in an internationally standardized format both to and from your router.

It is virtually OS independent.

Some *websites, *however, do determine what browser you are using.  Lazy or malicious web developers may ignorantly or deliberately design their sites for non-standards-compliant browsers such as the one developed by a large corporation that will remain nameless.

---

### Post by oziwombat on 2009-09-05
Hi Alan .
As one old codger to another , cost to upgrade your old pc is probably not worth it . Cost to upgrade [upwards of $300.00 Aus ] almost half the cost of a new base Dell & depending on what you intend to use it for the Dell should do things faster & last longer . I have two PC's & just use Ubuntu for Internet use as it is much safer to use & my old 2.66 Celeron 512gb ram & 20 gb hard drive is fast enough for me :D:D 

 BTW Ubuntu should pick up any drivers you need & should pick up both printer & scanner & ISP's not a problem .
Cheers Ozi

---

### Post by mapes12 on 2009-09-05
> **alan70years said:**
> [SIZE=4][CENTER]Info request
[/CENTER]
At the moment my computer set-up consists of an AMD Duron running Windows 2000 s/p4 with 256 RAM and a Maxtor 40gb hard drive.
If I save my hard drive (Avanquest disc copy &clean perhaps) with my OS, settings, and files, then upgrade the RAM to 1gb (as advised by Crucial) and the hard drive to say 250gb and then reload Windows: -
[LIST=1]
[*]Will windows still think it has 256 RAM and 40gb hard disc? And
[*]If I then load Ubunto Linux will I be able to use all the new space for Linux
[/LIST]Also &#8230; my ISP is (or was NTL) now Virgin media. Just recently I had cause to ask for assistance from them with regards my modem while talking to their technician I mentioned that I planed to build a Linux PC and asked what I would need to do to get it up and running via their ISP
To my surprise I was told they did not support Linux, any one out there running Linux on Virgin media? And how did you get it done?
Lastly I have checked for drivers for my Epson printer and found that I need RPM to LSB or DEB to LSB, 3.1 or 3.2. I assume DEB stands for Debian but what is the rest? I also cannot find the drivers for my Epson perfection V100 scanner! Any idea&#8217;s :confused:
[/SIZE]Hi Alan

I haven't used the cloning application you refer to but I have used Clonezilla which has support for cloning the NTFS file system (Win200...right?). It copies the MBR so that the re installed clone boots properly. I would set up the new drives partitions using Gparted ahead of of installing. Then put the cloned Win OS back first. It will detect the increased RAM and what have you. Check it boots OK then move on to install Ubu. Grub will detect the working Win partition to create a dual boot configuration for you.

The tech guy at Virgin Media probably thought you were talking a foreign language. You can run Linux across _ALL_ ISP networks. I'm not sure what broadband modem kit they have given you but if it's the type that plugs into a USB port then get yourself a proper ethernet router and try and set this up into your network instead. 

Not sure about the drivers for your printer / scanner but like others have commented plug em in and see if Ubu detects them. It probably will. BTW for printers and the like I have found HP provide the best support. Most of their kit just works on Linux.

---

### Post by Wheeeze on 2009-09-05
Hi Alan,  To hopefully help with the second part of your query, I used to use an old laptop running XP which was on Telewest (now Virgin Media) dial-up.  When I upgraded to broadband, the engineer got it all going and that was that.  

Time has gone on and I have added a wireless router to enable me to use the old lappy in other rooms.  Then I *really* upgraded by buying a basic desktop from a local retailer specifically for getting off Windows and trying Ubuntu.  After plugging the modem into the computer, running the OS, I was on t' internet without any problem!  I can't remember though, if I had to use my Telewest password stuff.  If I did, then it was straightforward.  I've never had to ask for Virgin's tech support.

If your computer communicates with V.M. using Windows, then I would guarantee that when you fire up Ubuntu, you will have no problem, as QIII outlined above.  

Getting my computer onto wireless was something else....  but it all works fine now!

---

### Post by lkraemer on 2009-09-05
Alan,
I'd suggest doing things in an orderly manner, and do a little
testing with a LiveCD before you start ordering parts.

We need a few questions answered to clarify what you want as the
end result?

1.  Do you use Dialup?
2.  Is your Modem an ISA or PCI Internal WinModem? Brand? Model?
3.  Does your computer (Laptop or Desktop) have the necessary slots
    for the memory upgrade?  (Most likely PC3200 would be my guess
    since it is AMD Duron)
4.  Do you have the new hard drive yet?  (Suggest Western Digitial)
    (Drive most likely is IDE instead of SATA!?????)
5.  Do you have a SPARE connector on your IDE cable on the Primary
    or Secondary IDE Ports to add a SLAVE Hard Drive?  (New 250 Gig) 
6.  Do you want a Dual Boot System?  Sounds as if you do!

Download and burn LiveCD's of the following software:
1. Clonezilla
   [http://clonezilla.org/](http://clonezilla.org/)
2. Ubuntu Version you will be installing. (Probably 32 bit)
3. Supergrub
   [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
(Boot each one to make sure they work properly)

I'd start with just the Memory Upgrade.  That should be easy.  Just
power down and insert the new memory.  Then power up.  Windows 2K
should recognize the new memory.  Next I'd reboot, with the Ubuntu
LiveCD inserted and take a test drive of Ubuntu, making notes on what 
doesn't work properly.  (We know the Modem won't work, Wifi, Scanner,
and Printer, so just skip these for now.)  After you are satisfied, you
can continue.

Power Down, and install the New 250 Gig drive on the IDE cable as a SLAVE
with maybe your CD Drive. (MUST SET Drive JUMPER PROPERLY, two devices on
an IDE cable ...One is MASTER and the other is SLAVE....)  Then, boot
from the Clonezilla LiveCD and do a disk to disk copy.  (Your present 2K
disk will be copied to the 250 Gig drive.. MAKE sure SOURCE and DESTINATION
are CORRECT!)  Once that is done you can REPLACE the original drive, using
the 250 Gig (Setting the Jumper to MASTER if two devices are on the
IDE cable, or cable select if that was what you were using, or whatever
the drive states if it is the only device).  At this point I'd boot the
new 250 Gig drive on Win 2K and make sure it is working 100%.  It should be.
At this point you can increase the Win 2K partition from the Ubuntu LiveCD
by booting Ubuntu and running gparted, if so desired.  Otherwise create your
Primary partitions for linux-swap (2 times your RAM), / and /home, or you can
just use the remainder for Ubuntu without a separate /home.  Your 
choice!  MAXIMUM of 4 Primary Partitions.  (Format the Ubuntu partitions
as EXT3, and the linux-swap.)  Then exit gparted.

Proceed with the install of Ubuntu using manual partition, and name the
partitions as /, /home, etc.  Then continue with the install.  Install
GRUB to the MBR of Win2K. (Supergrub can repair this when needed)
When finished Boot into Ubuntu.

The Modem, Printer and Scanner will come later.  (Scanner most likely will
never work under Linux, but if you have Dual Boot, it will still work
on Win 2K.  Probably same for Printer....  Modem - Might be able to use!
External Serial US Robotics Hardware Modems work good with Linux.

More to follow as you answer the questions.

lkraemer

---

### Post by Shazaam on 2009-09-05
+1 for Clonezilla. I cloned an 80gig Western Digital PATA (IDE) drive that was failing (loud clicks) to another Western Digital (160gig PATA) that went without a hitch. Boots and runs fine.

Things to remember before cloning...
1. Defragment ALL source disk Windows partitions first (better done in Safe Mode).
2. Make sure you have enough unformated room on the target drive to hold the cloned drive/partition.
3. A Clonezilla livecd loaded to ram (available on the Clonezilla boot screen) is the way to go.
4. Do a chkdsk on the new setup just to be safe when done.

You would run Clonezilla (direct disk to disk) like this...
Boot Clonezilla cd to ram.
Choose disk to disk (local not network).
Choose source disk.
Choose target disk.
It took about 40 minutes, even cloned the bootloader/mbr, did NOT confuse grub or Windows on reboot. When done I used my Ubuntu livecd to resize the 80gig partition to fill the target (160gig) drive.

---

### Post by Jerry N on 2009-09-05
From one old codger to another, and based on my experiences in messing with a bunch of older computer equipment, I think you are going to find Ubuntu to be frustratingly sluggish compared to Windows 2000 on this old setup.  I think I agree with the suggestion that you use your money to purchase a new computer, on which you can then dual boot Ubuntu and Windows 2000 if you wish.  You can easily connect the two computers together and share files across a network.  A real "geezer geek" would of course forget the cost of upgrading and put a new motherboard with a dual or quad core AMD CPU and a couple of GB of RAM and a new HD in the old box.:)

Jerry

---

### Post by LewRockwell on 2009-09-05
don't know where you are at, but around here almost everything over a year old gets a $100.00 cash offer and NOTHING more

all the stores(online/offline) are offering brand new warranted machines for $300.00 to $400.00 USD

these are full-size full-function machines from the likes of TOSHIBA and COMPAQ...not some no-name brand that will go out of business and leave you hanging

we can almost guarantee you that if you buy from wallyworld and keep your receipt...if there's a problem and you make noise at the return counter...you will at least get store credit if nothing else

if you lived close enough we would donate and deliver a machine if we had an appropriate one available(just don't tell everyone...lol)

as always, your mileage may vary

.

---

