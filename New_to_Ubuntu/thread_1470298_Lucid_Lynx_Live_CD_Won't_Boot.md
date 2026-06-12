---
title: "Lucid Lynx Live CD Won't Boot"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Xarver on 2010-05-02
Hello, I am trying to install Ubuntu 10.04 on a Dell 05D481.
So far I have no success... For some reason the cd just stayed on the boot menu. I waited a long time still nothing. I trying reburning with a newly downloaded iso and now it just stays on the purple screen... Any ideas? :confused:

---

### Post by Xarver on 2010-05-03
Anyone???

---

### Post by grobar87 on 2010-05-03
i have same problem:(...
after purple screen,i got some error with decompressing:confused:

---

### Post by TheNerdAL on 2010-05-03
What was the speed that you burned it?

---

### Post by Xarver on 2010-05-03
I burned it at the minimum my cd burner could do. 10x

---

### Post by Ibidem on 2010-05-03
Sounds like issues with Plymouth (the splash screen).
Try going into the "boot options" menu; it should be possible to specify to use the "nomodeset" option.
That's my best guess.

---

### Post by Xarver on 2010-05-03
There's no menu. All I get is that screen when I boot the cd.

---

### Post by TheNerdAL on 2010-05-03
Did you check the MS5DSUM?

---

### Post by Xarver on 2010-05-03
> **TheNerdAL said:**
> Did you check the MS5DSUM?

I downloaded the iso 2 times, but no.

---

### Post by grobar87 on 2010-05-03
> **TheNerdAL said:**
> Did you check the MS5DSUM?

How???

---

### Post by wallywally on 2010-05-03
HowToMD5SUM:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by TheNerdAL on 2010-05-03
Checking the MD5SUM is very important.

---

### Post by Xarver on 2010-05-03
I checked and there is nothing wrong with the iso.

---

### Post by grobar87 on 2010-05-03
i check the iso file and got some error...
"phrase not found"...:confused:

---

### Post by grobar87 on 2010-05-03
Now i check the CD a i got this :
"md5sum: /dev/cdrom: Input/output error"
what to do now??

---

### Post by grobar87 on 2010-05-03
anyone help...?

---

### Post by nhasian on 2010-05-03
> **grobar87 said:**
> Now i check the CD a i got this :
"md5sum: /dev/cdrom: Input/output error"
what to do now??

you use a usb-thumbdrive instead? :-k

---

### Post by grobar87 on 2010-05-03
> **nhasian said:**
> you use a usb-thumbdrive instead? :-k

i don't know how to install from usb...:confused:

---

### Post by Xarver on 2010-05-03
My thread is being hijacked. :|

---

### Post by grobar87 on 2010-05-03
> **Xarver said:**
> My thread is being hijacked. :|

[-X:lolflag:

---

### Post by TransitMan on 2010-05-03
Had the same issue with 32 and 64 bit burns on Staples CD's.
Trashed those, and re-downloaded and made sure the md5sum matched, using K3b and a copy of the md5sum from the server I downloaded from and then burned at the slowest speed on Memorex CD's.
Booted into the 64-bit with no problems.

I probably had a bad download from a Canadian server.
Used a different on in the US and got good results. (You milage may vary, but since this is a new release, servers will get slammed and the possibility of errors can happen.)

---

### Post by nhasian on 2010-05-04
> **Xarver said:**
> My thread is being hijacked. :|

sorry, if you are unable to use the liveCD, you can still install with the alternate CD:

[http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-alternate-i386.iso](http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-alternate-i386.iso)

[http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-alternate-amd64.iso](http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-alternate-amd64.iso)

---

### Post by nhasian on 2010-05-04
> **grobar87 said:**
> i don't know how to install from usb...:confused:

use the Ubuntu 10.04 Live CD on another computer.  choose "try Ubuntu without making any changes to the computer" 

once you get to the ubuntu desktop, insert a usb thumbdrive into the computer and go to System-> Administration-> Startup Disk Creator.  

there that wasn't so hard now was it?  Now go back to the original computer and boot off the thumbdrive to install ubuntu.  You may need to change the device boot order to boot from the thumbdrive before the hard disk.

---

### Post by nikefalcon on 2010-05-05
Also get a similar problem.

I downloaded the iso as torrent.
After booting from disk the purple screen is shown and then the new ubuntu logo with the blinking dots underneath; then the screen powers off and nothing happens.
I downloaded it again, this time did a standard download. After booting from the disk, i get the purple screen and then the installer(ubiquity?) crashes and the PC reboots.
Maybe i should try the alternate installer....

Any help would be appreciated.
Thanks

---

### Post by GSF1200S on 2010-05-05
> **nikefalcon said:**
> Also get a similar problem.

I downloaded the iso as torrent.
After booting from disk the purple screen is shown and then the new ubuntu logo with the blinking dots underneath; then the screen powers off and nothing happens.
I downloaded it again, this time did a standard download. After booting from the disk, i get the purple screen and then the installer(ubiquity?) crashes and the PC reboots.
Maybe i should try the alternate installer....

Any help would be appreciated.
Thanks

It would help us to know what video card you have. 

However, you may very well have to use the Alternate cd- no matter what I did, the LiveCD wouldnt work for me. After installing with the alternate cd, I appended xdriver=vesa to the bootline in grub and it booted fine. It depends on your hardware.. beware if you have 2 nvidia cards- a nasty bug makes getting a working system with nvidia drivers a nightmare.

---

### Post by Ducatiboy Stu on 2010-05-05
Try dowmloading from the main ubuntu derver, then burn..

I have had issues with the live CD ( and Alt CD ) not working, basically what I had to do was use a non ubuntu CD , ie SuperGrub or XP first...for some reason, if I used the live CD in an existing running Ubuntu setup it would bypass the live CD...even if I disabled the HDD in the BIOS...

---

### Post by nikefalcon on 2010-05-05
No I don't have a nvidia card. Its intel(G41chipset-embedded); ought to be well supported i guess.....
Anyway, I'll install from the alternate cd. 
Anyone knows how to manually specify partitions in the alternate installer??(i want a separate partition for /home) I have never used the alternate installer before.  :confused:

Thanks

---

### Post by manicmoddin on 2010-06-01
I've given up with the 10.4 boot disk I burnt, re downloaded from different server, if that dont work gonna install 9.10 and the "upgrade" lol

---

### Post by Craig Magner on 2010-06-01
I hate these kind of errors!!

---

### Post by Craig Magner on 2010-06-01
What make of Cd Rs are you using? Could just be a bad batch. Happened to me before with one of the cheaper brands :(

---

### Post by Rubi1200 on 2010-06-01
There are a couple of options to try and workaround the issue of the LiveCD not booting.

First, look at this this option:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

If not, then this might work:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Please note that these are for getting the LiveCD to boot to the desktop. From there, it is possible to install Lucid, but some issues may still occur. These methods have been tried and tested successfully by a number of users, but there is no guarantee. :)

In the first case, use i915.modeset=1 on the boot line. The second option looks like this:

[B]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --


[/B]

---

