---
title: "External drive unmounts - how to remount?"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by thedaylights on 2011-07-08
Sometimes my external hard disk will spontaneously unmount. I don't know why. It doesn't automatically remount when I unplug the USB and plug it back in. Any advice? I'm using 10.04 Lucid.

---

### Post by carverj on 2011-07-08
Have you tried the external hard drive using a different computer or OS? 
dmesg | tail to view the log and investigate possible cause.

---

### Post by thedaylights on 2011-07-08
> $ dmesg | tail
[ 5434.157059] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 5434.281057] usb 2-1: device descriptor read/64, error -71
[ 5434.508052] usb 2-1: device descriptor read/64, error -71
[ 5434.724060] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 5435.137030] usb 2-1: device not accepting address 5, error -71
[ 5435.249071] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 5435.657070] usb 2-1: device not accepting address 6, error -71
[ 5435.657111] hub 2-0:1.0: unable to enumerate USB device on port 1
[ 5641.279274] __ratelimit: 22 callbacks suppressed
[ 5641.279280] scim-bridge[1423]: segfault at c ip b77cbecc sp bf9c26e8 error 4 in libscim-1.0.so.8.2.4[b7773000+c2000]

No I've only used it with my ubuntu system. It's a new 2TB Western Digital MyBook. It was rather cheap compared to other 2TB drives.

I am connecting it to my laptop via a USB hub (a good one, I think).

---

### Post by dasan on 2011-07-08
give a try with file system check using fsck

---

### Post by thedaylights on 2011-07-08
> **dasan said:**
> give a try with file system check using fsck

$ fsck
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)?

---

### Post by dasan on 2011-07-08
Unmount the file system.

if your file system is ext4 
use fsck.ext4 "drive name" to check it

This is to fix file system errors

---

### Post by thedaylights on 2011-07-08
Dasan, I don't know what the name of the filesystem is. It is NTFS. When I plug it in, it shows up as MyBook. So should I type this?

$: fsck.ntfs /media/MyBook

But I'm not sure if it's mounted as sda2 or what. I never figured out why there are two names for my disk drive, as in sda2 and MyBook.

---

### Post by jtarin on 2011-07-08
[There's a ton of post on MyBook]("http://ubuntuforums.org/search.php?searchid=81877476")......I think they let it out of the gate too early.

---

### Post by thedaylights on 2011-07-08
> **jtarin said:**
> [There's a ton of post on MyBook]("http://ubuntuforums.org/search.php?searchid=81877476")......I think they let it out of the gate too early.

I read through the first page of posts and none of them deal with my situation. Really I just want to know how to force remount the drive.

Back in the old days I could just sudo mount -a and all my plugged in USB drives would mount. But it doesn't work now. :(

I totally appreciate the rule about searching through the forums for previously answered questions. But to be honest, I have almost never found that to be helpful for my ubuntu problems. I tend to google search for a solution before consulting ubuntu forums. And then if I can't solve it on my own I come here, read 11 pages of many different ways of solving a problem that is tangentially related to mine, and end up frustrated. Ubuntu forums works best when someone takes me step by step through the problem to resolution. Which is a lot to ask, I know.

The annoying thing is that I'm the guy that answers tech problems for my family on their windows systems, which I haven't used in years, because I'm willing to do some legwork. 

/rant over
[SIZE="4"][B]
tl;dr
Does anyone know how to force mount an external drive? sudo mount -a is not doing it for me.[/SIZE][/B]

---

### Post by coffeecat on 2011-07-08
> **jtarin said:**
> [There's a ton of post on MyBook]("http://ubuntuforums.org/search.php?searchid=81877476")......I think they let it out of the gate too early.

The "MyBook" brand has been used by Western Digital for a few years now and there are several different lines which are "MyBooks". The ones with pseudo-CDROMs have been problematic with both Linux and MacOS, but that doesn't sound like the issue here. I have used MyBooks without any problem. I think the "ton" of posts simply reflects the large number of MyBooks that are out there. Go into any retail computer store (in this country at least) and you will see MyBooks lining the external storage shelves. They are very popular.

> **thedaylights said:**
> 
$: fsck.ntfs /media/MyBook

No. That won't work. There is no effective NTFS filechecker in Linux - not even ntfsfix, which simply schedules a chkdsk in Windows for when the drive is next used in Windows. I think a filesystem check is a good idea, but I doubt it's the problem here. If you want to do a filesystem check, you need to use Windows for NTFS.

---

### Post by jtarin on 2011-07-08
[Here's one from the other day]("http://ubuntuforums.org/showthread.php?t=1794918&highlight=mybook")...about mounting and fsck.

---

### Post by dasan on 2011-07-08
> But I'm not sure if it's mounted as sda2 or what. I never figured out why there are two names for my disk drive, as in sda2 and MyBook.
You can always check it with 
sudo fdisk -l

And two names are not there. One is device name and other is mount point name.

finding out from sda 1,2,3 is more difficult that is the reason why we name partitions and keep but device will be always the same.
for ex you can mount /dev/sda2 to any folder and you can give any name too.

And as the other one pointed out if it is ntfs you should go to a win machine and fix it..

---

### Post by thedaylights on 2011-07-08
Ok so it seems like I should be looking for some virtual disk software and deleting that when I hook it up to a windows machine.

I'll get to that. In the meantime, I ran lsusb and my results were:

> $ lsusb
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


It is currently plugged into a usb port.

---

### Post by jtarin on 2011-07-08
> **thedaylights said:**
> 
I totally appreciate the rule about searching through the forums for previously answered questions. But to be honest, I have almost never found that to be helpful for my ubuntu problems. I tend to google search for a solution before consulting ubuntu forums. And then if I can't solve it on my own I come here, read 11 pages of many different ways of solving a problem that is tangentially related to mine, and end up frustrated. Ubuntu forums works best when someone takes me step by step through the problem to resolution. Which is a lot to ask, I know.

The annoying thing is that I'm the guy that answers tech problems for my family on their windows systems, which I haven't used in years, because I'm willing to do some legwork. 
Don't get me wrong I wasn't suggesting you do any searching....far from it....I wanted you to see what your up against. In some situations....not doable. Just trying to be realistic.:p

---

