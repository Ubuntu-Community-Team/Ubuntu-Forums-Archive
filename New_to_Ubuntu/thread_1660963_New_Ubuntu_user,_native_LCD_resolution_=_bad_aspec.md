---
title: "New Ubuntu user, native LCD resolution = bad aspect ratio..."
date: 2011-01-06
forum: New to Ubuntu
---

### Post by 31Orcas on 2011-01-06
Hello!

I'm new to Ubuntu, and, long story short, I screwed up the partition table on my 500GB hard drive (it's still alive though :)). So Ubuntu made me go and get a 1.5 TB WD Caviar Green hard drive (which we couldn't really afford... $69.99 + tax at Fry's).

I've been using Ubuntu for about 2 days now, and I'd like to get some more info on how it installs and what types of files it uses, ect.

I'm planning on dual-booting Windows Vista Home Premium and Ubuntu 10.10.

On a side note, Ubuntu says "1.3 TB free space" when I go to Places > Computer... I didn't install anything yet except for the updates.

So, my main problem that has also bugged me in both Windows and still persists in Ubuntu is that my monitor's native resolution doesn't have a good aspect ratio. It's not wide enough; it's too compressed horizontally. The image quality is beyond amazing compared to when I had it in 1152 by 864, however, my vision doesn't seem to enjoy horizontally compressed images.

Is it at all possible, with any OS, to change the aspect ratio of the screen and not the resolution?

Thanks in advance!

---

### Post by amjjawad on 2011-01-06
> **31Orcas said:**
> Hello!

I'm new to Ubuntu, and, long story short, I screwed up the partition table on my 500GB hard drive (it's still alive though :)). So Ubuntu made me go and get a 1.5 TB WD Caviar Green hard drive (which we couldn't really afford... $69.99 + tax at Fry's).

Screwing up the Partition Table does not require to buy a new HDD unless the HDD is totally dead.
Formatting the HDD will fix lots of issues and if not, then low level format is the last solution.


> I'm planning on dual-booting Windows Vista Home Premium and Ubuntu 10.10.
Check my signature, you'll find all what you need.


> On a side note, Ubuntu says "1.3 TB free space" when I go to Places > Computer... I didn't install anything yet except for the updates.
Not sure what do you mean here?!


> Is it at all possible, with any OS, to change the aspect ratio of the screen and not the resolution?
System > Preferences > Monitors

---

### Post by mastablasta on 2011-01-06
> **31Orcas said:**
> Hello!
 
I'm new to Ubuntu, and, long story short, I screwed up the partition table on my 500GB hard drive (it's still alive though :)). So Ubuntu made me go and get a 1.5 TB WD Caviar Green hard drive (which we couldn't really afford... $69.99 + tax at Fry's).
 
---------
 
On a side note, Ubuntu says "1.3 TB free space" when I go to Places > Computer... I didn't install anything yet except for the updates.
 

 
Caviar Green disks need to be properly aligned before you add any data to it. i am not sure what is the linux tool for this. you need a 3rd party programme after formating the disk. 
See more info here: [http://support.wdc.com/product/download.asp?groupid=805](http://support.wdc.com/product/download.asp?groupid=805)
Download links: [http://support.wdc.com/product/downloadsw.asp?sid=123](http://support.wdc.com/product/downloadsw.asp?sid=123)
 
> 
 
I've been using Ubuntu for about 2 days now, and I'd like to get some more info on how it installs and what types of files it uses, ect.

 
Chech the ubuntu manual in my signature. it has all the basic information on the OS with lots of pics and is easy to understand. it+'s for 10.04, the install for 10.10 is slightly different but the rest is the same.

---

### Post by coffeecat on 2011-01-06
> **mastablasta said:**
> Caviar Green disks need to be properly aligned before you add any data to it. i am not sure what is the linux tool for this. you need a 3rd party programme after formating the disk. 

I have a couple of Caviar Green (500GB and 1TB) discs in the machine I'm posting from. I'm fairly sure - although I'm happy to be corrected - that if you use the version of Gparted
from Maverick/10.10 or later that partitions will be correctly aligned. Possibly Lucid onwards. Whatever - my Maverick Gparted partitions seem to be behaving themselves.

---

### Post by coffeecat on 2011-01-06
> **31Orcas said:**
> Is it at all possible, with any OS, to change the aspect ratio of the screen and not the resolution?

No. The aspect ratio of a monitor is 4x3, 16x10 or 16x9 depending on the number of pixels horizontally and vertically. The physical dimensions of the screen will reflect the pixel ratio. Take a tape measure to it to see.

> **31Orcas said:**
> So, my main problem that has also bugged me in  both Windows and still persists in Ubuntu is that my monitor's native  resolution doesn't have a good aspect ratio. It's not wide enough; it's  too compressed horizontally. The image quality is beyond amazing  compared to when I had it in 1152 by 864, however, my vision doesn't  seem to enjoy horizontally compressed images.

1152x864 is a 4:3 ratio. The only way you can get a widescreen image on that is to have black bands on the screen top and bottom. Is that what you want? Apart from displaying videos I'm not sure how you would do that. If you want a proper widescreen image you need a new monitor.

Or am I misunderstanding you?

---

### Post by 31Orcas on 2011-01-06
@amjjawad: About formatting the HDD... I could easily have re-formatted it, but I can't risk losing the data on it.

@mastablasta: Thank you!! Great links, the manual is much better than the one of the Ubuntu home page.

@coffeecat: Nevermind, apparently my monitor is setup correctly : ).

---

### Post by amjjawad on 2011-01-06
> **31Orcas said:**
> @amjjawad: About formatting the HDD... I could easily have re-formatted it, but I can't risk losing the data on it.


You misunderstood my post :)

This is your original post:

> **31Orcas said:**
> Hello!

I'm new to Ubuntu, and, long story short, **I screwed up the partition table on my 500GB hard drive** (it's still alive though :smile:). **So Ubuntu made me go and get a 1.5 TB WD Caviar Green hard drive** (which we couldn't really afford... $69.99 + tax at Fry's).

Your post wasn't clear and you made it look like something is wrong with the HDD so you bought another one. Sorry if I misunderstood yours but again it was not clear enough.

There is a **difference** between corrupted Partition Table (MBR) and a HDD that can't boot from.

Corrupted MBR > Format
Un-bootable HDD > Re-install the Boot Loader

If you have some data on that HDD (the old one), boot from the LiveCD and restore what you have over there or fix the MBR so you can boot again from it.

Good luck ;)

---

### Post by theozzlives on 2011-01-06
I agree, Ubuntu didn't make you buy a new HDD. You wanted to. If you have a widescreen, try 1280x800. That should take care of the distortion.

---

### Post by 31Orcas on 2011-01-07
@amjjawad: Haha, I guess we didn't understand each other. 

So... I have both hard drives up and running, with the small hard drive mounted so that I can move, rename, delete, edit, and copy to and from Ubuntu with no problems at all.

It's all good, now all I have to do is use Ubuntu until I'm an expert : ).

@theozzlives:Yeah, you're right. No biggie, my mom always says that it's a good thing if things break, because it's out with the old and in with the new.

BTW, my old HDD is also a Western Digital! I'm using a Gateway GM-5472, and the hard drive it came with is flawless! And now it has a big brother/sister/who knows!

I think 1280 x 864 and 1440 x 900 are the best looking resolutions for this monitor. I'll just experiment around and see if I can achieve something.

---

