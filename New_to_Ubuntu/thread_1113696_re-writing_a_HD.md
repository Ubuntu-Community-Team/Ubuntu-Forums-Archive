---
title: "re-writing a HD"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by rock_fan_09 on 2009-04-01
Ok, so I have something wrong with my hard drive a virus i think that i cant find or remove. What I want to do is rewrite over the entire hard drive not just delete partitions and change type. Can i use FDISK to write over the entire HD or what program should i use. The computer is running on a live cd so the entire HD is available to reformat. Also should i include the mbr in this?

---

### Post by |Mitch| on 2009-04-01
deleting all the partitions will delete everything on the HD

---

### Post by Mark Phelps on 2009-04-01
> **|Mitch| said:**
> deleting all the partitions will delete everything on the HD

Actually, no it doesn't -- delete everything that is.  What it does is remove access to the files and directories.  But in fact, it leaves the data intact.  If it didn't you wouldn't be able to run utilities like testdisk and photorec and get your files back -- they would be "deleted".

What's more along the lines of what you want is dban.  Read the following link:

[http://www.dban.org/]("http://www.dban.org/")

---

### Post by rock_fan_09 on 2009-04-02
> **Mark Phelps said:**
> Actually, no it doesn't -- delete everything that is.  What it does is remove access to the files and directories.  But in fact, it leaves the data intact.  If it didn't you wouldn't be able to run utilities like testdisk and photorec and get your files back -- they would be "deleted".

What's more along the lines of what you want is dban.  Read the following link:

[http://www.dban.org/]("http://www.dban.org/")

Mark - there isnt much info on dban on that link. have you used it before and does it still leave your HD stable and ready for a reload???

---

### Post by egalvan on 2009-04-03
> **rock_fan_09 said:**
> Mark - there isnt much info on dban on that link. have you used it before and does it still leave your HD stable and ready for a reload???

click on the "About DBAN" link for some more info...

I've been using this little gem for over a year to clean used drives.

It **COMPLETELY** wipes a drive.

There is NOTHING left on it.

Totally ready to use as you see fit.


download the ISO and burn to a CD...
reboot and get it running.

But be careful, as it **COMPLETELY** wipes the drive...

yes, I'm repeating myself.
This is a powerful tool.
It's very useful.

I love it.

ErnestG

---

### Post by rock_fan_09 on 2009-04-03
> **egalvan said:**
> download the ISO and burn to a CD...
reboot and get it running.

But be careful, as it **COMPLETELY** wipes the drive...

ErnestG

ok i have the usb version and the .iso but no cd burner on this laptop and no instructions on the about site - Completely is what i want - a BRAND new clean HD wit no remnants of windows virus on it to attack the new os

---

### Post by BkkBonanza on 2009-04-03
google: dban usb boot
has a yahoo page with some info.

---

### Post by rock_fan_09 on 2009-04-03
i have installed the program to a usb drive but when i try to boot off of it the comuter says operating system is missing? Why am I not getting the boot off of the usb from dban?

---

### Post by BkkBonanza on 2009-04-03
There may be some other steps you need. Try to find a general info page about making usb bootable. There are a few things it needs. The boot partition needs to be marked as bootable. That is either done when formatting the drive, or can be done later using fdisk. Then it also needs a MBR suitable for booting. Also some older system bios have different boot methods where they treat the usb like a floppy rather than a hard disk. I have had success getting usb to boot for Backtrack but sometimes with other apps it has been troublesome.

---
I just googled and found these steps. May help you but be sure that you use the correct device name, it may not be /dev/sda - probably more like /dev/sdb - check first or else you will bugger your main hard drive.
---

With cfdisk you can partition the USB stick. You need to create a type 06 (=FAT 16) partition with a bootable flag.

cfdisk /dev/sda


When the stick is partitioned you have to format it. Use the folllowing command:

mkfs.vfat /dev/sda1


Now the USB stick needs a bootloader. Syslinux is a lightweith bootloader for floppy, network or cdrom. Intall it with the following command:

syslinux /dev/sda1

---
Then you go ahead and install dban onto the stick.

---

### Post by rock_fan_09 on 2009-04-03
dban includes syslinux.cfg in it and wipes the usb clean before installing itself on it. i had the usb wiped and flagged as bootable and dban still wiped that clean before it installed itself on the usb drive. Damn things like this used to be so easy - no i feel soooooo lost.

---

### Post by rock_fan_09 on 2009-04-03
should have said this is a windows machine and dban has a one click installl all deal in windows - im trying to wipe my HD on my good laptop its where i run my ubuntu but its out of commision now except a live Puppy linux cd. this pos cant do anything but surf the web and thats barely attainable. need my ubuntu back


So basically i downloaded the DBAN - dban-1.0.7-i386 WinImage Self Extractor file. Opening this asks which usb device you want it installed on and then makes you wipe the usb completely clean before it loads itself on it. The USB device then should be bootable and wipe the HD clean leaving rrom for a Windows free install of Ubuntu. BUT I cant get anything from the computer other than operating system is missing. The DBAN install includes initrd, kernel.bzi, Idlinux, syslinux.cfg and more files. This should be fully bootable and functioning.

As of now I ave to run this off of Windows XP or Puppy XP (live linux cd) the only way i can get any computer to turn on.

---

### Post by kevmitch on 2009-04-03
If you've got a linux live cd, you don't need any other special software unless maybe you want to **randomise** the disk, not just delete it. Even then it's questionable whether additional software or headache is necessary.

What you probably want is to literally set all the bits on the disk to 0. To do this, first make sure the disk is not mounted. A sane live cd will not mount the disk by default, but you might want to be careful that it hasn't been mounted automatically in reaction to your trying to access it. 

Now, assuming that your disk is /dev/sda 

```
dd if=/dev/zero of=/dev/sda
```

And go have a cup of coffee or two.

Now if you wanted instead to randomise the disk you could use 

```
dd if=/dev/urandom of=/dev/sda
```

But then you might have to let it run for a day or two depending on the size of your disk. 

People are often interested in doing the latter when they are setting up an encrypted disk. If it were just zeroed, you would be able to tell how much data was on the disk by counting nonzero bits even if you couldn't decode the data. 

Either way the data that was on the disk before either zeroing or randomizing should be essentially gone. It's possible that someone might be able to do some exotic forensics to (partially) read data that had physically been erased, but if you just want to get rid of any trace of viruses, I don't think that'll be too much of a concern. If you were worried about this, you could just zero or randomise it multiple times.

---

### Post by rock_fan_09 on 2009-04-03
> **kevmitch said:**
> 

Now, assuming that your disk is /dev/sda 

```
dd if=/dev/zero of=/dev/sda
```

And go have a cup of coffee or two.



have you ever used puppy - its a picky little distro with supprt as far as anything run in terminal and only accepts packages specially mde for it. its after 11pm and have to be up at 4 am so i will give that a try as soon as i get home from work and post the results after. thanks for the idea.  oh and i think mine is /dev/hda but no ig diff just a letter switch - lol

---

### Post by kevmitch on 2009-04-03
It would have to be pretty stripped down to not have dd. It's part of the GNU coreutils.

---

### Post by egalvan on 2009-04-03
> **rock_fan_09 said:**
> have you ever used puppy - its a picky little distro with supprt as far as anything run in terminal and only accepts packages specially mde for it. its after 11pm and have to be up at 4 am so i will give that a try as soon as i get home from work and post the results after. thanks for the idea.  oh and i think mine is /dev/hda but no ig diff just a letter switch - lol

From the dban web site:

[B]Download the dban-1.0.7_i386.exe file to your desktop and double-click it. This program will install DBAN to a floppy disk or USB flash device; it will not wipe the computer on which it is run.

You cannot install DBAN by copying or unpacking the EXE file to a blank floppy disk or other media.[/B]



As for Puppy, I run Puppy 4.2 and it is a useful distro for me.
I've run it ( and installed it) on many different machines, usually triple-boot with XP & some flavor of Ubuntu.
Very lightweight.
Very fast.
Runs great, for me.
Document handling, internet, video, audio, games.

As for being "picky" and "only accepts packages specially mde for it", well most distros are picky about what packages they will accept.
Try DIRECTLY installing anything not Ubuntu/Debian onto Ubuntu.
It can be done, but not without jumping through minor/major hoops.

Puppy is designed to be SMALL...
It's designed to run totally in RAM... will run well in 128Meg
I've seen it run with 64Meg...
it's designed to be small, as in under 90Meg download.
Compare to Ubuntu at some 700Meg.

If you need something bigger, try Knoppix,
or just run a full Ubuntu LiveCD.

Don't try to use a rock hammer to pound in a framing nail... :)
Ain't gonna work.
Proper tools for the proper job. :)

BTW, ever try Tiny Core?
10Meg download size...
It's amazing...
But no, it does not include OpenOffice :)


Again, I use dban and Puppy on a constant basis.
They both work well AS DESIGNED.

ErnestG

---

### Post by BkkBonanza on 2009-04-03
Did you even try? I'm about 95% sure that puppy has dd built in. Even small 32 MB linux distros have dd. It's very basic. I'm tempted to download and make a virtual machine of it just to see because I can't believe it wouldn't be there.

---

### Post by boof1988 on 2009-04-03
Shred can also be used to write zeros to the HDD.

Assuming the drive is /dev/sdx...

```
sudo shred -n 0 -z -v /dev/sdx
```

...will write zeros to drive /dev/sdx.

```
-n 0 # Don't write any random data to drive (If we only want the zero pass, to save time)
-z  # Make a pass of zeros on the drive
-v  # Be verbose
```

---

### Post by aeiah on 2009-04-03
if dd isnt on puppy id be very suprised too. i know for a fact that it's on the gparted live cd / live usb because i used it last week to fill a hard drive full of zeros that was going back to panasonic after testing.

---

### Post by rock_fan_09 on 2009-04-03
> **egalvan said:**
> From the dban web site:

[B]Download the dban-1.0.7_i386.exe file to your desktop and double-click it. This program will install DBAN to a floppy disk or USB flash device; it will not wipe the computer on which it is run.

ErnestG

dont get me wrong i Love puppy - its just not helping me out now and it and XP are all i have. the dd if=/dev/zero of=/dev/hda did nothing. I have followed exactly what your quote says and dban is installed on my usb drive but nothing laptop will not boot off of it says operating system not found or operating system missing

---

### Post by halitech on 2009-04-03
what is the make/model of the laptop? have you checked the BIOS to see if it supports booting from the USB? Is USB selected as the first boot option?

---

### Post by rock_fan_09 on 2009-04-03
> **BkkBonaza said:**
> Did you even try? I'm about 95% sure that puppy has dd built in. Even small 32 MB linux distros have dd. It's very basic. I'm tempted to download and make a virtual machine of it just to see because I can't believe it wouldn't be there.

i opened rxvt and at the sh-3.1# prompt typed dd if=/dev/zero of=dev/hda and hit enter a white box (cursor) dropped down to thenext line and tat was all that happened 40 min later.

---

### Post by rock_fan_09 on 2009-04-03
> **halitech said:**
> what is the make/model of the laptop? have you checked the BIOS to see if it supports booting from the USB? Is USB selected as the first boot option?

it is a Acer Aspire 5100 series and yes the bios supports usb hdd which is what it reads my usb drive as Ut165 USBFlashStorage as well as USB FDD, USB KEY and USB CDROM boots

---

### Post by halitech on 2009-04-03
if its not booting with the usb hdd option, try the usb key option and see if it works from there.

---

### Post by rock_fan_09 on 2009-04-03
> **halitech said:**
> if its not booting with the usb hdd option, try the usb key option and see if it works from there.

ok - its set to boot USB HDD - then - USB key - then USB FDD then DVDRAM and it loads to Puppy XP off the cd

---

### Post by halitech on 2009-04-03
well, I'd say either the key isn't set up right or the port you have it plugged into itsn't working properly. Do you have another machine that will boot from usb you can try or another port on the laptop to boot from?

---

### Post by rock_fan_09 on 2009-04-03
> **halitech said:**
> well, I'd say either the key isn't set up right or the port you have it plugged into itsn't working properly. Do you have another machine that will boot from usb you can try or another port on the laptop to boot from?

dban sets up the stick on its own and all 3 usb ports on the laptop have the same effect. Same results on a Acer travelmate 230 which i always ran puppy linux on from a usb boot

---

### Post by BkkBonanza on 2009-04-03
Re: your dd attempt. That seems to imply dd is there. Depending on the size of your hard drive it could take a long time. After all it is setting every byte to zero and on a big drive that takes a while. 

Assuming that /dev/hda is present and working, there is very little to go wrong with that command.

If you want to monitor it you could run it as background, like this,

dd if=/dev/zero of=/dev/hda& pid=$!

and then send it signals to dump stats, like this,

kill -USR1 $pid

---

### Post by rock_fan_09 on 2009-04-03
> **BkkBonaza said:**
> Re: your dd attempt. That seems to imply dd is there. Depending on the size of your hard drive it could take a long time. After all it is setting every byte to zero and on a big drive that takes a while. 

Assuming that /dev/hda is present and working, there is very little to go wrong with that command.

If you want to monitor it you could run it as background, like this,

dd if=/dev/zero of=/dev/hda& pid=$!

and then send it signals to dump stats, like this,

kill -USR1 $pid

 ok - i did as you suggested and it moved down 1 line and said   {1} 5563 down 1 more line and came back to the prompt sh-3.1# with cursor, does this indicate that Puppy XP does not have dd installed in it????

---

### Post by BkkBonanza on 2009-04-03
No, it means the process is running now and the process id is 5563.

Type, **ps** and you should see it in the process list.

Type **kill -USR1 $pid** and it should dumps some state info.

Type **kill -15 $pid** to stop it because you gave it the wrong device and it's borking your main system in Kentucky...

Running a command with the & at the end puts it into the background - means it gets started and runs "behind the scenes" while you get the prompt back. You can also see background tasks with the **jobs** command.

The kill command sends a "signal". How a signal behaves depends on the program and this one reacts to USR1 by dumping stats. Most react to -15 by terminating immediately.

---

### Post by rock_fan_09 on 2009-04-03
> **BkkBonaza said:**
> No, it means the process is running now and the process id is 5563.

Type, **ps** and you should see it in the process list.

Type **kill -USR1 $pid** and it should dumps some state info.

Type **kill -15 $pid** to stop it because you gave it the wrong device and it's borking your main system in Kentucky...

it said 32155361+0 records in
        32155360+0 records out 

is that good???

if it is how will i know when dd is finished running???



THANK YOU for your help with this Linux re-born newb. I gotta get away from windows on at least my best laptop and desktop

---

### Post by BkkBonanza on 2009-04-04
Records out/in is not too useful because you'd have to calculate how many bytes it is. But I think it usually says how MB or GB total it's done. If blocks (records) are 512 bytes you'd multiply by 1000 divide by 2 to get approx. bytes... or chop off 6 digits times by 2 to get MB.

You'll know it's done when it doesn't show up in the process list ps, or jobs list. Also it may spew out a Done 5563 at some point. Not sure it does that but if it does it will happen when you don't want it to like in the middle of a directory listing or something.

Congrats on leaving Windows. I still need it for photography but I run it as a virtual machine under Ubuntu - so it knows who's in charge - where it's jailed behind the VirtualBox NAT.

---

### Post by rock_fan_09 on 2009-04-04
> **BkkBonaza said:**
> Records out/in is not too useful because you'd have to calculate how many bytes it is. But I think it usually says how MB or GB total it's done. If blocks (records) are 512 bytes you'd multiply by 1000 divide by 2 to get approx. bytes... or chop off 6 digits times by 2 to get MB.

You'll know it's done when it doesn't show up in the process list ps, or jobs list. Also it may spew out a Done 5563 at some point. Not sure it does that but if it does it will happen when you don't want it to like in the middle of a directory listing or something.

Congrats on leaving Windows. I still need it for photography but I run it as a virtual machine under Ubuntu - so it knows who's in charge - where it's jailed behind the VirtualBox NAT.


sh*t the ps now says

[1]+ Terminated            dd if=/dev/zero of=/dev/hda 

does that mean i stopped the process and its not finished?

ok started it again and...

its now running as 21421 root

how do i know its finished and i cant leave windows altogether - this comp only has XP on it but will get puppy linux installed on it tomorrow 

the other laptop well u gave me a good idea rather than a dual boot xp media edition and ubuntu - im going to ONLY load ubuntu on it and then do a virtual XP media edition if 2g og memory is enough to run both and still use windows to play my downloaded tv shows on the hd tv in 720p res

can you run the virtual windows as a second monitor on the hd tv and ubuntu as primary on the laptop screen?

---

### Post by Ocxic on 2009-04-04
Anyone considered "dd if=/dev/random of=/dev/sda"  [Replace sda with the drive you wish to wipe]
Running that command from a live CD will wipe the drive. Run multiple times for a secure erase.

---

### Post by JackMeadows on 2009-04-04
G'day

I was wondering if it's possible to copy my Complete Linux H/D to another clean H/D so I always have a back-up that will save me re-installing the whole system, with the up-dates, after I have F'it up and need to format and start again?

Something along the lines of Acronis
[http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

With winxp and how it can just stops working I have a dedicated a H/D that is held just to replace XP on my other H/D and so saves me reinstalling XP from scratch.

---

### Post by BkkBonanza on 2009-04-04
I much prefer the vm approach to running WinXP. It may not be able to do absolutely everything as a dual boot (due to virtual driver issues) but it's a lot more convenient. VirtualBox even provides for merging the desktops so that apps from both Linux and XP can be on the same desktop. I don't usually do that as I find that starting the XP vm on the second desktop allows me to flip between both os with ctrl-alt-arrow very easily. I never had much success with running them on different video screens. It seems to be related to my Acer notebook and intel drivers. It may work for you. 2GB was plenty for me to run a few virtual machines. It all depends how much you need for your app. I run my XP in a 512MB machine without problems. I also use it to run several development linux web servers. It's great for trying things out. I tried out monowall and freenas this way. You can snapshot a vm as well so that at any time you can revert back to that state. It's all very cool.

It's possible to take a current XP install and convert it into a vm image. There is a tutorial about it on the virtualbox forum.

Regarding copying hard drives for backup. I've used Clonezilla. Free and easy to use. I thought Acronis also supports linux but not sure, never used.

---

### Post by JackMeadows on 2009-04-04
[QUOTE=regarding copying hard drives for backup. I've used Clonezilla. Free and easy to use. I thought Acronis also supports linux but not sure, never used.[/QUOTE]

Thanks very much, will give  Clonezilla a try, Acronis and Linux ...not sure as it is on another machine so not accessible right now

---

### Post by rock_fan_09 on 2009-04-04
ok, one pass completed and running the second run over of dd. will two times of running dd be good enough to ensure the hard drive is thoroughly wiped. And dd does have the same effect as dban or killdisk?  effectively turning everything to zeros so ALL data is  Forever Wiped??? - 

think i'm going to dl puppy 4.0 Dingo and install it on this machine, cant EVER go back to a Windows only machine again. This thing is sooooo old puppy is like th only linux will run fast on it, or would a attempt at xubuntu be a good try. ubuntu just requires to much system resources even going back to 7.0

---

### Post by halitech on 2009-04-04
if you are used to Ubuntu, try Debian with XFCE which I find much faster then Xubuntu on the same hardware.

---

### Post by rock_fan_09 on 2009-04-04
Re-Wrote the HD twice with dd, and doing a systems recovery restore. Thanks for the help. Once XP is reloaded I can dual boot with Ubuntu

---

### Post by rock_fan_09 on 2009-04-04
How do i mark this thread as solved??

---

### Post by BkkBonanza on 2009-04-05
I actually don't think you gain anything by zeroing many times. If you use /dev/random then I think there may be some benefit as each pass would change the content and randomize the residual magnetic traces. Not that any of this really matters. Unless you're being investigated by federal authorities it seems unlikely anyone would bother with the attention needed to detect pre-erased content. Nonetheless, proper disk wipers like shred will do multiple passes using content designed to reduce residual magnetism. I suspect that one pass with zero is as good as 2 passes. I'm not an expert so if you want a more definitive answer then google and read. I explored it a few years ago and maybe ideas have advanced since then.

---

### Post by egalvan on 2009-04-05
If the usb did not boot,

and the cd does boot,

why haven't you tried making a bootable cd of dban?

Just curious.

You probably aren't reading this anymore.

---

### Post by rock_fan_09 on 2009-04-06
> **egalvan said:**
> If the usb did not boot,

and the cd does boot,

why haven't you tried making a bootable cd of dban?

Just curious.

You probably aren't reading this anymore.

the computer has a cd/dvd player but not a cd burner - so burning a cd wasn't a option.

---

### Post by rock_fan_09 on 2009-04-06
BkkBonaza - thanks for the help - now that i got the other comp working this one is taking a crap - it keeps powering off on its own, grrrr. i want to dual boot this with linux - was thinking puppy or xubuntu or the Lenny Debian i was told about - just gotta figure out how to burn a .iso - for some reason the .iso i dl on here and took to the other comp vis usb stick - nero says its not a recognized format - for 4 different linux dl so far

---

### Post by egalvan on 2009-04-07
> **rock_fan_09 said:**
> the computer has a cd/dvd player but not a cd burner - so burning a cd wasn't a option.

OK, so I thought that might be the problem... :)
wasn't sure...

If you get stuck again, the following store has a good selection of cd/dvd images, and shipping is quick..
they also send some cash to the distro... good way to support the writers.
i've used them...
bought the debian distro, pmagic, puppy, some Ubuntu 8.04 cd's, and the ubuntu repo's on dvd...

[http://www.linuxcd.org/?ref=distrowatch](http://www.linuxcd.org/?ref=distrowatch)

of course, this depends on where you live...
they have world-wide shipping, but that doesn't always pan out.

---

