---
title: "installer crashes"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by bindlestiff7 on 2011-01-26
Hi All,
I've been wanting to try out Linux but didn't want, at this stage, to install it and dump XP (I'd love to of course).  I tried the Live CD and liked what I saw so decided to install Ubuntu to my 60GB Iomega external hard drive (USB).  I expected it to be slow but in this case that wouldn't be a problem as I'm only playing at the mo'.

Problem:  each time I try to install, I get as far as time zone/keyboard selection etc but then I get a Installer Has Crashed message every time.

quote
input/output error during write at /DEV/SDB
Installer has crashed
unquote

Suspecting that NTFS may be involved, I reformatted the drive to FAT32, partitioned in two equal partitions.

Same result - installer crashes at the same point.

Every help page that I read seems to assume that I have successully installed the system and gives me lists of commands to enter in terminal mode - a terminal that I don't yet have.

Can anyone advise on this one please?

Ian

---

### Post by Habeouscorpus on 2011-01-26
Well, to clarify the error message, it's saying there's an error writing to the USB. What option are you selecting? Specify partitions, erase and use entire disk, or Install alongside?

---

### Post by Smart Viking on 2011-01-26
It sounds like a faulty CD, burn a new one, preferably as slow as possible.

---

### Post by Quackers on 2011-01-26
Did you check the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by bindlestiff7 on 2011-01-26
> **Habeouscorpus said:**
> Well, to clarify the error message, it's saying there's an error writing to the USB. What option are you selecting? Specify partitions, erase and use entire disk, or Install alongside?

The entire disk, two partitions, is just going to handle Ubuntu.

---

### Post by bindlestiff7 on 2011-01-26
> **Quackers said:**
> Did you check the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I checked the page that you linked above - when it says 'terminal' does it mean a terminal in Linux, or does it mean Telnet as in DOS?

---

### Post by Smart Viking on 2011-01-26
> **bindlestiff7 said:**
> I checked the page that you linked above - when it says 'terminal' does it mean a terminal in Linux, or does it mean Telnet as in DOS?
Terminal in linux, the bash shell. It's a place to launch commands to change the system, it is much more capable than cmd.exe in windows.
EDIT: Or.. usually the bash shell, that's what you'll most like be using.

---

### Post by beew on 2011-01-26
Interesting. I experienced a similar problem a few days ago and still haven't figured out why. I got as far as copying files and the installer crashed with an input/output error saying that maybe the medium I was installing to was corrupt or the machine was too hot,or the iso was bad, none were true because I was able to install later but with the live usb prepared differently.

[URL="http://ubuntuforums.org/showthread.php?t=1671408"]
http://ubuntuforums.org/showthread.php?t=1671408[/URL]

---

### Post by bindlestiff7 on 2011-01-26
> **Smart Viking said:**
> Terminal in linux, the bash shell. It's a place to launch commands to change the system, it is much more capable than cmd.exe in windows.
EDIT: Or.. usually the bash shell, that's what you'll most like be using.

Difficult, I can't get Ubuntu to install so that I can get to a Terminal............

---

### Post by Smart Viking on 2011-01-26
> **bindlestiff7 said:**
> Difficult, I can't get Ubuntu to install so that I can get to a Terminal............
You can use it when you are in the live CD. There are ways to check md5sum in windows too but i have no idea how.

---

### Post by bindlestiff7 on 2011-01-26
> **Smart Viking said:**
> You can use it when you are in the live CD. There are ways to check md5sum in windows too but i have no idea how.

Any chance you can give me a quick heads-up on how to check it in Live CD mode?

---

### Post by Smart Viking on 2011-01-26
Boot it up and enter into the terminal(replace the path:
```
cd /media/where-windows-drive-is-mounted/location/to/ubuntu.iso
```
then
```
md5sum ubuntu.iso
```^ The filename is not going to be ubuntu.iso, replace that with the real filename.

And that's it, after that compare it to the mdsum that is on the page you downloaded ubuntu.

---

### Post by bindlestiff7 on 2011-01-27
Thanks for the help from you guys.  The problem was solved when a friend who was suffering the same Ubuntu problems called me with the solution.  He had discovered that Kubuntu had a disk verification routine in the Live CD start-up menu.  So I downloaded Kubuntu and, after running the disk verification, it installed first time.  I'm not sure what the differences between the two distros are, but not a problem as I need to start somewhere.
Thanks again.

Ian

---

