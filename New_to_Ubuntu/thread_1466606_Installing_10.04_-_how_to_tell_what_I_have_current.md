---
title: "Installing 10.04 - how to tell what I have currently?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by zcacogp on 2010-04-30
Chaps, 

I am just on the verge of going from 9.10 to 10.04. 

I think I want to do a fresh install on at least one of my machines (for a number of reasons.) If I do this, is there an easy way to tell what I have installed on the machine before I start? Ideally, to provide a list of software that I have installed since the machine was built (it had 9.04 and 8.10 on it beforehand, and was upgraded - as opposed to having a fresh install - each time.) 

Also, the machine doesn't have a built-in CD drive. Is there a way of installing from the download without needing to put it on a CD? Can I remote mount the download across the network, or something like that? Or put it on a USB stick? (If I can't then it's not a major hassle, but I will need to spend 1/2 an hour or more finding the external CD drive I have ... and I can't remember where I put it!) 

Thanks, in advance, for any help. 


Oli. 

P.S. Also, where is the best place to get the download from? It sounds like the Ubuntu servers are all chocka at the moment.

---

### Post by Jon Monreal on 2010-04-30
I can see a couple of options here.

You could create an [apt-mirror]("http://www.howtoforge.com/local_debian_ubuntu_mirror") (that guide is old) to install from the network. This isn't the easiest option, however.

If you have a sufficiently good internet connection, you could simply export a package list and then install everything again. If you have any software installed that isn't in the repos, you'll have to write down their names as they fail in order to get them later. This is probably easier. If you need to know how to do this, feel free to ask.

You could look into [Keryx]("http://keryxproject.org/"), which I have no experience with. From the looks of it, though, you can't simply import the packages from Synaptic or the like. And if it did work, you could end up with a lot of extraneous old dependencies on the USB that ultimately aren't installed in the new installation, and packages that might not work because you aren't downloading the latest version.

I apologize if this is all a bit overwhelming, I've always used APTonCD myself.

---

### Post by Paqman on 2010-04-30
> **zcacogp said:**
> is there an easy way to tell what I have installed on the machine before I start? Ideally, to provide a list of software that I have installed since the machine was built (it had 9.04 and 8.10 on it beforehand, and was upgraded - as opposed to having a fresh install - each time.) 


Yep, that's [really easy]("http://ubuntuforums.org/showthread.php?t=261366").

> 
Or put it on a USB stick?


Absolutely, use the USB startup Disk Creator tool, or install Unetbootin and use that.

> 
P.S. Also, where is the best place to get the download from? It sounds like the Ubuntu servers are all chocka at the moment.

Grab the [official torrent]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt"), there will be thousands of seeders and it'll download in a flash.

---

### Post by zcacogp on 2010-04-30
Chaps, 

Thanks for your answers. 

I decided to plug on and try the instructions on installing via USB. Using the System > Adminstration > USB Disk Creator tool gave me a checksum error, every time, so I tried the unetbootin route instead. That appears to have created a USB bootable OK (as in, it completed on my desktop machine without any errors), but when I placed the USB drive into the laptop and booted it, it won't work. 

When I boot the laptop with the USB drive plugged in, I am shown a pale grey screen (with unetbootin at the top), and there are three options.  

Option 1. "Default"

- This shows a purple-backed "Ubuntu" screen, but then gives the message "(initramfs) mount: mounting /dev/loop0 on //fielsystem.squashfs failed: No such device
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

Option 2. "Help". 

- This gives various screenfuls of text (white on a black background), then the error message "[5.586383] console: switching to colour frame buffer device 128x48 ALERT! does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for al ist of built-in commands.

(initramfs)"

Option 3. "oem = OEM install (for manufacturers)" 

- This does the same as option 2 ("Help"), and errors in the same way. 


For what it's worth, the machine I am trying to install it to is an old IBM X31 laptop. 


Any suggestions? 


Oli.

---

### Post by Paqman on 2010-04-30
> **zcacogp said:**
> 
For what it's worth, the machine I am trying to install it to is an old IBM X31 laptop. 


Do you know for sure that it boots from USB alright? A lot of old machines don't.

---

### Post by zcacogp on 2010-04-30
OK, we're making small steps of progress. 

Paqman, thanks for your thoughts. I re-made the USB drive (ran unetbootin again), and I can now get the laptop to run 10.4, in the 'try this' mode. 

However, despite it having an "Install Ubuntu 10.04lts" icon on the desktop, I can't make it install. If I click this icon, I am asked the usual questions about where I am (geographically) and what language I use, and then the window closes and it goes no further. 

The other two boot-up options ("Help" and "oem" both still give errors.) 

Maybe I should just try from CD, perhaps? 


Oli.

---

### Post by zcacogp on 2010-04-30
... more information. If I run the command that is executed by the icon (ubiquity --desktop %k gtk_ui), in the terminal, it just returns to the command prompt without doing anything. 


Oli.

---

### Post by mörgæs on 2010-04-30
If your machine has been upgraded through several Ubuntu releases I would recommend that you don't try to reconstruct what was there. The benefit of a fresh install is that all traces of obsolete software and configurations are wiped out. Just install a default 10.04, and if needed you can add new software from Software Centre.

I can't help with the USB boot, sorry.

---

### Post by zcacogp on 2010-04-30
OK, just created the USB drive for the third time (didn't work at all) and now a fourth time, and it almost worked as it should ... 

Now it has got 24% of the way through installing it (the install screens appeared as they should), but it has just given me an "[Errno 5] Input/Output error". With a suggestion that the CD drive lens may be dirty, or similar. 

Which seems odd as I am installing from a USB drive. 

I'll try again. Fifth time. This isn't an auspicious start for getting into 10.4 ... 


Oli.

---

### Post by Paddy Landau on 2010-04-30
> **zcacogp said:**
> Using the System > Adminstration > USB Disk Creator tool gave me a checksum error, every time...
When you downloaded the ISO, did you [check the MD5]("https://help.ubuntu.com/community/UbuntuHashes")? A bad download could cause the problems you're having.

Alternatively, try finding that CD drive, in case the old machine doesn't boot correctly from USB.

---

### Post by Jon Monreal on 2010-04-30
I remember getting Errno 5 back in the days of Feisty (7.04). It was solved by using "sudo ubiquity --desktop %k gtk_ui", but I would check the MD5 first as suggested above.

---

### Post by zcacogp on 2010-04-30
Paddy, 

Thanks. No, I hadn't checked it (and still haven't). 

I have, however, managed to make it work with a CD. (After a fair old rootle in the basement I found the external CD drive, and after a bit more rootling found the power cable ... ) And it is now working. And I am posting this from the newly-built machine! 

(And, finally, I am really quite liking it! None of the teething problems I had with 9.10.)  

Thanks to everyone for your help. It was appreciated. 


Oli.

---

### Post by Paddy Landau on 2010-05-01
Glad you got it solved.

Have fun.

---

