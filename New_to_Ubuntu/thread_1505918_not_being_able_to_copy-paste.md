---
title: "not being able to copy-paste"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by fremantle on 2010-06-09
using ubuntu 9.10 karmic

whenever i try to copy something from one directory to another, as soon as i clik :paste: both of the windows get closed.

---

### Post by fremantle on 2010-06-09
im the only one whos threads are being ignored

---

### Post by nhasian on 2010-06-09
please wait 24 hours before bumping a thread.

make sure you have write privileges to the destination folder when copy/pasting. 

> **fremantle said:**
> using ubuntu 9.10 karmic

whenever i try to copy something from one directory to another, as soon as i clik :paste: both of the windows get closed.

---

### Post by fremantle on 2010-06-09
> **nhasian said:**
> please wait 24 hours before bumping a thread.

make sure you have write privileges to the destination folder when copy/pasting.
yes i do. even in root the same thing happens.

---

### Post by nhasian on 2010-06-09
what happens if you move or copy the file in a terminal?

---

### Post by Metrop021 on 2010-06-09
are you using right click copy > paste. or control + c and control + p

---

### Post by fremantle on 2010-06-09
> **nhasian said:**
> what happens if you move or copy the file in a terminal?
i tried but to no avail. maybe i used the wrong command, can u gimme the copy-paste terminal command?

---

### Post by fremantle on 2010-06-09
> **Metrop021 said:**
> are you using right click copy > paste. or control + c and control + p
both. same result. the windows disappear

---

### Post by nhasian on 2010-06-09
[Usage Summaries and the Copy Command]("http://rute.2038bug.com/node7.html.gz#SECTION00740000000000000000")
[URL="http://linuxcommand.org/lts0050.php"]
Manipulating Files[/URL]

> **fremantle said:**
> i tried but to no avail. maybe i used the wrong command, can u gimme the copy-paste terminal command?

---

### Post by fremantle on 2010-06-09
omg... can anyone plz help mee!!!!

---

### Post by 4Orbs on 2010-06-09
I would be interested in knowing where you are copying from and where you are trying to paste the file. Are you trying to paste the file into a folder on your Windows partition? Are you pasting a file from ext4 partition into a folder on NTFS partition? A little more info would be helpful.

Are you using a desktop theme that was not included with Ubuntu. Sometimes 3rd party themes can cause similar problems.

---

### Post by fremantle on 2010-06-09
hmm,,, im pasting FROM my ubuntu partion to the windows NTFS partition. the theme is a 3rd party theme (ambience-x-dust). but it also occurs when i paste to my dextop and sometimes in the ubuntu filesystem.

---

### Post by garvinrick4 on 2010-06-09
Try installing NTFS Configuration Tool.

Just use your Ubuntu Software Center.

---

### Post by garvinrick4 on 2010-06-09
rick@rick-laptop:~$ aptitude show ntfs-config
Package: ntfs-config
State: installed
Automatically installed: no
Version: 1.0.1-3ubuntu5
Priority: optional
Section: universe/admin
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 864k
Depends: ntfs-3g, python-support (>= 0.90.0), python2.6, udev, python-glade2
Description: Enable/disable write support for any NTFS devices
 This program allow you to easily configure all of your NTFS devices to allow
 write support via a friendly gui. For that use, it will configure them to use
 the open source ntfs-3g driver. You'll also be able to easily disable this
 feature.
Homepage: [http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

---

### Post by fremantle on 2010-06-09
ok. but i'll need some help with the gui. stick around ;)

---

### Post by fremantle on 2010-06-09
i cant select "enable write support for internal device" ??!

---

### Post by nhasian on 2010-06-09
did you follow the instructions in my last post on how to copy a file?  Can you post the command you used as well as the output of it?

---

### Post by fremantle on 2010-06-09
i did a restart and now im facing the returning-gdm issue ... cant login

---

### Post by fremantle on 2010-06-09
goddammit. i wish using linux was less painful

---

### Post by 4Orbs on 2010-06-10
It sounds highly possible that you installed Ubuntu from a badly burned disk or corrupted download. Did you check your install disk before installing the system? (the md5sum)

---

### Post by nhasian on 2010-06-10
> **fremantle said:**
> goddammit. i wish using linux was less painful

its not.  you just have to relax and follow our instructions (yes sometimes that includes reading) and answer some questions so we can help get you up and running.

you mentioned you were still running 9.10?  Any reason you haven't upgraded to 10.04?  a fresh install of 10.04 might be a good idea at this time.  You did not mention if you were using wubi or have ubuntu installed on its own partition.

you should run a scandisk from windows on your NTFS partitions as well as fsck from a linux boot disk on your EXT3/4 partitions.  If your doing a fresh install of ubuntu then you dont need to do the fsck.

---

