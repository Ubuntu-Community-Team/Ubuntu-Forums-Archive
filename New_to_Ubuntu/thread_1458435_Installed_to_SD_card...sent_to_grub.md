---
title: "Installed to SD card...sent to grub"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by jacjyd on 2010-04-20
Hey, not new to using linux, but this is my first install!

I just got a Dell Mini 9 with Win XP...was hoping to boot linux from an SD card (just for kicks)  but apparently it's not possible without an SD card reader (or there are conflicting reports).  I made a live CD SD card using UNetbootin...

I decided to just try and install it straight to the SD card.

It seemed to work, or it did something.  When I boot the computer, I have the option of win xp or ubuntu.

When I choose ubuntu, it sends me straight to the grub prompt.

1) What did I do wrong?
2) Can I fix it?
3) Is there any way to do what I want to do? =P

I updated the bios on my dell mini to A06, if that matters.

Thanks!

---

### Post by CaptainMark on 2010-04-20
Been a while since ive been doing anything other than web browsing on ubuntu but it sounds like youve installed grub on your main drive over windows boot manager. you need a windows cd to get to the recovery console and run FIXMBR 
Like i say ive been outta the loop for a while but its a start.

Ps, plus you may want to re run the SD card install but in ther setup look for the option to put grub on SD card too

---

### Post by jacjyd on 2010-04-20
How does this help getting to linux?  

I see what you're saying though.  I do remember reading on a forum somewhere else that I should've needed to do some advanced setting thing but I never got the chance.

---

### Post by snowpine on 2010-04-20
I have a Dell Mini 9. It cannot boot from an SD card.

I would recommend installing Ubuntu side-by-side with Windows on your SSD hard drive (assuming you have enough space).

If you want to abandon the project, follow CaptainMark's advice to restore your Windows boot loader. :)

---

### Post by jacjyd on 2010-04-20
:-) Yeah, I think I just basically screwed up and I might have to start over.  I have some leeway though since WinXP is still working just fine...I just have to take the extra second to choose it at startup!
 
At the moment there isn't enough room for Ubuntu on the SSD. :-( Since it came with XP anyway, I have Steam installed on it and a few games...but they take up a lot of space since XP already takes up 7 gigs or so! =P
 
I wonder if the games can run from the SD card...

---

### Post by snowpine on 2010-04-20
I forgot to mention, here's how to prevent that from happening next time. :)

Your SD card (or any other drive for that matter) has a name, like /dev/sda, /dev/sdb, etc. Usually /dev/sda is the internal drive, /dev/sdb is the first external drive, etc. So when you get to the Partitioning step of the installer, make a note of the device name.

Then, when you get to the last step of the installer, click the Advanced button. This will bring up a screen where you can specify where to put Grub. If you choose the correct drive (for example /dev/sdb), it will not touch the Windows boot loader on /dev/sda.

If you set it up that way, the computer will boot straight to Windows. However, you can press a key (I think it is Esc on most eee's) and choose to boot from the drive with Ubuntu instead. Remember though that it can't be an SD card (but you could use a USB thumb drive).

---

### Post by LewRockwell on 2010-04-20
Thumb drives are more robust physically and therefore preferred anyway, IMHO.

.

---

