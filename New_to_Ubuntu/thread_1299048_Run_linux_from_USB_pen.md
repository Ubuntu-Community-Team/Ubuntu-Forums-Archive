---
title: "Run linux from USB pen???"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by pc999 on 2009-10-23
Hi

Just a simple question, is it possible to use a USB pen to run Linux, I know it is possible to instal from one but it is possible to run from one, like it is a HDD.

This would be great to really try it, spcially on my netbook here sometimes I just what a fast boot.

If Ubuntu cant do it is there any distribution that can?

Thanks in advance.

---

### Post by veli on 2009-10-23
Try out this Ubuntu:

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

But if you want something really, really fast, have a look at Puppy Linux.

---

### Post by jeremyswalker on 2009-10-23
What version of Ubuntu are you using? "System > Administration > USB Startup Disk Creator" will let you create a LiveUSB from a LiveCD image. I'm pretty sure it offers a "persistence" option too, which will save your settings across reboots. If that option is not available, maybe take a look at [Pendrive Linux]("http://www.pendrivelinux.com/").

EDIT: As far as booting from a USB pen drive being fast, I've not experienced this. In my experience, booting from a USB is typically slow compared to booting off the hard drive. Of course, I'm sure this could be different with certain pen drives (or if your hard drive was really slow).

---

### Post by bkratz on 2009-10-23
> **pc999 said:**
> Hi

Just a simple question, is it possible to use a USB pen to run Linux, I know it is possible to instal from one but it is possible to run from one, like it is a HDD.

This would be great to really try it, spcially on my netbook here sometimes I just what a fast boot.

If Ubuntu cant do it is there any distribution that can?

Thanks in advance.


I believe this is the source to look at for persistent installs

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Sarmacid on 2009-10-23
Here you can see how to install grub2 on a usb and have multiple live distros boot from isos [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

### Post by Mighty_Joe on 2009-10-23
> **jeremyswalker said:**
> In my experience, booting from a USB is typically slow compared to booting off the hard drive. Of course, 

The "Live USB" install made with the Live CD USB Creator suffers from the same drawback as the Live CD itself, it is a compressed live file system.  A full install to a USB drive is much faster, but takes up more space, of course.
[How To: Create a Live CD]("http://ubuntuforums.org/showthread.php?t=1193680") covers all the possible USB install methods.

---

### Post by jmundinger on 2009-10-23
> **bkratz said:**
> I believe this is the source to look at for persistent installs

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I used that for a persistent install to a 4 gb flash drive, including downloading and using the 4gb-gb-casper file.  It works just fine on my netbook.  It also runs on my laptop, but it's a crapshoot whether it will use the wireless card in my laptop - it usually doesn't.  Once in awhile - after I have de-activated/activated the wireless card driver - it might work.  It usually doesn't.

I'm still trying to figure out the difference between "persistent" and the live CD - except that persistent appears in the menu when it boots up.  I had assumed that some stuff would be stored on the pendrive and be available from one session to the next.  But, that doesn't seem to be the case.

---

### Post by markbuntu on 2009-10-23
A persistent will save any configuration changes and your personal /home/user stuff. A live will not.

---

### Post by falconindy on 2009-10-23
Running an OS from a USB drive will shorten the lifespan of it dramatically. The flash media used is fairly cheap and can only sustain a fixed number of writes before it gives up. There's a reason that reliable SSDs cost as they do.

---

### Post by Mighty_Joe on 2009-10-24
> **jmundinger said:**
> I'm still trying to figure out the difference between "persistent" and the live CD - except that persistent appears in the menu when it boots up.  I had assumed that some stuff would be stored on the pendrive and be available from one session to the next.  But, that doesn't seem to be the case.

It should save your changes.  There's plenty that can go wrong.  Search the forum and you'll find no shortage of people who are having problems with their persistent Live USB installs.  
IMHO, if you want to use a flash drive for more than experimenting, do a full install.  

[QUOTE=falconindy]
The flash media used is fairly cheap and can only sustain a fixed number of writes before it gives up.
[/QUOTE]
*All* flash memory has a limited number of writes.  Current drives can take a huge number, say, [90 million]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html") for a 1GB drive.  Thanks to wear leveling, the larger the drive, the more writes it can take.  I've been running 9.04 off a 8GB flash drive since it came out without any problems. Of course, I've turned off swap and moved logging to tmpfs to save unnecessary wear. I'll likely grow bored of Ubuntu before this flash drive wears out.

---

### Post by jmundinger on 2009-10-24
> **markbuntu said:**
> A persistent will save any configuration changes and your personal /home/user stuff. A live will not.

mine doesn't

---

### Post by pc999 on 2009-10-26
Hi again, thanks for all the reply I did it using something called Win34DiscImager, it seems really good as I used it without problems and in multiple distros (having hard time to chose).

But I do I get the permanency thing, and BTW those things like turn swap off and such here I go to do it too.

Thanks once more.

---

### Post by irne.barnard on 2009-10-26
I can't seem to see the problem. I've installed Ubuntu 9 (64bit) on a 16GB flash disc ... directly. All I did different is to set it to install the grub onto the flash as well. Then I set the Bios to first try to boot from USB, then HDD. I left my Windowze on the internal HDD. So if I want to run Ubuntu I simply connect the flash and restart, allowing the grub to auto-start Ubuntu. If I want windows ... remove flash & restart. Simple as that!

I've also done the same with my laptop and an 80GB external HDD. However there I made a boo-boo by installing grub on the internal disk. I'm waiting for my courage to grow to the point of trying to "repair" the windows bootstrap, because grub fails if I don't have the external plugged in.

---

### Post by Mighty_Joe on 2009-10-26
> **irne.barnard said:**
> I can't seem to see the problem. I've installed Ubuntu 9 (64bit) on a 16GB flash disc ... directly. 

The topic of conversation is problems with a "persistent" Live USB install, [see here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), not a full install like you did.

---

### Post by kcox5342 on 2009-10-26
I tried the persistent USB thing with 9.04 a while back.  It worked fine on a 2GB stick but not on an 8GB, but I realized the problem was that the directions that I had been following said to move the slider all the way to the right to create the biggest persistence file possible.  With the 8GB stick this file was >4GB which caused it to not get made.

However, I tried running Update Manager with the 2GB stick and 300MB of upgrades, and it failed to install them.  Can one install upgrades with the Persistent approach or does that require a full install?

---

### Post by Mighty_Joe on 2009-10-26
> **kcox5342 said:**
>  With the 8GB stick this file was >4GB which caused it to not get made.

There is a bug in the Jaunty USB Creator that limits the size of the [persistent file to 2GB]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544").  It is fixed for Karmic.

> **kcox5342 said:**
> 
However, I tried running Update Manager with the 2GB stick and 300MB of upgrades, and it failed to install them.  Can one install upgrades with the Persistent approach or does that require a full install?

From what I understand, updates should work except for kernel updates (the Live CD uses a different kernel from the regular Ubuntu distribution).  Don't quote me on that tho.

---

### Post by irne.barnard on 2009-10-26
> **Mighty_Joe said:**
> The topic of conversation is problems with a "persistent" Live USB install, [see here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), not a full install like you did.Sorry about that ... newbie :oops:

---

### Post by Mighty_Joe on 2009-10-26
> **irne.barnard said:**
> Sorry about that ... newbie :oops:

Not a big deal. Just trying to make sure we're all talking about the same thing :)

---

### Post by LewRockwell on 2009-10-26
> **irne.barnard said:**
> I can't seem to see the problem. I've installed Ubuntu 9 (64bit) on a 16GB flash disc ... directly. All I did different is to set it to install the grub onto the flash as well. Then I set the Bios to first try to boot from USB, then HDD. I left my Windowze on the internal HDD. So if I want to run Ubuntu I simply connect the flash and restart, allowing the grub to auto-start Ubuntu. If I want windows ... remove flash & restart. Simple as that!

I've also done the same with my laptop and an 80GB external HDD. However there I made a boo-boo by installing grub on the internal disk. I'm waiting for my courage to grow to the point of trying to "repair" the windows bootstrap, because grub fails if I don't have the external plugged in.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by irne.barnard on 2009-10-27
> **LewRockwell said:**
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.Thanks, I'll give that a try.

---

