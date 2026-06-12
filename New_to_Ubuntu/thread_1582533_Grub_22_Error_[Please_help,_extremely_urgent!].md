---
title: "Grub 22 Error [Please help, extremely urgent!]"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by idku on 2010-09-26
I have Windows XP and [2] copies of gOS on my computer. 

When gOS installed, it booted first. All the time. I didn't mind it much since gOS was for the children, and they used the desktop the most. Now i've used Easeus to remove the partitions that gOS were on. 

It did fine, then on the reboot I get this : 

> 
GRUB Loading stage1.5.

GRUB loading, please wait. . .
Error 22


I can't load from a USB. I can't load from a recovery CD. I can't load from my 'XP Home Edition Upgrade' disk. I can't type. I can't do ANYTHING. 

I'm a (more than) full time student and I need access to XP immediately. This is a crisis for me, and i'm absolutely lost... please please, I have found other threads that relate to this but unfortunately I don't understand any of them and I can't even begin to take the steps that are mentioned.

---

### Post by sikander3786 on 2010-09-26
You'll need to boot from a Windows cd and fixmbr. What do you mean by I can't load from a recovery CD? Did you configure Bios to boot from the CD instead?

Previously, was the system set to dual boot Windows and gOS? If so, does the Grub menu still show up or it is that error only that you get?

---

### Post by pytheas22 on 2010-09-26
You should be able to boot to a USB stick or CD directly from BIOS--no need to go through grub to do that.  When your computer first turns on, the first or second screen that's displayed should tell you which key to press to access the boot menu--usually it's a key like F8 or escape.  Press that key and a message should pop up asking you which medium you want to boot to, and select your USB stick or CD instead of the hard disk.

If you don't see anything about a boot menu, see if there's something mentioning "Setup" or "Configuration."  By entering that, you should be able to set the boot order of your devices, and you can tell it to boot to CD or USB before the hard disk.

If you can boot to a CD or USB, you can restore grub from there.  The easiest way to do so would be to install Ubuntu somewhere on the hard disk, and along the way the installer should configure grub to boot all of your operating systems.  You can also set up grub without installing a new operating system using the grub-install command, but to give you instructions for that, I'd need to know a little information about your partitioning layout.

Also, do you see the grub error message directly after you get past the BIOS screens, or do you have the opportunity before that to enter the grub menu by pressing escape?  If the latter, try pressing escape to get into the menu and let me know if you can open an editor (I think you press 'e' to do that but I'm not positive; look for instructions on the screen).

---

### Post by idku on 2010-09-26
@ [sikander3786]("http://ubuntuforums.org/member.php?u=806649") 

I was able to create a set of 2 HP Recovery Discs** when I got the computer**. When I press 'ESC' on the big 'HP' splash screen, I can select the CD rom, but I get the GRUB error. This happens no matter what I select on that 'Boot Screen'.  I can't 'choose' the discs at all. 

I'm not sure what a 'GRUB menu' is, but i'll tell you what happens if I press 'power' and don't touch anything. 

1. Turn on desktop.
2. I get the HP startup/splash screen giving me 3 options. ESC for Boot Menu. F1 for Setup. F10 for System Recovery.
3. I get the error. 

That's it.

---

### Post by idku on 2010-09-26
> **pytheas22 said:**
> and select your USB stick or CD instead of the hard disk

I've done this to try and access the CD, but it doesn't do a thing. Just gives me the Error 22 message. I can't boot from a USB, I don't have one with anything on it to boot.


> The easiest way to do so would be to install Ubuntu somewhere on the hard disk, and along the way the installer should configure grub to boot all of your operating systems.How do I make a 'live USB' thing (such technical terms I know... ) on my UNR based netbook? 

> Also, do you see the grub error message directly after you get past the BIOS screens,Yes I do. No other screens available.

---

### Post by sikander3786 on 2010-09-26
If the system just passes by the CD-ROM during boot, I doubt either the CD Drive is not working, the disc is defected or the disc is not even bootable.

Press and hold down the Shift key as soon as the computer gets past the Bios screen. Do you see the GRUB menu? Is Windows listed in there? Try with both Right and Left Shift if not successful first time.

You can create a live USB from UNR from System > Administration > Startup Disk Creator. You'll need an Ubuntu distro image to do that.

---

### Post by pytheas22 on 2010-09-26
> I've done this to try and access the CD, but it doesn't do a thing. Just gives me the Error 22 message. I can't boot from a USB, I don't have one with anything on it to boot.

That's weird--that sounds like it's not really booting from CD.  Are you positive your CD is bootable and not damaged?  Can you boot to it in another computer?  Have you tried multiple CDs?

You could also try unplugging the hard drive cables, if this is a desktop system.  Then it should definitely be forced to boot to CD.
> 
How do I make a 'live USB' thing (such technical terms I know... ) on my UNR based netbook? 

The easiest way is to use Ubuntu's tool at System>Administration>Startup Disk Creator.  If you don't have any bootable Ubuntu system available, you can also do it from Windows; take a look at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

EDIT: sorry, I missed the UNR bit.  But I see sikander3786 already answered that question more competently anyway.

---

### Post by idku on 2010-09-26
> **sikander3786 said:**
> Press and hold down the Shift key as soon as the computer gets past the Bios screen. Do you see the GRUB menu? Is Windows listed in there? Try with both Right and Left Shift if not successful first time.

This doesn't give me a menu, though it does take an extra second or two before giving me the same GRUB error 22 message.

> You can create a live USB from UNR from System > Administration > Startup Disk Creator. You'll need an Ubuntu distro image to do that.

Will do this now.

---

### Post by sikander3786 on 2010-09-26
> 
you can also do it from Windows; take a look at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I thing there is a bug with the new version. Please take a look at this thread when you are free.

[http://ubuntuforums.org/showthread.php?t=1582312](http://ubuntuforums.org/showthread.php?t=1582312)

That is why I've another strong reason for recommending [unetbootin]("http://unetbootin.sourceforge.net").

---

### Post by idku on 2010-09-26
Thanks you two so much for helping. I'm moving a little slower because I really don't understand this technical stuff (and honestly the situation is making me physically sick) so bear with me, i'll be a couple of minutes.

---

### Post by idku on 2010-09-26
> **pytheas22 said:**
> The easiest way to do so would be to install Ubuntu somewhere on the  hard disk, and along the way the installer should configure grub to boot  all of your operating systems.

I'm currently trying this, I created the USB as directed and it's loading... just an update.

---

### Post by jtarin on 2010-09-26
> 1. Turn on desktop.
2. I get the HP startup/splash screen giving me 3 options. ESC for Boot Menu. F1 for Setup. F10 for System Recovery.
3. I get the error. Choose F1 for setup and this will put you in the bios setup where you can configure the boot order of your devices. Choose CDROM/DVD to be your first boot device.Save and exit. If you have a good CD it will boot from the CD.

---

### Post by idku on 2010-09-26
It installed. 

It restarted.

I got to select Windows, but at the Windows XP screen it 'flashed' and went BACK to the HP splash screen, like it had restarted. Now it's running CHKDSK and i'm not sure what's going on. 

(another update is all)

---

### Post by idku on 2010-09-26
I've got Windows up... however... it's stuck in a loop. Tells me it's found new hardware, named 'Generic Volume' or 'Volume' and do I want to 'Continue Anyway' or 'STOP Installation' because it's not passed compatibility or something... I swear, if I didn't NEED Windows at this point, i'd wipe it from my desktop too!

I know this is an Ubuntu forum... but are there any ideas on what this development is? :confused:

---

### Post by sikander3786 on 2010-09-26
Might be the USB drive plugged in that was used in installation of Ubuntu ;-)

---

### Post by idku on 2010-09-26
Maybe. But it's not plugged in anymore... -sigh- ...now, back to my original issue. I wanted to wipe out Ubuntu completely, so that only Windows remains on my desktop. I need to fix the partitions so that it's all in one 'piece' again... WITHOUT doing this allllllllllllll over again. Any suggestions?  :(:(

---

### Post by sikander3786 on 2010-09-26
Unless you are able to boot from a Windows XP CD, it can't be done :-) Ubuntu was made to sit there LOL :-) Just joking.

If you remove Ubuntu, GRUB will still be there until you do fixmbr from a Windows CD. Let it sit there until you get a working/bootable Windows XP CD.

---

### Post by idku on 2010-09-26
So... install a Linux distro next to Windows, and let it sit there? Ok... I can do that, assuming you can tell me how to make Windows default as the first OS in the list...

I know i'm way off the original topic here, but i'll make a new thread if needed... ?

---

### Post by sikander3786 on 2010-09-26
Install startupmanager

```

sudo apt-get install startupmanager

```

It shows up under System > Administration > StartUp-Manager. Choose your default OS there.

---

### Post by egalvan on 2010-09-26
EasyBCD has an option to automatically restore the MBR that Windows needs.

[http://neosmart.net/gallery/photo/view/neosmart/EasyBCD/EasyBCD+2.0/Bootloader+Setup/](http://neosmart.net/gallery/photo/view/neosmart/EasyBCD/EasyBCD+2.0/Bootloader+Setup/)


EasyBCD, an under-appreciated piece of work :)
I use it constantly.

---

### Post by idku on 2010-09-26
Then that's what i'll do... i'll mark the thread appropriately once I complete everything, I have to wait for the other distro of Linux (that I wanted to put on in the first place... ) is downloaded and installed to know if everything will work harmoniously together. Thanks a lot to everyone who helped.

---

### Post by jtarin on 2010-09-26
> **egalvan said:**
> EasyBCD has an option to automatically restore the MBR that Windows needs.

[http://neosmart.net/gallery/photo/view/neosmart/EasyBCD/EasyBCD+2.0/Bootloader+Setup/](http://neosmart.net/gallery/photo/view/neosmart/EasyBCD/EasyBCD+2.0/Bootloader+Setup/)


EasyBCD, an under-appreciated piece of work :)
I use it constantly.I agree completely, but I have been accused of "zealotry" in trying to make my point here. I think it is essential in a dual boot environment when you want to preserve your boot environment and retain control.

---

### Post by idku on 2010-09-26
For now... Lucid is happily existing on my desktop alongside XP. I'll look into the 'BCD' (can I PM you, Mr. Zealot, should I need assistance?) and i've installed Startup Manager, which put XP up first. 

Ahhhh... I feel better y'all. Thank you so much... I really have a lot to do for classes and this was a huge problem. Thank you for the swift replies!  :P:):)

---

### Post by jtarin on 2010-09-26
> **idfku said:**
> For now... Lucid is happily existing on my desktop alongside XP. I'll look into the 'BCD' (can I PM you, Mr. Zealot, should I need assistance?) and i've installed Startup Manager, which put XP up first. 

Ahhhh... I feel better y'all. Thank you so much... I really have a lot to do for classes and this was a huge problem. Thank you for the swift replies!  :P:):)
Yes you may...and I might add there are other ways to dual boot Linux without Grub overwriting your MBR.

---

### Post by egalvan on 2010-09-28
I had suggested EasyBCD because the OP stated

**used Easeus to remove the partitions that gOS were on**

and

**need access to XP immediately**

sounded like an emergency :)

Since he seemed to have only Windows left, and needed immediate access.
I thought to mention EasyBCD. :P

Yeah, one should have a good understanding of what one's system is doing, and  how to solve problems,
but sometimes "quick_and_dirty" is wanted...

BTDW, I donate ($$) to the authors of EasyBCD, as it works very well,
and I use it in my consulting business.

---

### Post by jtarin on 2010-09-28
> **egalvan said:**
> I had suggested EasyBCD because the OP stated

**used Easeus to remove the partitions that gOS were on**

and

**need access to XP immediately**

sounded like an emergency :)

Since he seemed to have only Windows left, and needed immediate access.
I thought to mention EasyBCD. :P

Yeah, one should have a good understanding of what one's system is doing, and  how to solve problems,
but sometimes "quick_and_dirty" is wanted...

BTDW, I donate ($$) to the authors of EasyBCD, as it works very well,
and I use it in my consulting business.

While I wouldn't classify it as something dirty, I would classify it as a quick and elegant solution to something overwriting my MBR when I don't think it needs to be there and would like a clean solution to dual boot. I think if everyone knew and understood EasyBCD there would be even more adherents to this solution. Kudos for you in donating and using in your business. I am not affiliated with this software only a user. I have dual booted Linux for more than 13 years and have never had Lilo or Grub in my MBR.....BSD boot manager either. Until Vista I always used the boot.ini file to boot and always had both operating systems boot flawlessly.Now I use EasyBCD to edit the Win7 boot manager.

---

