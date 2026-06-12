---
title: "Installation just won't work...."
date: 2011-01-11
forum: New to Ubuntu
---

### Post by brianrobles204 on 2011-01-11
Hi,

I've been trying to install Maverick on my PC for a few days now. I'm running Windows 7 right now, and I'm using a Lenovo Ideapad. 

The problem is when I first booted the Live demo through my USB, I tried to install it alongside Windows for the time being. The Live demo worked, but when I tried to install it, there was an error when it reached, like, 75%. I forgot what the error said, but it had something to do with a file not installing due to a dirty harddrive.
 
After that, when i tried to boot my Windows, this black check thing started to check my disk, saying something about NTFS~ after it finished checking, I started Windows normally (although it was a bit slower).

Starting windows then went back to normal and everything, but when I tried to install ubuntu again, it won't even reach the part where I get to choose how to install it. It loads indefinitely after I clicked forward on the part where it tells you to have enough memory, to be plugged in, and to be connected to the internet :|

Trying it in Wubi, it also stopped loading on 0%, saying formatting swap space in partition # 1 of hosts/ubuntu/disks/swap.disk

:| I really want ubuntu, coz I want to be a FOSS advocate, so could someone tell me what's wrong with my computer? Sorry for the long post, but I just wanted to be specific~:confused:

//edit: opening My Computer, it says '11.6 gb free of 93.1 gb', but this is after I tried installing ubuntu for the first time. I can't remember if this is any different from before trying to install ubuntu. I don't think this is much of a problem, is it?

---

### Post by mistypotato on 2011-01-11
Whatever the case, it sounds as though you may have errors on the hard drive or not enough space maybe.

Try running chkdsk on the hard drive to correct any errors before trying to install Ubuntu.

Tell me more about the PC you're trying to install this on....
Hard disk size
Free space available

You might also try booting with the Ubuntu Live CD Disk in the CD drive rather than through USB...
If you have a CD/DVD drive that is.

---

### Post by mastablasta on 2011-01-11
it could be that your download was corrupted. check the md5sum to verify that:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Quackers on 2011-01-11
How many primary partitions is Windows using on your hard drive? Have a look in Windows disk management screen.

---

