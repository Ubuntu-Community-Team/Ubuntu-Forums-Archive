---
title: "Xubuntu won't Install"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by ukmpoam on 2009-03-28
Hi 

I have just downloaded Xubuntu & created an ISO file on CD but when I put the CD in the drive it auto runs but nothing happens. I just get the Windows dialogue box that ask what I would like to open the CD with.

Any ideas on what is wrong?

Thanks

Andy.

---

### Post by Elfy on 2009-03-28
You need to boot with the cd - change bios to do so or if you have a pc new enough to give you a boot option do it there.

---

### Post by RedSingularity on 2009-03-28
Start the computer with the CD in the drive.

---

### Post by ukmpoam on 2009-03-29
Hi

I think that the PC is booting up correctly from the CD as I have tried the same with Ubuntu (rather that Xubuntu) & the OS loaded but not correctly since I have insufficient RAM, hence my trying Xubuntu.

The CD Autoruns & I can see it running through the files but it does not seem to execute on any of them.
 
Any other thoughts?

Thanks

Andy.

> **forestpixie said:**
> You need to boot with the cd - change bios to do so or if you have a pc new enough to give you a boot option do it there.

---

### Post by Elfy on 2009-03-29
So you never actually reach the desktop - sounds like you don't have enough memory, possibly though try starting with safe graphics.

When you get the cd menu up - F4 (or F6) will allow you to use safe graphics if that is causing the problem, also you can add acpi=off - they have all helped me in the past.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Further, as you are going to be installing anyway you could use a partition editor such as [partedmagic]("http://partedmagic.com/download.html") or [gparted]("http://gparted.sourceforge.net/livecd.php") to pre partition the hdd before you start the cd and it would use the swap to help with memory issues.

It would be a help to people if we knew what specs the pc in question had.

---

