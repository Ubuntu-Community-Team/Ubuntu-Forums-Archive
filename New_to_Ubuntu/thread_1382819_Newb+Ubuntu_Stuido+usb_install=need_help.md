---
title: "Newb+Ubuntu Stuido+usb install=need help"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by RedEar on 2010-01-16
Okay,
As stated, I am a total Linux newb. I tryed to search around and use fixes people have posted, but I either do not understand and so they do not work, or I have a different problem. So please try to help me learn.

I have a Dell Inspiron mini 10v running windows xp.
I would like to partition and dual boot ubuntu studio. 
I atempted to use a usb stick; a sandisk cruzer 4gb. I formated and took everything off of it and then installed the disk image ubuntustudio-9.10-alternate-i386
I used Live USB creator
I changed the Bois (is that right?) to boot USB. Ubuntu Studio shows up on the USB when I boot it. But it either says it can not find the DVD or it gives me the "can not find /casper/vmlinuz disc image"

I have tryed the comand cdrom-detect/try-usb=true nothin...
I tryed vmlinuz initrd=initrd.img  nothin...
I would try moving folders but have no idea how to or what I am doing.

Please help. I get the feeling I will love ubuntu and use ubuntu studio a lot if only I could get it on my computer...

Thanks

---

### Post by warfacegod on 2010-01-16
I would not use the alternate .iso, it doesn't have any GUI and that sounds like what you are running into. Try the regular .iso

---

### Post by RedEar on 2010-01-16
Thanks, I will try that and report back.

---

### Post by kenuf on 2010-01-16
> **RedEar said:**
> 
I atempted to use a usb stick; a sandisk cruzer 4gb. I formated and took everything off of it and then installed the disk image ubuntustudio-9.10-alternate-i386
I used Live USB creator
I changed the Bois (is that right?) to boot USB. Ubuntu Studio shows up on the USB when I boot it. But it either says it can not find the DVD or it gives me the "can not find /casper/vmlinuz disc image"

I have tryed the comand cdrom-detect/try-usb=true nothin...
I tryed vmlinuz initrd=initrd.img  nothin...
I would try moving folders but have no idea how to or what I am doing.

Please help. I get the feeling I will love ubuntu and use ubuntu studio a lot if only I could get it on my computer...

Thanks

I'm a NOOB too..  But I've installed several flavors of Ubuntu on 7 machines so far, so maybe I can help a little.

1.  I have never been successful Using a Windows app to create a live image USB.  But everytime I've booted to to a live CD and used the USB startup disk creator it has worked.  
If you have access to a computer with a CD Burner... Burn the image and try it.

2.  4 GB may be a little small...  that is the min recommended size for Ubuntu Netbook Remix.  You might try a 8GB drive.

3.  You could try Ubuntu Netbook Remix and then add the media authoring tools you want from Studio.
UNR has worked very well for me on the 3 netbooks I've tried it on.

For future reference it's BIOS Basic Input/Output System

Best of luck! and I hope something there helps!

---

### Post by warfacegod on 2010-01-16
> **kenuf said:**
> I'm a NOOB too..  But I've installed several flavors of Ubuntu on 7 machines so far, so maybe I can help a little.

1.  I have never been successful Using a Windows app to create a live image USB.  But everytime I've booted to to a live CD and used the USB startup disk creator it has worked.  
If you have access to a computer with a CD Burner... Burn the image and try it.

2.  4 GB may be a little small...  that is the min recommended size for Ubuntu Netbook Remix.  You might try a 8GB drive.

3.  You could try Ubuntu Netbook Remix and then add the media authoring tools you want from Studio.
UNR has worked very well for me on the 3 netbooks I've tried it on.

For future reference it's BIOS Basic Input/Output System

Best of luck! and I hope something there helps!

If a 700MB .iso will fit onto a CD then a 4 GB jump drive ought to be plenty of room to make an install "disc". I agree with you on the using USB creator part, it's the only thing that has worked for me as well.

---

### Post by RedEar on 2010-01-16
> **warfacegod said:**
> If a 700MB .iso will fit onto a CD then a 4 GB jump drive ought to be plenty of room to make an install "disc". I agree with you on the using USB creator part, it's the only thing that has worked for me as well.
Will it work to burn the disc and create the usb on a mac? All my other systems are mac.

---

### Post by kenuf on 2010-01-16
It should work...  booting to the live CD lets Ubuntu control all the writing to the USB drive.  So it will select the format.

> **warfacegod said:**
> If a 700MB .iso will fit onto a CD then a 4 GB jump drive ought to be plenty of room to make an install "disc". I agree with you on the using USB creator part, it's the only thing that has worked for me as well.

You may be very correct...  but two small things.

The USB 'live' boots are not static (the files get changed every time you use) unlike a CD which just resides in memory.  The USB drive is treated just like a tiny hard drive so the size needed is the fully installed size not the installer size.

And Studio is actually a DVD...  Download size is 1.5GB

---

### Post by warfacegod on 2010-01-16
> **kenuf said:**
> It should work...  booting to the live CD lets Ubuntu control all the writing to the USB drive.  So it will select the format.



You may be very correct...  but two small things.

The USB 'live' boots are not static (the files get changed every time you use) unlike a CD which just resides in memory.  The USB drive is treated just like a tiny hard drive so the size needed is the fully installed size not the installer size.

And Studio is actually a DVD...  Download size is 1.5GB

I didn't know Studio was a DVD. I believe that usb are static unless you make them with the ability to "save files and settings in reserve space". Either way, 4 GB is still plenty.

---

### Post by kenuf on 2010-01-16
> **warfacegod said:**
> I didn't know Studio was a DVD. I believe that usb are static unless you make them with the ability to "save files and settings in reserve space". Either way, 4 GB is still plenty.

OK that makes sense.  

I have a little concern about the performance of Studio on a 1.66 netbook.  

Should he be OK?

---

### Post by warfacegod on 2010-01-16
> **kenuf said:**
> OK that makes sense.  

I have a little concern about the performance of Studio on a 1.66 netbook.  

Should he be OK?

Its a single core so it will be a bit sluggish but if he doesn't turn on all the bells and whistles, like Compiz, it should do *O.K.*

---

### Post by RedEar on 2010-01-16
> **warfacegod said:**
> Its a single core so it will be a bit sluggish but if he doesn't turn on all the bells and whistles, like Compiz, it should do *O.K.*
It will more to explore it than to use it all the time. If I like Studio specificaly, I can set up a specific computer to run it. I am just anxious to be off of Windows...

---

### Post by warfacegod on 2010-01-16
> **RedEar said:**
> It will more to explore it than to use it all the time. If I like Studio specificaly, I can set up a specific computer to run it. I am just anxious to be off of Windows...

An admirable notion.

---

### Post by snowpine on 2010-01-16
I think this is a bug in the Ubuntu Studio installer. It should work OK if you burn to a DVD and use an external DVD-ROM, or if you install regular Ubuntu then all the ubuntustudio-* packages from Synaptic Package Manager.

---

### Post by RedEar on 2010-01-18
It worked! Thanks all. 
Just FYI I loaded Ubuntu on to my USB using USB installer for Ubuntu vs. 2.o and it worked perfect. Ran it from the usb and then partitioned and installed. Then installed the ubuntustudio packages and restarted. Works fine. I have yet to push it but it is all there and I am happy, thanks to you all!
Seth

---

