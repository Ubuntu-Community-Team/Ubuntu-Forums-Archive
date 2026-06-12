---
title: "USB Installs"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by skinnyj on 2010-07-06
Absolute beginner here, and I am getting ready to install Ubuntu. Seeing as how I move from place to place a lot, a question came to mind.

While moving from computer to computer, would I have to constantly reinstall the drivers that are necessary for that system, or is it all managed by Ubuntu?

---

### Post by spydeyrch on 2010-07-06
Well, that depends. How are you doing the install? Are you installing Ubuntu to an external HDD and then taking that drive with you and thus connecting it to different machines at different times? Please clarify a little. Thanks. ;)

-Spydey:o

---

### Post by skinnyj on 2010-07-06
> **spydeyrch said:**
> Well, that depends. How are you doing the install? Are you installing Ubuntu to an external HDD and then taking that drive with you and thus connecting it to different machines at different times? Please clarify a little. Thanks. ;)

-Spydey:o

I'm actually [planning on] installing it to a SanDisk Cruzer 8 gig flash drive.
Like the one here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820171399](http://www.newegg.com/Product/Product.aspx?Item=N82E16820171399)

---

### Post by spydeyrch on 2010-07-06
There are a few options: are you planning on doing a Live USB with persistent file or are you going to go through the full install process with your USB flash drive as the destination drive?

-Spydey :D

---

### Post by skinnyj on 2010-07-06
> **spydeyrch said:**
> There are a few options: are you planning on doing a Live USB with persistent file or are you going to go through the full install process with your USB flash drive as the destination drive?

-Spydey :D
Most likely a full install with the drive as the destination.

---

### Post by spydeyrch on 2010-07-06
Well, a couple things.

1.) I don't know how GRUB would react to being installed on a USB thumb drive and consequently being moved from one computer to another. Someone else in this forum might be able to give you more info regarding this little issue. You might run into problems with that but I don't know because I haven't done it. But you will want grub on the thumb drive.

2.) From personal experience, via Live USB with persistent file, I have taken my 16GB thumb drive to many computers with different hardware specs. I have installed many different drivers. Primarily for wireless. But never for GPU (that would mess it up). I never had a problem. It would always select the correct driver. From my understanding, if you install a driver for an ATI card then go to a nVidia computer, you might run into problems, hence I didn't install gpu drivers. But this was for a live usb with persistent file. I would assume that it runs pretty much the same.

Now you have gotten me curious. I might go home and try installing it to my thumb drive.

My recommendation would be to go with a live persistent install instead of doing a full install with the usb thumb drive as the destination.

If you would like some pointers/suggestions about doing a live usb install (with persistent file) let me know and I will see what I can do. :D

-Spydey:p

---

### Post by skinnyj on 2010-07-06
> **spydeyrch said:**
> 
Now you have gotten me curious. I might go home and try installing it to my thumb drive.


Hehehe, let me know if you come across any problems.
I just might try the Live USB install, so those pointers would most certainly be welcome.

---

### Post by spydeyrch on 2010-07-06
> **skinnyj said:**
> ......I just might try the Live USB install, so those pointers would most certainly be welcome.

Ok, well, when you do the live usb with a persistent file, the max that it can use is 4GB. Therefore with your 8GB usb, you will need to partition it to have 2 partitions, each of 4GB. If you don't you will only be able to use 4GB for the live install and the remaining 4GB will be un-usable. The first partition is going to be for the live version (with persistent file) and the second one will be your 'shared' partition. The 'shared' partition can be used as a regular USB thumb drive to store files which will be accessible from any and all OSes.

So here we go:

If you already have ubuntu installed, skip the next two paragraphs.

1.) You will want to download, if you haven't already, the version of *buntu that you want to use. You will either need to burn it to a CD/DVD or use the [universal USB installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") for windows or [UNetBootin for both Linux & Windows]("http://unetbootin.sourceforge.net/") to install it to a separate USB thumb drive from the 8GB that you will you use for your live install. (Let me know if that makes sense or if something doesn't work.)

2.) Once you have installed the .iso via UNetBootin/Universal USB Installer to the second USB thunb drive or burned it to a CD/DVD, boot from it.

3.) Once you are in the OS, insert your 8GB USB Flash Drive. You should see it mounted and an icon appear on your desktop. Right click on it and select 'format'.

WARNING!!!! This will erase all the info currently on your 8GB thumb drive!!! You have been warned!!! WARNING!!!!

Click on the 'Disk Utility' button. Select your drive at the root and format it into two partitions: each of 4GB. Make sure that you select the format as FAT32 (it might just be labeled as FAT). Label them according: 1st - Ubuntu, 2nd - Shared.

Let the system do it's stuff.

Once it is done, close the disk utility program. Un-plug the USB drive. Then plug it back in. Once it comes up go ahead and close any windows that appear. Go to the menu bar System -> Admin -> USB Creator (it might be label startup creator or something similar).

Select the location of the .iso that you want to install to the usb drive. Then select the first partition (it should be labeled accordingly to what you previously labeled it.)

Down towards the bottom make sure that you select the persistent option and move the slider all the way to the right to select as much available space in the first partition as possible to use as the persistent file.

Go ahead and select next/done/proceed (I don't remember exactly what it is called but it is the button that starts the process).

Once it is done. Try it out by restarting the machine and booting from your new liv persistent usb. Any changes you make to the system will be saved. Any drivers you install will be saved. I would refrain from installing any graphic drivers for, hopefully, obvious reasons. Also, you can update your ubuntu install via the update manager EXCEPT (from personal experience) don't update the kernel (linux image). Also, don't do all updates at once. Do it in multiple updates. I have had my system crash if I do all the updates at once.

Hopefully that helps. Let me know if you have any questions. ;)

-Spydey:P

---

### Post by spydeyrch on 2010-07-06
I may have missed a step or explaining something in more depth. I am at work right now and so don't have my system available to me. Let me know. :popcorn:

-Spydey

---

### Post by skinnyj on 2010-07-07
> **spydeyrch said:**
> 
2.) Once you have installed the .iso via UNetBootin/Universal USB Installer to the second USB thunb drive or burned it to a CD/DVD, boot from it.


What is the minimal size for this second drive? I heard that 1GB is good enough.

---

### Post by CharlesA on 2010-07-07
It only needs to be larger than the ISO, so a 1GB one would work.

---

### Post by skinnyj on 2010-07-07
Well that makes sense. Now all that's left to do is to prepare my flash drive for install (As in, move everything to a place that is safe and empty the drives.)

---

### Post by CharlesA on 2010-07-07
I've got a dedicated thumb drive I use for doing installs and whatnot via USB, so I can just wipe it and "burn" whatever I want to install via usb onto it. No backing up data for me. :-)

---

### Post by skinnyj on 2010-07-07
I can't wait to get this done. I'm also very surprised at how quick and helpful this forum is.

---

### Post by Directive 4 on 2010-07-07
> **skinnyj said:**
> Most likely a full install with the drive as the destination.



i'd do this, 

just remember to point grub at the usb during install

most prob everything will work great,

i have not found a computer that has given me problems yet.


one word of warning, be carefull insatlling updates to the usb when the internal HDD s mounted.

---

### Post by CharlesA on 2010-07-07
Didn't see if you wanted to do a persistant install or not, but if you do it that way, the drive will have to be a couple gigs in size at least.

Otherwise you are just installing the LiveCD to a thumb drive.

---

### Post by skinnyj on 2010-07-07
I might try the full install first and give it a few days and see how it works. If it ends up crapping itself, then I'll do the Live USB install so it won't crap itself.

---

### Post by skinnyj on 2010-07-07
> **spydeyrch said:**
> 1.) You will want to download, if you haven't already, the version of *buntu that you want to use. You will either need to burn it to a CD/DVD or use the [universal USB installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") for windows or [UNetBootin for both Linux & Windows]("http://unetbootin.sourceforge.net/") to install it to a separate USB thumb drive from the 8GB that you will you use for your live install. (Let me know if that makes sense or if something doesn't work.)

 
I got it to boot, but it was saying that it was missing the kernel or a main file, so I'm currently redownloading the .iso and see if that might correct the problem.

---

### Post by spydeyrch on 2010-07-07
> 
Didn't see if you wanted to do a persistant install or not, but if you  do it that way, the drive will have to be a couple gigs in size at  least.

Otherwise you are just installing the LiveCD to a thumb drive.


Yes, just remember that if you go the live usb (w/persistent file) route, that you will be using your 8GB flash drive as the primary drive and need at least two partitions, the first being 4GB, no more (can't use more than 4GB), and no less as this would limit your persistent file.

As far as the full install to the USB flash as the destination, I was thinking about something the other night. This is what I came up with. Again, remember that this just what I was thinking in my head and haven't done it yet so I don't know if it would really work and/or what issues might come up. Feel free, anyone, to add/remove from what I write:

In order to get a full install on the USB drive, not just a live usb, this is what I would do:

WARNING!!! Again, this was just me thinking last night and out loud here  on the forum. I don't know if it will work exactly as I have written  it. Just make sure that you are aware of the risks. WARNING!!!

You will need either a live cd and your 8GB flash drive or 2 flash drives: your 8GB (1st) and an extra usb flash (2nd) that will already have a live version on it.

While my machine is powered down (off), I would disconnect all HDD from either the data cable, power cable, or both.

Boot off of either the CD or 2nd usb flash, doesn't matter.

Once you are up and running, insert/connect your 1st usb flash (the 8GB one). Then run the isntall program from the live desktop with your 8GB usb flash as the destination. You will want to install GRUB to it and do everything normal, treat it as if it was an internal HDD.

Once the install is done, restart the machine with your HDD still disconnected but only your 8GB flash connected. Boot off of it to see if it installed correctly and working properly.

Run update manager but only update in small groups of updates (hopefully that makes sense).

You should then have a running full install on your 8GB flash drive.  :p

I would then reconnect your HDDs, while powered off, and boot from your 8GB usb. You should still be able to boot from it and now also have access to your other HDDs.  :p

WARNING!!! Again, this was just me thinking last night and out loud here on the forum. It is a very rough idea. I don't know if it will work exactly as I have written it. Just make sure that you are aware of the risks. WARNING!!!

-------

There are some issues that I can foresee right now. With a Live USB (with or without a persistent file, doesn't matter), everything is run from the main memory (RAM) and the USB is actually accessed very little when compared to a normal HDD.

Yet, by doing a full install to your 8GB, it will be acting as a normal HDD and therefore, I would imagine that, the data would be written/read to it like a normal HDD. Staying away from performance comparisons between HDD and USB Flash Drives, the main issue that I am bringing up is that with constant read/write to your USB flash drive, you lower the lifespan of your USB flash drive. The nands (memory cells) in your usb flash drive have a limited life span. How much or how drastically your will be affecting the life span of your USB flash drive when comparing a live usb to a full install on to the usb, ...... I really don't know. :confused: 

But that is why I stay away from a full install and go with live usb w/persistent file. It works for me. :D

-----------

Also, by having the other HDDs disconnected while you install, it forces GRUB to install to the USB flash drive BUT also doesn't place any chain booters, refferencers, etc, on any other drives. That way it doesn't mess with your windows/ubuntu/GRUB (if you have them) on your other drives.

This should also allow you to update GRUB on your 8GB USB, while booted from it, and shouldn't affect the other HDDs. One little side note, if, while booted from the 8GB USB, you update GRUB, it will show any other OSes found on the computer where you are currently booted. It will add those other OSes to the GRUB menu. Yet, if you move the 8GB usb to another computer, those options to boot the other OSes, found on the previous machine, will still exist in the GRUB menu but, obviously, will not point to any operable OS. Just making sure that is clear.

AGAIN, this is all a little speculation mixed with a little personal experience and creative ideas. Hope it works out. :P

-Spydey :popcorn:

---

### Post by spydeyrch on 2010-07-07
> **skinnyj said:**
> I got it to boot, but it was saying that it was missing the kernel or a main file, so I'm currently redownloading the .iso and see if that might correct the problem.

I have found that UNetBootin can be flaky sometimes and requires sometimes up to 3 different tries to get it to work. On the other hand, Universal USB Installer has worked well for me up to this time, except once when it just did not want to work!  ](*,) It is really a personal choice. I don't think that it would be the .iso that you downloaded but just give it another go with the program again. If you have any questions, let me know. :D

-Spydey :popcorn:

---

### Post by skinnyj on 2010-07-07
It may or may not have been something I did, but here's what I've done since redownload.
1) Ran USB installer to install with a 1GB persistent file.
2) Let it run.
3) Copied a version of GRUB onto the Live drive.

I am currently in Ubuntu, and there isn't any problems coming up. Unless I it was the GRUB I was missing to begin with, it might as well have been the .iso or that I wasn't attempting to do a Live install without a persistent file.

I haven't started installing just yet.

---

### Post by skinnyj on 2010-07-07
I'm currently doing the full install onto the 8gb. I couldn't get it to manually separate, so I just decided to erase and use the whole drive. It is in fact writing all the files to the drive. Luckily I have this backup drive to go off of if I ever need it. I put the boot loader onto the drive as well, so I hope that was the right choice. It should be, because that's where all the files are. I'll post back if any errors come up.

---

### Post by spydeyrch on 2010-07-07
> **skinnyj said:**
> I'm currently doing the full install onto the 8gb. I couldn't get it to manually separate, so I just decided to erase and use the whole drive. It is in fact writing all the files to the drive. Luckily I have this backup drive to go off of if I ever need it. I put the boot loader onto the drive as well, so I hope that was the right choice. It should be, because that's where all the files are. I'll post back if any errors come up.


How is it that you are doing a full install? Meaning, what steps are you taking to do the full install? Just curious. :p  Thanks! :D

-Spydey

---

### Post by skinnyj on 2010-07-07
The install was a success.
I used the install process that was on the Live USB.

---

### Post by spydeyrch on 2010-07-07
> **skinnyj said:**
> The install was a success.
I used the install process that was on the Live USB.

Meaning that you booted from a live ubuntu (CD or usb, doesn't matter) and then did a full install to your 8GB Flash drive? Or did you make your 8GB a live USB w/persistent file? I think that you probably mean the first one, the full install to your 8GB, right?

Have you tried to boot your computer to its normal operating system(s) without the 8GB, CD/2nd USB flash inserted? Just make sure that it boots properly.

-Spydey:p

---

### Post by oldfred on 2010-07-07
I used my install USB to do a full install to a larger 16GB flash drive. 

When I unplugged my install USB, the full install changed from sdg to sdf and would not boot. I would swear it had entries by drive letter in it as I had to manually edit grub to get it to boot. But when I updated the grub install it changed to UUIDs (I swear) and works on my portable as sdb or on my desktop as sdf. I have not tried booting with both USB keys installed to see it that confuses it  or not.

---

### Post by skinnyj on 2010-07-08
> **spydeyrch said:**
> 
Have you tried to boot your computer to its normal operating system(s) without the 8GB, CD/2nd USB flash inserted? Just make sure that it boots properly.


Apologies for not explaining fully last night, I was actually rushing to get some things done, seeing as how we needed to leave to get groceries.

The computer's normal OS (Windows Vista) boots properly. I am using a full install that is on the 8GB. The Live USB works as well. The only test I have left to do is to try and see if it would work on a different computer. My instinct is telling me for some reason that it won't, seeing as I have been on Windows for the longest time.

Right now, everything seems stable. Nothing has come up yet.

Also, is there a setting that smoothes out the font? It seems that the black font blends in with the white background at some points. I can notice the change as I type.

---

### Post by spydeyrch on 2010-07-08
> **oldfred said:**
> I used my install USB to do a full install to a larger 16GB flash drive. 

When I unplugged my install USB, the full install changed from sdg to sdf and would not boot. I would swear it had entries by drive letter in it as I had to manually edit grub to get it to boot. But when I updated the grub install it changed to UUIDs (I swear) and works on my portable as sdb or on my desktop as sdf. I have not tried booting with both USB keys installed to see it that confuses it  or not.

Yeah, that is what I was afraid would happen to the OP's install and system.  That is why I recommended disconnecting all other HDD. I have done something similar to my system.

I installed Win7 on a 1TB the disconnected it. Installed Mint9 on a 500GB then disconnected it. Then installed Ubuntu 10.04 on a 500GB and then disconnected it. After the last install, I connected all three drives, choose the mint9 drive in my bios as the 1st drive then booted from that drive. Once I was in mint 9, I then ran:

```

sudo update-grub2

```

Mint then found itself, Win7, and ubuntu 10.04 and updated its grub menu accordingly.

Then I restarted, waited for the Mint grub menu to come up and booted into ubuntu 10.04. I ran the same command in the terminal and updated my ubuntu grub menu. It added mint9 and windows 7.

The advantages to this are that each drive has its own boot menu on the actual drive and doesn't add or take away to/from the other drives. If I remove a drive, I still can boot into the other remaining drives because at least one of those drives still has a boot menu on it. If I change the order of the drives, I just have to update grub via the terminal and then I am good to go.

So my recommendation is that you do it like this but with your USB drive. Hopefully that all makes sense. :o

-Spydey:p

---

### Post by spydeyrch on 2010-07-08
> **skinnyj said:**
> The only test I have left to do is to try and see if it would work on a different computer. My instinct is telling me for some reason that it won't, seeing as I have been on Windows for the longest time. 

I don't see why not. If you did everything correctly, then it should come up just fine. I would just make sure not to install any video drivers. That is my only piece of advise.


> Also, is there a setting that smoothes out the font? It seems that the black font blends in with the white background at some points. I can notice the change as I type.

Could you possibly take a screen shot and send it to us here in the forums? That would possibly help to understand what you mean. ;)

-Spydey :D

---

### Post by skinnyj on 2010-07-08
Now that I've had a closer look, it seems more of a discoloration, but it's still there. It might be the monitor resolution (1440x900), or something else. It's mostly on the i's in this picture, but every few characters I type, it the text changes definition with the discoloration changing on each character. It isn't a huge problem, but it is a little irritating (for me anyway.) Sorry about the forum stretch.

[IMG]http://img682.imageshack.us/img682/3200/screenshotwk.png[/IMG]

---

### Post by spydeyrch on 2010-07-08
Yeah, I can see what you mean about the 'i'. Strange. To be honest, I don't know exactly what the issue/cause is. I can only guess that it is either an issue with the font or with your video drivers. I would try and install the ubuntu restricted from the software manager. I think that the msfonts are included in that package. If not, then install the msfonts.

That might help but in the end it is probably your video driver that is going to be the issue/cause and the only way to fix this is, as far as I know, to install the appropriate drivers from the software manager. Yet I could be wrong.

-Spydey :p

---

### Post by oldfred on 2010-07-08
This link has a script were the poster installed two video drivers and switches to the correct one.
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

I also install this as part of my normal updates:
sudo apt-get install msttcorefonts

[URL="http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/"]
[/URL]

---

### Post by spydeyrch on 2010-07-08
> **oldfred said:**
> This link has a script were the poster installed two video drivers and switches to the correct one.
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

I also install this as part of my normal updates:
sudo apt-get install msttcorefonts

[URL="http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/"]
[/URL]

Perfect, that looks like it would solve the video driver issue.

Yeah, those mssttcorefonts is what I was referring too but couldn't remember exactly what they were called.

-Spydey :D

---

