---
title: "Trouble installing with USB"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by NGLGDV on 2010-05-23
Hi everyone,

I'm very new to the Linux world, and this is the first time I try to install Ubuntu. 
Just to let you know I downloaded the 64-bit version.
I've tried following the information on [_this page_]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick"). When I put the installer on my flash drive, I had a window popping up saying that some files were broken. I closed that window and then the set up was done "**successfully**". When I plug in my flash drive, Windows offers to Install Ubuntu, so I'm guessing it worked fine, and also I have the "wubi" application on it.
But when I tried booting on the USB, nothing works. I get to an Ubuntu screen with different options (running Ubuntu from the flash drive, or installing it on the hard drive, are 2 of them), but it won't let me choose any of them. I went to the Help menu where I saw the command line "boot:", and when I press enter I get an error message saying that **the kernel image couldn't be found**... 
The only thing I could do was unplug my laptop and reboot it with Windows...
What should I do?

Sorry for the long message...

---

### Post by Ozymandias_117 on 2010-05-23
Press the esc key during that purplish boot screen (Figure 2 on the link you provided) and there should be an option there to test for defects. Try that.

---

### Post by sylvester_0 on 2010-05-23
Hello, I checked the link that you posted and I'm not familiar with that installation method. It looks quite old.

I'd recommend you format the stick and try using UNetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to install 10.04 x64 Live to the USB stick. However, if you've got less than 3GB of RAM and you're a total newbie, I'd recommend you use the 32-bit version; it'll make life a lot simpler (Adobe Flash being the main concern.)

---

### Post by NGLGDV on 2010-05-23
Thanks for your answer Ozymandias! I should have mentioned it in my first post, but I didn't get to that nice looking purple screen; mine is white over black, and ugly ^^
Thanks Sylvester!! I'll try what you say! I'll come back to let you know!

---

### Post by dtfinch on 2010-05-23
I've had times where reformatting the usb drive made a difference, like the bootloader could only access files that were located in the first 1gb or so of the drive.

---

### Post by NGLGDV on 2010-05-23
So I tried putting the 64-bit installer on my flash drive using UNetbootin as **Sylvester **suggested. I got a similar answer as before... Now I am downloading the 32-bit version, we'll see if that works. But as it takes 3 hours to download, you might not here from me for a while ^^
In the mean time, I'm also formatting my flash drive, following dtfinch's advice; **thanks**!!

Thanks everyone for your help :)

---

### Post by r_s on 2010-05-23
Unetbootin offers a method where you just need to mention the distribution and it will itself create a bootable usb. I don't think so it takes about 3 hrs , perhaps much less.

---

### Post by sylvester_0 on 2010-05-23
> **NGLGDV said:**
> So I tried putting the 64-bit installer on my flash drive using UNetbootin as **Sylvester **suggested. I got a similar answer as before... Now I am downloading the 32-bit version, we'll see if that works.

So, you tried writing your 64-bit iso to the drive using unetbootin and had the same problem? Are you sure the iso isn't corrupt (an md5sum can tell you this.) I recommend using torrent to grab isos because they can be resumed if something happens to your connection plus they already perform checksumming.

> I don't think so it takes about 3 hrs , perhaps much less. 

I guess it all depends on his connection speed...

---

### Post by NGLGDV on 2010-05-23
So I'm downloading the 32-bit version from the website, and also through UNetbootin, as **r_s** said. If none of those work, I'll try using torrent :)
Thanks for being so patient with me!!

---

### Post by NGLGDV on 2010-05-24
Hey guys I'm back!
So I rebooted my laptop with my flash drive plugged in (on which I had downloaded Ubuntu through UNetbootin). I successfully boot on the flash drive, so now I'm able to play around with Ubuntu a little bit. :)
But how do I install it? I didn't have an option to do so as it was booting... Should I use the Install Ubuntu icon that is my desktop now?

Sorry again for all my stupid questions... And thanks for helping me out!

---

### Post by NGLGDV on 2010-05-24
Any advice?

---

### Post by NGLGDV on 2010-05-24
Ok, so I tried installing Ubuntu from the shortcut on my desktop. When I got to the screen asking to prepare the disk space, I chose install side by side, and I allocated around 40GB to Ubuntu (Windows had like 11, and its recovery system 160...). Then I had a "please wait" window for like 20 minutes, and then the installer said that it couldn't partition the disk. I got back to the screen asking to prepare the disk space, but the "install side by side" option had disappear, and I don't want to erase everything, and I don't know how to partition the disk by hand...
Any help?

---

### Post by r_s on 2010-05-24
yes , the desktop icon would say , install ubuntu to hard drive.

---

### Post by r_s on 2010-05-24
you should post the layout of your partitions

---

### Post by NGLGDV on 2010-05-24
Ok: so I re start the installer, I go through the first screens (language, time zone, keyboard) and then I get to the "Prepare Disk Space". I don't have anymore the "install side by side" option. The first bar shows : Windows Vista (loader) (/dev/sda1) 11.1GB and Windows Recovery (loader) (/dev/sda2) 149.0GB.
Does that help at all?

---

### Post by r_s on 2010-05-24
so why don't you use a custom layout [[ Manually edit partition table ]] , and add another primary partition for ubuntu and some swap space. 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by NGLGDV on 2010-05-24
Thanks for the link!!
How much space should I leave for each partition?

---

### Post by r_s on 2010-05-24
It depends on you and the type of applications you wish to run, for swap 2 GB is sufficient.

---

