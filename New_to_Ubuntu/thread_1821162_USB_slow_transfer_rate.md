---
title: "USB slow transfer rate"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Bitter Jane on 2011-08-08
Hey, folks. I have done a bit of research before posting a new thread, but it had no satisfactory result (or not one easy enough for a noob like me), so here I am.
I can't make my USB flash drive transfer data at a reasonable speed. The transfer rate is about 100 KB/s and that's a pain, since I have to copy files adding up to several GBs. Once (but only once) the speed went up to 7 MB/s and it was something rather "mysterious", I haven't done anything to cause that (or so I think).
System Settings> Disk Utility points that the USB drive is recognized as 2.0 and the connection speed is 480.0 MB/s, not 12 or any other value. 
The only result that rmmod ehci_hcd has is the following error: 
ERROR: Module ehci_hcd does not exist in /proc/modules
So I can't unloadi ehci_hcd and uhci_hcd and reload them. 
And I ran out of applicable ideas, any help would be much appreciated.  
PS: I'm using Natty and it's my first non-Windows experience, so I can't say whether or not it would've worked well with the previous versions.

---

### Post by LowSky on 2011-08-08
This is a long standing bug in Linux. The reason it is long standing is because its almost a phantom. Many of the developers cannot duplicate it and unfortunately it is usually seen by new comers who have no idea what to report. the reason it so rare is because somehow very few linux users are placing gigabytes worth of data onto a flash drive. If you want to see faster results add the files slowly it seems to say faster that way.

I filed a bug a few years ago about the same issue. I noticed the problem effected only my AMD powered machines (athlon64 in my experience). It seems to only effect USB thumb drives, hard drives connected by USB seem to work fine.

---

### Post by Bitter Jane on 2011-08-09
Interesting pieces of information. My laptop, however, is based on Intel. While I don't have the possibility to test an external hard drive at the moment, it could be an alternative, as well as personal file storage services (to an extent, obviously). 

I found out quite a few people had problems even with all their usb peripherals, so I'm lucky! 

Also, I was wondering whether a kernel upgrade or (rather) downgrade could be of any use. On another thread related to the same issue, an Ubuntu user offers a more detailed description.

> I can vouch that this works, but for me (and my laptop) only kernel 2.6.26-16 in a fresh 8.04 Hardy Heron install works. If you do a search of my posts, my problems didn't start until kernel 2.6.24-19, an update I got for Hardy sometime last summer. (June or July, I think.)

I have three versions of Ubuntu that I ordered CDs for (Feisty, Gutsy, Hardy) that all have 'normally' (optimally?) functioning USB until the kernel is upgraded.

I'm not that dependent of flash memory, but...Would doing such a downgrade bring many disadvantages?

---

### Post by hakermania on 2011-08-09
Ok, same here :)
I've seen tons referring to this bug, but who knows why... Specifically, I've seen the speed to start at 25 Mb/s and end up 50-100kb/s :/

---

### Post by Bitter Jane on 2011-08-10
And I have another noob question. If plugging in the USB flash drive is reported as "new high speed USB device using **ehci_hcd** and address 6" (dmesg-- and notice it's high speed, not full speed), why can't I find the module in /proc/modules and by using lsmod?

---

### Post by androidfan on 2011-09-20
I just thought I would post that this same problem just started to happen to me only a few days ago.  It doesn't seem to be related to upgrading (as some people have suggested in other threads) because there were no problems in natty until 3-4 days ago (and I upgraded right away).

As have many other people, when I begin transferring files it starts off quickly, but a short while later, ranging anywhere from 50MB to 350MB (after a few non-scientific tests) into the transfer,  it slows not just the transfer, but the entire computer down to a crawl.  I have now reproduced it on 3 different flash drives (4GB, 8GB, and 16GB) and have not experienced the same with an external USB hard drive attached to the same port (as previously mentioned).

Anyway, the problem began after I did many of the things listed on this website: [Things to Tweak/Fix after installing Ubuntu 11.04 Natty Narwhal]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html").  I did them all (the ones that I did anyway) in a row, so I don't know which (if any of them) may have triggered something to cause this.  Does anybody with more knowledge have any ideas?

And if it helps at all, I am running 64-bit Ubuntu 11.04 Kernel 2.6.38-11-generic with Gnome 2.32.1 on an older ThinkPad T400.

---

### Post by SherylC on 2011-10-03
> **androidfan said:**
>   I have now reproduced it on 3 different flash drives (4GB, 8GB, and 16GB) and have not experienced the same with an external USB hard drive attached to the same port (as previously mentioned).

I'm here to lament this with everyone else. This did start not too long after I upgraded to Natty. Transfer to my external USB hard drive is fine, but to any other device it lumps along at around 400kb tops ... I'm moving some mp3s to my phone right now... 2.7 gb is going to take almost 2 hours .... zzzzzzzzzzzzz

---

### Post by jdorenbush on 2011-11-19
I've been having this problem for several Ubuntu releases now (currently using 11.04) and I still haven't found a solution.

My files transfer at a fairly reasonable speed up until the very end when it reaches '0 seconds remaining' and it stays at that position for a minute or two, sometimes longer. The slow transfer speed only occurs when _writing_ to a USB drive, and I don't experience the problem on my USB external harddrive, _only on USB flash drives_.

:confused:

---

### Post by J V on 2011-12-01
Done some sleuthing myself:


[list]
[*]**Starts off fast, then goes slower**
This is because when mounted with async it will write to the cache, when the cache is full you see the "Real" write speed
[*]**Missing ehci_hcd module**
Nowadays this module is compiled into the kernel while others like usbhid aren't
[/list]


Could we all list our uname -m?

It might be an x86_64 specific issue...

---

### Post by jdorenbush on 2011-12-02
> **J V said:**
> 
Could we all list our uname -m?

It might be an x86_64 specific issue...

x86_64

---

### Post by Kg001 on 2011-12-03
This Bug has me tearing my hair out. 

It has been an issue for me for many years on two different machines & all distros since 8.04. I find it hard to accept that after all this time it remains unsolved.  & the comments by some experienced users are really, very annoying. The initial 8.04 system that had the issue was an AMD Athalon system. However the functionality of Ubuntu has lead me to gradually transfer ever thing to the current machine Resulting in a monster that Linux handles with grace & aplomb. 

MY Issue is that on _any_ Fat 32 USB drive, large transfers of either large files or many small files. start at high speed the go into a stop small burst, stop small burst, mode. it affects all USB Thumb drives but the larger Newer drives will transfer bigger lumps faster before stalling e.g. an older 2G thumb drive will stall at approx 200meg & the new 32G Lexar drives pull down 480meg before stalling connecting the drive to a windoze virtualbox VM results in a steady transfer at USB1.1 speeds :( Usb hard drives fat32, NTFS, RIESERFS, EXT3 & EXT4 are unaffected. 

Current system AMD PHENOM-2 X6 running 10.10 x64, 8G ddr2 memory, roughly 8 tb storage (1/3 on usb) with a copy of XP running SCADA Data collection & analysis 24/7 as a Virtual machine. A sweet heavily loaded system with one major issue that is really starting to bite me in the but. :-x God forbid I have to migrate this monster back to Windoze!!!

Looking around I have come across many dozens of reports of this issue & no hint of a solution or indeed any real attempt to solve it.

While I am definitely no Linux Guru I certainly qualify as a long term power user & am not scared to dive in at the command prompt if someone has the patience to spell out what they need me to do or test, to get some traction on this issue. I am quite prepared to do what ever is needed & in my power to do.

Cheers all KG001

---

### Post by rabinnh on 2011-12-20
Add me.  X86_64, 11.04.  It was fine until the update to 11.04 (Ubuntu user since 8.04).  I am currently copying 100MB to a USB stick and it is taking forever.  The rate is 146.4KB/sec.  If I use dd to write an image to the same stick, it's as fast as ever.  This indicates that it may be a file system issue with FAT32.

---

### Post by kristianz on 2012-02-05
Same here. It starts out at 30 MByte/s until cache fills up, then it goes down to a few hundred kByte/s. What's even more annoying is that the whole system stops to a crawl: Every 5-10 seconds almost everything freezes for a couple of seconds. When transfering a few GBs will take me all day, having the computer freeze on me that whole period makes it annoying as hell. (Yes, it's happening as I'm writing this.)

Natty, AMD64, all USB ports, all thumbdrives..

---

### Post by techvish81 on 2012-02-05
it has happened with me when i was using an old usb thumb drive but has never happened in any other newer thumbdrives , since ubuntu 10.04 to 11.10. when it happened , i was on ubuntu 11.10 x64.

---

### Post by J@n on 2012-02-06
Thank god I am not the only one! I re-installed Minty 12 (Ubuntu with a green look-n-feel) and discovered that copying to a USB thumbdrive was slow as molasses:(

Tried different thumb drives (2, 8, 16 GB formatted to EXt2, Ext3, Ext4, NTFS and FAT32) and all "stopped" working after the first file.

Tried OpenSUSE 12.1 KDE from a live CD yesterday and no problem there. So no hardware issue or BIOS setting as fas as I am concerned but definitely in the Ubuntu distro.

Note: I have no intention to switch to OpenSUSE. It was merely for testing purposes.

Hope someone can do something about it.

Greetz,

J@n

---

### Post by philinux on 2012-02-06
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)

Please click on the affects me button. And post a comment with info not just a "I've got this too."

---

### Post by J@n on 2012-02-06
Hi philinux,

Thank you for the tip. Just added my problem to the list (of 218:confused:).

I hope this will get solved in Ubuntu (hence it will be solved in Minty too!)

Greetz,

J@n

---

### Post by kristianz on 2012-02-08
According to the bug-tracker linked to, the problem has been fixed in the latest kernels (3.3). Next Ubuntu release will use kernel 3.2, so it remains to be seen when this bug no longer affects us Ubuntu/derivatives users.

---

### Post by mutex023 on 2012-04-24
For the time being I've a workaround for this - 
[http://ubuntuforums.org/showthread.php?t=1963360](http://ubuntuforums.org/showthread.php?t=1963360)

---

### Post by NikTh on 2012-04-25
Until they fix this bug , you can try **ionice** command to copy quick your files. 
**Example **
1) File game_of_thrones.avi (favorite series) its on /Downloads dir 
2) my usb flash drive kingston mounted on /media/kingston 
Then execute the command **cp **with **ionice** together 
```
ionice -c 2 -n 0 cp /Downloads/game_of_thrones.avi /media/kingston
```

---

### Post by SuperMau on 2012-06-21
I have no clue to why the bug report states that it has been fixed in newer kernels. I am on Precise 12.04 and have had this problem since the beginning. The problem persists all the way to kernel 3.5. I have noted that it is worst on pen drives with FAT32.

I will try to make some tests with usbmon and report back ([http://www.mjmwired.net/kernel/Documentation/usb/usbmon.txt](http://www.mjmwired.net/kernel/Documentation/usb/usbmon.txt))

Till then my work around has been formating my pendrives with NTFS...

---

### Post by sirpy on 2012-07-26
the solution found here worked for me
[http://ubuntuforums.org/showthread.php?t=1867460](http://ubuntuforums.org/showthread.php?t=1867460)

instead of 3mb/s it now copies at 9mb/s

---

### Post by truant on 2012-08-01
Every single Ubuntu install I've had over loads of different machines has suffered from this problem, and I've been using Ubuntu since day one.

My newest laptop has USB3.0 sockets/hub and transfers to/from assorted USB2 flash drives at 30MB/s in Windows, ten times less than that for the same devices in Ubuntu.  Devices which Ubuntu reports are connected at the full 480Mb/s.  I get the 100% copy complete, wait a few minutes before actually finishing thing too. I don't have any usb3 devices to test with, yet.

For unrelated reasons I'm running a daily build kernel from last week, 3.5.0-999-generic #201207280406 on AMD64 hardware and it's not fixed there.

Same problem in Debian Testing.  Booted into a Fedora live environment a moment ago, blisteringly quick speeds there.  So if it's the kernel, it's Debian/Ubuntu's build thereof.

I'm going to try adding pci=acpi to my boot options in a moment, see if that helps.

[ edit: on my system (Toshiba L830-114) pci=acpi is not a valid boot option and does nothing but generate an error ]

---

### Post by KaizerLinux on 2012-08-01
Strangely enough, I've had the complete oposite experience! Though my transfer speeds to USB drives in Ubuntu are a bit unstable, they are significantly faster than in Windows 7 :P

---

### Post by truant on 2012-08-02
Yeah, reading through the various (and numerous!) usb-speed related bug reports there's so much variation.  The developers all try to help, but the overall conclusion seems to be it's not an easy thing like a bit of missing code in ehci_hcd module, it's one of those weird hardware lucky dip things.  

Some combinations of hardware just freak out and go slow, and it's really hard to reproduce - thus making it very hard to fix.

I'll keep plugging away with the bug reports.

---

### Post by jeroen.bakker on 2012-12-12
Next did really help me. I changed the line in fstab from:
# try usb:
/dev/sdb1 /media/usb0 auto noauto,rw,noexec,users,utf8,nodev,sync, noatime,nodiratime,uid=1000,gid=1000,umask=0022 0 0

into:
# try usb:
/dev/sdb1 /media/usb0 auto noauto,rw,noexec,users,utf8,nodev,noatime,nodiratime,uid=1000,gid=1000,umask=0022 0 0

Copy rate increased to somewhat 3 MB/s

---

