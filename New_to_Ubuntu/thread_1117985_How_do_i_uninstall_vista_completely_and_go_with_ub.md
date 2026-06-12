---
title: "How do i uninstall vista completely and go with ubuntu"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by jalehtor on 2009-04-06
I am computer illiterate, but I managed to install Ubuntu unto a completely clean desktop and love it. My mom has a Dell laptop inspiron 1501 which came with Vista, and the Vista has never worked. Despite more memory the computer moves like treacle, it's full of bugs, it's not usable.

So to do her a favor I want to rid her of Vista and install Ubuntu. However, this is mom's computer, and I don't want to destroy it. I need (sorry) specific instructions on how to do this. I went online, and searched here, and can't find what I need.

Do I just pop the Ubuntu disc in and hope that it makes the bad, bad Vista go away? I have no interest in partitioning the computer as Vista right now does not work and she has no info to save. I just want to get rid of Vista in its entirety and replace it with Ubuntu.

I'm sorry for the stupid question.

---

### Post by ubuntu27 on 2009-04-06
If you are using the DesktopCD (a.k.a LiveCD), then when you are in the step to partition the disk, just select "Use Guided partition - **use entire disk**" Something along those lines.

That will delete absolute everything on the HD, and install ubuntu over it.
That means of-course that it will delte Windows, its application, your personal files in Windows, windows viruses (yay!), etc. And make your computer like brand new.

Here is the guide with graphics:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by khelben1979 on 2009-04-06
> **jalehtor said:**
> Do I just pop the Ubuntu disc in and hope that it makes the bad, bad Vista go away?

You got it! ):P

---

### Post by jalehtor on 2009-04-06
> **ubuntu27 said:**
> If you are using the DesktopCD (a.k.a LiveCD), then when you are in the step to partition the disk, just select "Use Guided partition - **use all hard drive**" Something along those lines.

I'm going to use the same cd that I used for my computer. It worked really well, no bugs. So just pop it in? I mean the Vista has half killed the computer and I'm worried that it won't be able to deal with an entirely new program. Is there no way of uninstalling Vista first?What about the thousands of bugs that arrived with Vista? They won't transfer to Ubuntu,will they? As you can see, I KNOW NOTHING about this. 

With profound apologies :???:

---

### Post by jalehtor on 2009-04-06
> **khelben1979 said:**
> You got it! ):P

OK. Pray for me.

---

### Post by Didius Falco on 2009-04-06
> **jalehtor said:**
> I'm going to use the same cd that I used for my computer. It worked really well, no bugs. So just pop it in? I mean the Vista has half killed the computer and I'm worried that it won't be able to deal with an entirely new program. Is there no way of uninstalling Vista first?What about the thousands of bugs that arrived with Vista? They won't transfer to Ubuntu,will they? As you can see, I KNOW NOTHING about this. 

With profound apologies :???:

By choosing the "use entire disk" option from the Live CD, you'll do the  ultimate uninstall of Vista. It will delete the partition(s) that are on the hard drive and make new ones for Ubuntu.

You can't get a cleaner uninstall than that!!

---

### Post by eeeek on 2009-04-06
During the partitioning steps of the install, choose to use the full disk. This should format the entire hard drive and erase everything. 

If you want to be sure of your erase, you can use DBAN - Darik's Boot and Nuke. This is a simple program that wipes your hard drive clean. It can take a few hours, depending on the size of your drive, though. I've used this a lot and can vouch for it.

But yes, the easiest is to pop in the liveCD and run with it. 

Best of luck.

---

### Post by jalehtor on 2009-04-06
I popped in the live cd and what I got are a bunch of icons on my desktop--Bittorent, ubuntu 8.1, bittorent6, infra recorder...this is not what happened when I popped the disc into my desktop. Then I just got the install info. I restarted the computer, and I'm getting the same thing. 

What should I do?

---

### Post by mikeytag on 2009-04-06
jalehtor,
I think what you did before is actually install Ubuntu through the Wubi installer. Which is a way that you can dual boot to Ubuntu easily without fear of messing up your Windows installation.

If you truly want to wipe your drive and dedicate it all to Ubuntu then you need to reboot with the CD in the tray. Your computer should detect the Ubuntu CD and BEFORE it gets to Windows you should be given a few options to Install or try out the Live CD, etc. Do install and choose to use the entire disk when you are presented with that option.

P.S. MAKE SURE ANY FILES YOU NEED/WANT ARE BACKED UP TO AN EXTERNAL DRIVE OR SOMEWHERE ELSE AS THIS WILL ERASE YOUR ENTIRE DRIVE

---

### Post by mikeytag on 2009-04-06
If you are not presented with the options to install Ubuntu before Windows, that means that your computer's BIOS is not setup to boot to CD before your hard drive. It that is the case reply back with your computer brand and model number and I can give you exact directions on how to enable that.

---

### Post by stchman on 2009-04-06
> **jalehtor said:**
> I am computer illiterate, but I managed to install Ubuntu unto a completely clean desktop and love it. My mom has a Dell laptop inspiron 1501 which came with Vista, and the Vista has never worked. Despite more memory the computer moves like treacle, it's full of bugs, it's not usable.

So to do her a favor I want to rid her of Vista and install Ubuntu. However, this is mom's computer, and I don't want to destroy it. I need (sorry) specific instructions on how to do this. I went online, and searched here, and can't find what I need.

Do I just pop the Ubuntu disc in and hope that it makes the bad, bad Vista go away? I have no interest in partitioning the computer as Vista right now does not work and she has no info to save. I just want to get rid of Vista in its entirety and replace it with Ubuntu.

I'm sorry for the stupid question.

Load up the LiveCD and take it for a test spin.  Make sure everything works.  Then install.  There will be an option to use the entire disc.  This will wipe the hdd clean.

---

### Post by jakupl on 2009-04-06
When you turn on the computer, the VERY first thing you see is the bios. It should say how to enter the bios settings "usually F2, Esc or something similar."

---

### Post by jalehtor on 2009-04-06
> **jakupl said:**
> When you turn on the computer, the VERY first thing you see is the bios. It should say how to enter the bios settings "usually F2, Esc or something similar."

Oh no. What are bios??? I get a message on the bottom saying f2 to enter setup, f12 to enter multiboot menu. 

When I press f12, I get a choice of hard drive, cd-rom drive, removable devices, broadcom pxe, diagnostics, and enter setup on the bottom which takes me to her normal screen. 

When I press f2 I am asked for the pw, then get a menu with main, advanced, security, boot, exit menu on top.

This is like gibberish to me! What should I do???

---

### Post by capnthommo on 2009-04-06
hi jalehtor.  ok F12 is giving you the choices of boot up options.  you need to hilight boot from CDRom and press enter.  that will make the machine boot from the live cd in the drive.
you can then go through the steps to try without installing or if you want, to install.  remember when you get to the relevant section to select the option to "use whole disk" - this will remove everything else (vista etc) on the machine and install ubuntu.
dont forgt to carry out the updates once you are installed and then do all the fiddly extras. (sorry if you already know this - but better safe than sorry)
and you HAVE backed up any data files to another storage (CD DVD. Ext HDD or something) haven't you?  would be a shame to lose precious family photos wouldn't it?
good luck
nigel
):P

---

### Post by jalehtor on 2009-04-06
> **capnthommo said:**
> hi jalehtor.  ok F12 is giving you the choices of boot up options.  you need to hilight boot from CDRom and press enter.  that will make the machine boot from the live cd in the drive.
you can then go through the steps to try without installing or if you want, to install.  remember when you get to the relevant section to select the option to "use whole disk" - this will remove everything else (vista etc) on the machine and install ubuntu.
dont forgt to carry out the updates once you are installed and then do all the fiddly extras. (sorry if you already know this - but better safe than sorry)
and you HAVE backed up any data files to another storage (CD DVD. Ext HDD or something) haven't you?  would be a shame to lose precious family photos wouldn't it?
good luck
nigel
):P

There's literally nothing to save on her computer. The Vista never worked well enough for her to actually use the thing, and she's had it for over a year. I'll follow your instructions, thank you!

---

### Post by jakupl on 2009-04-06
> **jalehtor said:**
> Oh no. What are bios??? I get a message on the bottom saying f2 to enter setup, f12 to enter multiboot menu. 

When I press f12, I get a choice of hard drive, cd-rom drive, removable devices, broadcom pxe, diagnostics, and enter setup on the bottom which takes me to her normal screen. 

When I press f2 I am asked for the pw, then get a menu with main, advanced, security, boot, exit menu on top.

This is like gibberish to me! What should I do???

Great. Press F12 and press cd-rom. then it should boot from the cd. (that is the bios.)

EDIT: WOW I'm slow :)

---

### Post by jalehtor on 2009-04-06
It worked! Problem solved, and my 82-year-old mom is working it like a pro. THANK YOU!!!! ):P

---

### Post by Didius Falco on 2009-04-06
> **jalehtor said:**
> It worked! Problem solved, and my 82-year-old mom is working it like a pro. THANK YOU!!!! 

From "computer illiterate" to "My son, the Hero!!" in 4 hours!! That rocks, jalehtor!

---

### Post by capnthommo on 2009-04-07
> It worked! Problem solved, and my 82-year-old mom is working it like a pro. THANK YOU!!!! 

good to hear.  just in case you haven't, don't forget to reboot and go back into BIOS (F12 i think it was, wasn't it?) and reset the boot option to 'boot from HDD' instead of CDRom.  like i said before, you probably have, but better safe?
cheers
nigel
:guitar:

---

### Post by Paidhima on 2009-04-07
> just in case you haven't, don't forget to reboot and go back into BIOS (F12 i think it was, wasn't it?) and reset the boot option to 'boot from HDD' instead of CDRom. like i said before, you probably have, but better safe?

If the boot device was chosen via the F12 boot menu, this is unnecessary.  F12 (occasionally F8) on most modern computers brings up a temporary boot menu, so you can avoid the BIOS Boot Device Boogie every time you need to load from optical.

---

### Post by staticroutes on 2009-04-07
just install ubuntu and follow the instructions and your computer will be cured. trust me, it's easy as pie. :D

---

