---
title: "Trying to get Ubuntu Live CD persistence to work..."
date: 2009-12-26
forum: New to Ubuntu
---

### Post by AKD1 on 2009-12-26
Hi, I'm VERY new to Ubuntu and Linux in general, so please excuse my naivete/stupidity.

I'm trying to persist a live instance of Ubuntu linux 9.10 on my dell latitude. I've successfully created and run Ubuntu Live CD. However I'm now trying to run the Live CD session persistent. I've followed the instructions carefully at the Ubuntu wiki "https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence" however my data and settings still don't get saved after I reboot. I'm trying to use my 250MB Lexar JumpDrive USB drive as my persistent media. 

After following the instructions on the wiki and rebooting, my desktop shows a "casper-rw" ext3 folder with a single 16KB folder labeled "lost+found" (though I can't open it). "Casper-rw" has 207.2 MB free. 

Also there is no obvious persistent menu label after rebooting. 

Another peice of information: I've tried to include the "persistent" keyword before and after all of the various different options already listed after hitting F6 on the start up screen and seeing the Boot Options. 

Any help is greatly appreciated!!!

Amit

---

### Post by lrcaballero on 2009-12-26
Welcome to Linux/Ubuntu, if I understood your thread correctly and excuse me if I didn't, but when you play around with a Live CD just to see if you like the Distro that you are trying, you may NOT save anything!!! what ever changes you make while exploring through a Live-CD and you reboot again everything gets lost and for a good reason, so that it doesn't mess with your Hard Drive.

Good Luck,

Luis

---

### Post by tom.swartz07 on 2009-12-26
> **AKD1 said:**
> Hi, I'm VERY new to Ubuntu and Linux in general, so please excuse my naivete/stupidity.

I'm trying to persist a live instance of Ubuntu linux 9.10 on my dell latitude. I've successfully created and run Ubuntu Live CD. However I'm now trying to run the Live CD session persistent. I've followed the instructions carefully at the Ubuntu wiki "https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence" however my data and settings still don't get saved after I reboot. I'm trying to use my 250MB Lexar JumpDrive USB drive as my persistent media. 

After following the instructions on the wiki and rebooting, my desktop shows a "casper-rw" ext3 folder with a single 16KB folder labeled "lost+found" (though I can't open it). "Casper-rw" has 207.2 MB free. 

Also there is no obvious persistent menu label after rebooting. 

Another peice of information: I've tried to include the "persistent" keyword before and after all of the various different options already listed after hitting F6 on the start up screen and seeing the Boot Options. 

Any help is greatly appreciated!!!

Amit

Hi!

As it turns out, persistence will not work for a liveCD, you can, however have persistence on a liveUSB install though.

It seems like youve covered all of the steps, its just that you were using the wrong medium.

Like the previous poster said, LiveCDs were meant to erase everything after its shutdown. USB's on the other hand allow you to save it.


Head over to [www.pendrivelinux.com](www.pendrivelinux.com) and read up for some more info

---

### Post by AKD1 on 2009-12-26
Wow! Thanks for the very quick replies!

I'd love to boot from a USB however my computer's BIOS doesn't allow me to boot from USB, only to boot from CD. Since I'm still very inexperienced with Linux, I'd like to have a persistent instance of Ubuntu WITHOUT having to install it on my hard drive and risk clobbering up any XP files.

What would you suggest? 

Thanks again!

---

### Post by Miljet on 2009-12-26
The wiki how-to indicates that this method doesn't work on all versions, and it doesn't show that it has been tested on either 9.04 0r 9.10. So it is possible that it won't work with your version (9.10).

---

### Post by tom.swartz07 on 2009-12-28
> **AKD1 said:**
> Wow! Thanks for the very quick replies!

I'd love to boot from a USB however my computer's BIOS doesn't allow me to boot from USB, only to boot from CD. Since I'm still very inexperienced with Linux, I'd like to have a persistent instance of Ubuntu WITHOUT having to install it on my hard drive and risk clobbering up any XP files.

What would you suggest? 

Thanks again!

Since you dont want to risk any of your data, I would suggest using Virtualbox. This will allow you to 'install' Ubuntu just as you would install a program. There are numerous threads here on the forums with how-to guides to set up virtualization. For more information, Lifehacker.com has a TON of guides on virtualbox.

Have fun!

---

### Post by alienkid10 on 2010-02-17
Hello I have this EXACT same problem. I am using a 1GB casper-rw file on a USB stick that IS plugged in during boot. I boot off the liveCD and F6 esc add "persistent" change things reboot and nothing has been saved besides a 12KB lost+found folder. What can I do to troubleshoot this? And yes the computer I want to boot from doesn't boot USB. Ubuntu 9.10 Followed the same guide. Now I Did use USB creator and booted from that and did the same boot steps as above 'cept booting from USB on the one computer I own that boot USB and it does save. But again can't boot from USB

---

### Post by C.S.Cameron on 2010-02-18
This thread has discussion on persistent Live CD.

[http://ubuntuforums.org/showthread.php?t=1388919](http://ubuntuforums.org/showthread.php?t=1388919)

---

### Post by sandyd on 2010-02-18
use wubi? (although that may end sadly and turn into one of those wubi nightmare threads)

---

### Post by marshmallow1304 on 2010-02-18
> **AKD1 said:**
> I'd love to boot from a USB however my computer's BIOS doesn't allow me to boot from USB

I've been in that boat before.  You can use [PLoP boot manager]("http://www.plop.at/en/bootmanager.html").  You can put it on a floppy or CD, then boot from the floppy or CD with your USB drive plugged in and use PLoP to boot from the USB.  Of course, you'll need a bigger USB drive if you want it to hold both the Ubuntu image and a persistence file.

---

### Post by despoteuodia on 2010-03-01
why not use a boot cd to chainload the flashdrive on a persistent usb install? (i also was unable to use 9.10 live cd with usb persistence)

perhaps this will help? 
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

it should yeild a cd to boot a usb device for when you cannot natively boot from usb disks.

---

### Post by alienkid10 on 2010-03-01
becuase I still want windows to access to the drive without sifting though 100s of files and folders. And I don't want the life of the drive to decreasing exponentially by all the reads required for a bootable USB.

---

### Post by RobCr on 2010-03-24
> **alienkid10 said:**
> becuase I still want windows to access to the drive without sifting though 100s of files and folders. And I don't want the life of the drive to decreasing exponentially by all the reads required for a bootable USB.

Give Puppy Linux a try, and be pleasantly surprised -
a) Runs totally in ram (and thus frees up the CD drive)
b) Very fast
c) IT KNOWS how to persist, without having to research your heart out
When you close your session, it prompts you to Persist your settings, data, etc.

The other distro's should also try it, and learn the proper way to provide persistence.

---

### Post by prometeo2008 on 2011-06-07
Hi guys

I have the same problem. I run Live Linux Mint 9.0. I did a live linux Mint USB, because I wanted persistence for getting rid of installing the same apps all the time, but the experience was not good due to I was hacked (I suppose) while I was on the Net and the next usb boot the OS didn't work. The solution I thought it should be live CD persistent. That way OS would be in a read-only (CD-ROM) mean and the installed apps in the persistent casper-rw USB ext 3 4096 bytes/cluster partition. I did it, but no way. The lost and found new created folder seems to be corrupt and there is no customization surviving to the next boot :(. By the way, in Mint, at the boot time  i have to use [TAB] instead <F6> to reach boot parameters or kernel arguments and add AT THE END (does it matter?) persistent --. To make things worse I am clueless because, i do not know whether is there any bootlog and where it is for getting clues on what changes I should make :KS
Help me, please!

---

