---
title: "Newbie w/ many issues"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by honkanen on 2010-06-23
I am currently dual-booting Windows 7 and Ubuntu 10.04.  I'm really wanting to make this work but even Ubuntu is kicking my *** here.  Here are some of the issues I'm experiencing.  I'm googling around trying to find things to try but if you guys have any suggestions, I'd appreciate it.

1. For the life of me, I can't get my Dell Photo Printer 926 installed on here at all.  Sure don't want to keep saving what I want to print, copying it over onto my Windows partition, shutting down and rebooting the computer, logging into Windows and printing from there.

2.  Screen resolution.  Screen gets garbled (various colors and lines all over the screen so i can't see Ubuntu at all) when I switch screen resolutions. If I switch the res from 1152 x 864 to anything else such as 1280x1024 or 1024x768 it gets so garbled, I'm forced to hold down the power button to turn off the PC and reboot.  My video card is an ATI Radeon X300.

3.  My desktop (really noticeable with maximized windows such as firefox) exceeds the size of my LCD screen.  The outside edges of the desktop or maximized window are just out of sight on what I'm seeing on my screen.  For example, with a maximized window, the screen is too far to the right so I can't see the vertical scroll bar.  I can fix this by using the buttons on my LCD monitor to change the  horizontal positioning until I see everything normally but when I reboot, it goes back to the same problem again. This does not happen in Windows.

4.  My Dell SK-8135 keyboard has a Volume Wheel which I always use to adjust the volume.  Works fine in Windows but is messed up on Linux.  It's about a 50/50 chance that the volume will actually increase when I move the wheel, the other half of the time, when I move the wheel the volume mutes completely.  This also happens with alsamixer through terminal.  My audio controller is: Intel Sigmatel STAC92xx HD audio.

5.  When I try to use any 3D screensaver such as the ant spotlight, after it goes to screensaver, the whole PC freezes and I have to do a cold reboot on my PC.

That's all I can recall off the top of my head right now.
Thanks for any help on this!

---

### Post by Zeike on 2010-06-23
> **honkanen said:**
> 
2.  Screen resolution.  Screen gets garbled (various colors and lines all over the screen so i can't see Ubuntu at all) when I switch screen resolutions. If I switch the res from 1152 x 864 to anything else such as 1280x1024 or 1024x768 it gets so garbled, I'm forced to hold down the power button to turn off the PC and reboot.  My video card is an ATI Radeon X300.

3.  My desktop (really noticeable with maximized windows such as firefox) exceeds the size of my LCD screen.  The outside edges of the desktop or maximized window are just out of sight on what I'm seeing on my screen.  For example, with a maximized window, the screen is too far to the right so I can't see the vertical scroll bar.  I can fix this by using the buttons on my LCD monitor to change the  horizontal positioning until I see everything normally but when I reboot, it goes back to the same problem again. This does not happen in Windows.

5.  When I try to use any 3D screensaver such as the ant spotlight, after it goes to screensaver, the whole PC freezes and I have to do a cold reboot on my PC.


I'd be willing to bet that these three problems are related to your video card.  ATI cards are notorious for causing problems in Ubuntu, and linux in general. 

I don't have an ATI card myself, so I can't be too specific, but I suggest you try making sure the binary ATI driver is enabled in "System"->"Administration"->"Hardware Drivers".

---

### Post by Peter09 on 2010-06-23
You should see your printer in 
 
System->Admin->Printers

---

### Post by honkanen on 2010-06-23
Thanks for the replies.  I had tried to go into "System"->"Administration"->"Hardware Drivers" but the window comes up completely empty with nothing listed in there.  You're probably right though in that those 3 are related to my video card but I'm not too sure what I can do about it.

---

### Post by snip3r8 on 2010-06-23
10.04...what can i say?im still using Karmic because Lucid gives me hell with graphics drivers (but thats an nvidia card)

---

### Post by howefield on 2010-06-23
> **honkanen said:**
> I can't get my Dell Photo Printer 926 installed on here at all.

Many Dell printers are actually Lexmark printers, so you might have success with a Lexmark driver. There are a couple of sites explaining how, just search them out.

---

### Post by pablolie on 2010-06-23
Seems most of your issues are related to the video driver.

This topic may be of help...
[http://ubuntuforums.org/showthread.php?t=1466210](http://ubuntuforums.org/showthread.php?t=1466210)

---

### Post by honkanen on 2010-06-23
Thanks for the suggestion on the Lexmark driver.  It looks like my Dell printer is the same thing as the Lexmark X3450 and that Lexmark printer has a driver specifically for Linux.  I'll try it out tonight.

If I keep having these video and audio issues, I may download Karmic Koala to see if an earlier version of Ubuntu is any better.

I'll take a look at the link the to Ubuntu ATI thread. 
Thanks guys.

---

### Post by honkanen on 2010-06-23
Weird.  I just read through the 3 pages on the Ubuntu ATI link you gave to me but in the end, those guys are still having the same issues and nothing is solved even though the thread is marked as "Solved".

---

### Post by howefield on 2010-06-23
> **honkanen said:**
> Weird.  I just read through the 3 pages on the Ubuntu ATI link you gave to me but in the end, those guys are still having the same issues and nothing is solved even though the thread is marked as "Solved".

Good luck, Ubuntu (as most distros) is as sweet as a nut with supported hardware.  Trying to soldier on with hardware not up to it is no fun. Is the graphics card integrated or can it be replaced ?

That's what I'd do, replace with a cheapo nVidia, even an old/low spec one.

---

### Post by honkanen on 2010-06-23
It's a Dell Dimension 5150 with the default hardware so it's probably integrated.  I found linux drivers for this off of the ATI website so I'll give them a shot later.  I didn't think that by switching from Windows to Linux I would need to also replace my all-in-one printer and my graphics card and hope it works with those 2 new purchases.

---

### Post by QIII on 2010-06-23
> **Zeike said:**
> I'd be willing to bet that these three problems are related to your video card.  ATI cards are notorious for causing problems in Ubuntu, and linux in general. 

Do please stop with the FUD.  The issue here is that the particular card in question is a "legacy" card.  It is no longer supported by ATI.  They have produced a "legacy" driver, but it may or may not work with the latest version of Xserver.

Here's the real deal on AMD/ATI cards.  I wish people would stop dispensing FUD.

When ATI was ATI, they provided little support, if any, for Linux.  That much is true.

ATI was bought by AMD in 2007.  AMD/ATI worked very hard to get on the Linux train.  They now have superior Linux support with a particular sweet-spot for Ubuntu.  Just exactly the opposite of your implication.

For the last several versions of Ubuntu, AMD/ATI has been sure to provide the latest and greatest driver in the Ubuntu repositories by the final release of the Ubuntu version.  That means that Ubuntu users have the driver before it is even available for public consumption for other distros.

Phoronix has even had several headlines line "AMD/ATI gives more candy to Ubuntu" because of that.

If you have a non-legacy AMD/ATI card, then the Ubuntu repo has the latest driver when the new version of Ubuntu is released.  You will have absolutely no problems with your card if you install the driver from the Ubuntu repo.  AMD/ATI cards are "notorious" for *working *in Ubuntu now.

For legacy cards, you will either have to use the legacy driver provided by AMD/ATI or the open source driver.

And, just by the way, if you have a legacy nVidia card you will either have to use their legacy driver or the open source driver.  I had a GeForce2 MX400 on an older machine that simply would not work in Jaunty.  nVidia is not a silver bullet.

For the OP:  You have to understand something about OEMs and the hardware they produce.  Hardware OEMs write drivers for their hardware, not the developers of OSs.  Windows does not support your printer.  The OEM has created a driver that works in Windows.  If the OEM has not created one for Linux or has created a poor one, that is on the OEM and it is not an indictment of Linux or any particular distro. However, this is a real problem and difficult for the Linux community.  Such things are legitimate considerations when contemplating a switch to Linux.  If there is something that you need that simply will not work in Linux, then you should use what works for you.  Choice is what matters.  Use what works.

---

