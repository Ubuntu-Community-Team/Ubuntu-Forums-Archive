---
title: "Formating my Windows Partition"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-11-21
I dual boot XP and Ubuntu. But...I want to get rid of my regular XP install, and install Windows XP Pro Performance Edition(basically just a smaller version of XP). I want to format the Windows partition and get rid of XP, and put Pro Edition in its place.

So how exactly would I go about doing this?

I've got gparted installed. So is this as easy as starting up Gparted, selecting my NTFS partition, and click format?

The thing I'm a little hesitant on, is when I right-click my NTFS partition and click on Format, it gives me options to what I can format the partition to. Do I just format the partition to FAT16?

After I get this partition formatted, how exactly do I install this new XP? Obviously I have it burned to a disc. So when I restart the computer with the disc in an installer should pop up. The installer should give me an option to install to the NTFS partition, right?

Any info you can give me will be appreciated. Thank you.

---

### Post by Jon Monreal on 2009-11-21
The legality of "Windows XP Pro Performance Edition" is highly questionable.

However, if one were installing Windows XP from CD, they could simply boot the XP CD and use that to remove and then create a new partition and format it as NTFS.

If I were you, I would stick with XP instead of some possibly broken hacked-to-pieces OS. Also consider installing XP in a VM on top of Ubuntu.

---

### Post by SkyNet2029 on 2009-11-21
you need to boot off of the installer disc and format the partition with it's formatter. The gparted format to ntfs will not be recognized by xp. I also agree with the other poster in that using a hacked up edition of xp pro does not seem to be the best use of one's brainpan.

---

### Post by h8uthemost on 2009-11-21
Thank you for the suggestions guys. I'll go ahead and use the installers formatter to do this.

And my brother in law has this installed, and I've spent some time with it. And I think this edition is pretty excellent. It's XP, it just has a bunch of the crap taken out. And since I only use Windows for the Zune software, then I really don't need all that other junk.

Thanks again.

EDIT: Also, installing as a VM, that seems way too complicated for me. Plus I only have a 70GB internal drive, and 512MB of RAM. So I don't even know how well VM on my computer would work. That's why I'm just wanting a tiny XP.

---

### Post by Jerry N on 2009-11-22
Quote:  *"The gparted format to ntfs will not be recognized by xp"*

_Not correct_ - Windows 2000, Windows XP and Win 7 RC will all install to an NTFS partition created by gparted (I use Partition Magic for this).  Been there, done that!  Gparted can also be used to modify the size of an XP partition, if you are sure you are not wiping out any files in the upper part of the drive space.

Jerry

---

