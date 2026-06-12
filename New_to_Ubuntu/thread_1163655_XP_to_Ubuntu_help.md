---
title: "XP to Ubuntu help"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by SL1DEmemphis on 2009-05-18
Hello,  So I've been try to do a bit of research before I screw anything up.  I am new to linux based OS' and I am not sure how to install Ubuntu on my XP PC.  I am wanting to remove XP in the process along with everything on that HD.

I have the Ubuntu .iso and a 8gig flashdrive.  
I have read up on this page, [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick),  but I am still confused, I am not sure what to do.

Where do I go from here?  Any help is appreciated, thanks!

Andrew

---

### Post by Volt9000 on 2009-05-18
Well, what have you tried so far? Exactly where are you getting stuck?
You'll have to provide more details for us to help you.

---

### Post by Chemical Imbalance on 2009-05-18
First off, welcome to the forums!

The first step you should take to get that .iso onto your usb drive is to download this and install it onto your windows machine:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


Also make sure you have backed up all your data from XP onto some external media.

---

### Post by SL1DEmemphis on 2009-05-18
Well, I haven't exactly started,  right now I am formatting my stick to FAT32 then going to put the ubuntu.iso on it.  then I don't know what to do!  Am I supposed to put anything else on it.   is that SYSLINUX or UNETBOOTIN required to install? Should I format my harddrive before I begin or will it do that in the process?

---

### Post by Volt9000 on 2009-05-18
Before starting this, you should check to make sure your computer can boot from a USB drive. Not all BIOSes support this. It would be much easier to just burn the image to a CD.

You don't need to reformat your hard drive, as the installer gives you the option of doing that for you.

As for creating the USB stick, the guide refers to a program called [UNetbootin](http://unetbootin.sourceforge.net/) which lets you create a bootable USB stick with a Linux distro on it. So run that and install the image onto the stick, and then just boot from it. If your computer can boot from a USB stick, then just boot your computer with the stick inserted and the Live session should start.

---

### Post by Chemical Imbalance on 2009-05-18
> **SL1DEmemphis said:**
> Well, I haven't exactly started,  right now I am formatting my stick to FAT32 then going to put the ubuntu.iso on it.  then I don't know what to do!  Am I supposed to put anything else on it.   is that SYSLINUX or UNETBOOTIN required to install? Should I format my harddrive before I begin or will it do that in the process?

Yes, format the drive to FAT32 first.

Then install unetbootin.

Unetbootin will take that iso file (which is meant for cd's only) and will convert it to be able to boot with on a usb stick.

Unetbootin is easy to use.  Just install and run it.
Plug your usb stick in.  Unetbootin will ask where your .iso file is located.  Make sure the path to your usb stick is correct and press install.

It will finish within a few minutes.

Afterwards, before you boot the usb stick to install ubuntu, make sure you have backed up all your important files from XP (like music, documents, pictures,  etc...).  This is because you have said you want to completely wipe away your XP install.

It is always a good idea to back up anyways.

Also, I recommend you don't install Ubuntu right away at first.  
You can use the WUBI installer to run ubuntu from within windows.
You can also just boot a "live" session from your usb stick that lets you explore Ubuntu from your RAM without touching your hard disk.

A live session also allows you to see if your hardware will work with ubuntu.
If I were you, I wouldn't install until you are confident in doing so.
Read up on linux and ask all the questions you want first.
Linux is not like Windows in a lot of respects and it pays to research first.

---

### Post by SL1DEmemphis on 2009-05-18
Alright I will give that a try, I'll let you know how it goes, thanks!

---

### Post by Duskao on 2009-05-18
If I were you I would just burn it onto a cd instead of the flash drive as that is a little bit more complicated process. But either way you should be able to accomplish what you want to do without too much of a hitch. Being able to boot computers from flash drives is a fairly newish process and not all mother boards and bios support it.

---

### Post by SL1DEmemphis on 2009-05-18
I'm in the process up transferring my wanted files to my second HDD

---

### Post by SL1DEmemphis on 2009-05-19
Thank you everyone, I am now talking to you through Firefox in Ubuntu!  Now I get to explore!

---

### Post by lisati on 2009-05-19
> **SL1DEmemphis said:**
> Thank you everyone, I am now talking to you through Firefox in Ubuntu!  Now I get to explore!

Well done for what you've achieved so far - keep up the good work! I'm sure that if you have any further questions there will be someone here with a few ideas to try.

---

### Post by theozzlives on 2009-05-19
Congrates!!! You'll like Ubuntu better than Windows and one day you'll realise, "Hey, I don't have any adware, spyware, or any malware".

---

### Post by SL1DEmemphis on 2009-05-19
Thanks again!  So far I do like Ubuntu better than Windows...  I need to figure out the file system and how moving files works, it looks similar to Mac OS.

---

### Post by SL1DEmemphis on 2009-05-19
quick question, should I add a Program/Application folder or is there already something like that elsewhere?

---

### Post by SL1DEmemphis on 2009-05-19
So wow, this is so easy.... Ubuntu > Windows...  Finding Applications is soooooooo so easy its crazy.

---

### Post by Volt9000 on 2009-05-19
> **SL1DEmemphis said:**
> quick question, should I add a Program/Application folder or is there already something like that elsewhere?

If you're talking about the equivalent of C:\Program Files in Windows, there isn't anything really like that in Linux. The closest thing would be /usr/bin which is where most program binaries are installed into.

If you're talking about something like Start > Programs, this is available (by default) in the top-left corner, the Applications menu. This is where your program icons will appear.

---

### Post by rcayea on 2009-05-19
Congrats!I hope you enjoy ubuntu.

---

### Post by Chemical Imbalance on 2009-05-20
In most linux distros (distributions), like Ubuntu, you can install programs/applications from a central repository ("repo").  
These repos house all the programs that developers package and safety-check specifically for a distro.  

So, in other words, don't install programs from the internet unless its not in the ubuntu repository.  
Make sure if you do, however, that it's not some shady site.

To install a program, the easiest way would be to go to Add/Remove or go to Synaptic Package manager.

I do install quite a few things like games and Google Earth from my web browser though.

Also, the name of Ubuntu packages are called .deb (similar to Windows' .exe).  
Some other endings for linux packages that work in Ubuntu can be .sh, .tar and .bin.

But don't worry about this too much now.  Just giving you a heads up.

Also, if you want some reading on linux, check out my signature for a great beginner's guide.

Enjoy Ubuntu!

---

