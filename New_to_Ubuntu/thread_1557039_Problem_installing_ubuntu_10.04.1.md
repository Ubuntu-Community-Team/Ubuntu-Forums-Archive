---
title: "Problem installing ubuntu 10.04.1"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Torinogut on 2010-08-20
Hello

I have downloaded and failed to install ubuntu on my laptop twice now. I am running windows 7 home premium 64-bit.

First I tried burning a DVD. It got stuck on the ubuntu loading screen (the one with the red and white dots) wether I chose install or try live.

The second time around I tried using unetbootin (with the same ISO), and it got stuck on the same loading screen.

My computer is a [MSI GX740]("http://eu.msi.com/index.php?func=prodnbspec&maincat_no=135&cat2_no=271&cat3_no=&prod_no=1999")

So I am wondering where I can find the 10.04.1 md5sum/hash and if there is a known compability issue with any of my hardware. 


Torinogut

---

### Post by moody_mark on 2010-08-20
Hi, have a look here for hardware

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

This page is a useful resource for buring ISOs and has a link to a place where you can find md5 for the ISOs

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Ive seen this problem a couple of times on a machine which I knew would run Ubuntu, and indeed other distros of linux just fine. It was a badly burnt CD, or one that hadnt completed. I would lean towards the source of your problem being either a incomplete / bad burn, or a incomplete / bad ISO image.

Hope this helps

---

### Post by Torinogut on 2010-08-20
Thank you for your reply. I may be blind, but I can't seem to find the md5sum for 10.04.1 or is it supposed to be the same as 10.04?

---

### Post by moody_mark on 2010-08-20
Hey, no problem. Try this page here and scroll down

[http://releases.ubuntu.com/10.04.1/](http://releases.ubuntu.com/10.04.1/)

You'll see a link to md5sums

[http://releases.ubuntu.com/10.04.1/MD5SUMS](http://releases.ubuntu.com/10.04.1/MD5SUMS)

That should be what you need

---

### Post by Torinogut on 2010-08-20
The md5sum checks out. I formatted the partition i tried to install on previously and used wubi. And it got almost to the end before I had an error. Maybe this can shed some light on why I can't install ubuntu. only the last paret of the log is included as the file was to big to attach.

---

### Post by moody_mark on 2010-08-20
Hi, Ive never used wubi, the problem you have installing it could well be related or another reason. If you have already burnt a new CD then try booting just into the live session (try without installing). Try the CD on another machine if you have access to one to verify thats still not the problem.

If you still have issues and verify the CD / DVD is ok, then I would recommend you try another distro, such as crunchbang or mint, or even fedora just to see if its perhaps something specific to Ubuntu, and not your machine. I used to use Knoppix just on a CD as a "get out of jail free card" a while ago to help revive dead windows machines to recover data.

---

### Post by pqwoerituytrueiwoq on 2010-08-20
Just to make sure you nothing goes wrong for you...
i head somewhere you should use win 7 to shrink the partition before installing ubuntu cause gparted can mess 7 up (use disk management)
you should defrag before shrinking a partition

---

### Post by Torinogut on 2010-08-20
Live Cd worked fine on another computer. I'll try a small distro to find out if I can boot this computer at all with linux

---

### Post by c.c.rascal on 2010-08-20
hi looking for some help with ubuntu 10.04 ive bein booting off of a usb onto a dell inspiron while in ubuntu all seems well the problem seems to b when booting back off of my hard drive into windows 7 again i get a blue screen error
i tyred it on another comp it was fine so then tryed again on the dell and the same results now im wanting to try ubuntu but need to sort this out first any help would be gratefull

---

### Post by Hawhaw1 on 2010-08-20
I am having the same problem with 10.04.1.
It will reach the Ubuntu loading screen (with 5 dots) and stay there. No sound or anything from the pc either so its not loading anything.

---

### Post by Torinogut on 2010-08-21
Just wanted to notify that I had the exact same problem with mint. And that Opensuse live CD worked, albeit only in safe mode, and I couldn't get into the OS itself after it was installed. So it seems my hardware is a bit new for linux

---

