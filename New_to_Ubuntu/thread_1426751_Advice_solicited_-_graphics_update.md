---
title: "Advice solicited - graphics update"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by zukzuk on 2010-03-10
Hello, all - total Ubuntu newbie here.  I've just installed Ubuntu 9.10, KK, on my old Dell Optiplex GX240 box after upgrading RAM to 1gb, and installing a new 40gb HD.  I have wireless connection to my network and I am able to print wirelessly to my Brother laser printer.  I'll have sound in a few days when my speakers get here.  So far, things work well.  But I have an ATI RAGE 128 PRO Ultra GL AGP graphics card in the machine, and the display of web sites at 1280x1024 (5:4) falls a bit short of the glorious display I get on my iMac (1920x1200).  Further, under System > Preferences > Appearances > Visual Effects, Ubuntu says I can only have the basic desktop without visual effects, whatever those are.

I know from searching the forum that my ATI RAGE is too old to perform well with Ubuntu.  So I'd like to purchase a graphics card compatible with the system, install it, perhaps install a proprietary driver (I have no proprietary drivers at all at present), and without further ado have improved graphics and an enhanced desktop.  My research has suggested that NVIDIA cards and drivers are somewhat problematical with Ubuntu.

My question: what inexpensive graphics card will allow me the above benefits without hassling me and requiring terminal work?  (Since I'm new to Ubuntu, I find the sudo bit to be somewhat daunting.  I haven't worked out the file structure or commands yet.)

TIA.

---

### Post by coffeecat on 2010-03-10
> **zukzuk said:**
> My research has suggested that NVIDIA cards and drivers are somewhat problematical with Ubuntu.

:-s

I think Mr Google must have been having a bad day to serve you up such information. :wink: I predict a flood of posts advising nvidia.

> **zukzuk said:**
> My question: what inexpensive graphics card will allow me the above benefits without hassling me and requiring terminal work?

Get an nvidia Geforce card in the 6***, 7*** or 8*** range (for inexpensive). Install it. Go to System > Administration > Hardware Drivers and enable the proprietary driver with one mouse-click. Reboot and enjoy all the visual effects.

No terminal work at all! :)

---

### Post by albert s on 2010-03-10
*display
description: VGA compatible controller
product: G72 [GeForce 7500 LE]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list rom
configuration: driver=nvidia latency=0
resources: irq:24 memory:dc000000dcffffff
memory:c0000000cfffffff(
prefetchable)


^^^^^^^^^^^^
my graphics output.
all working fine for me and Im new to all this and really dont know what Im doing at all.
needed a few pointers from the good people on here to get it all sorted nicely,
but NO major issues at all in the end, just my stupidity in doing it wrong.  :o

---

### Post by jim Kane on 2010-03-10
> **zukzuk said:**
> Hello, all - total Ubuntu newbie here.  I've just installed Ubuntu 9.10, KK, on my old Dell Optiplex GX240 box after upgrading RAM to 1gb, and installing a new 40gb HD.  I have wireless connection to my network and I am able to print wirelessly to my Brother laser printer.  I'll have sound in a few days when my speakers get here.  So far, things work well.  But I have an ATI RAGE 128 PRO Ultra GL AGP graphics card in the machine, and the display of web sites at 1280x1024 (5:4) falls a bit short of the glorious display I get on my iMac (1920x1200).  Further, under System > Preferences > Appearances > Visual Effects, Ubuntu says I can only have the basic desktop without visual effects, whatever those are.

My question: what inexpensive graphics card will allow me the above benefits without hassling me and requiring terminal work?  (Since I'm new to Ubuntu, I find the sudo bit to be somewhat daunting.  I haven't worked out the file structure or commands yet.)

TIA.

                                       see this thread
    [LEFT][/LEFT]
    [LEFT][http://ubuntuforums.org/showthread.php?t=1423459](http://ubuntuforums.org/showthread.php?t=1423459)[/LEFT]
    [LEFT][/LEFT]
    [LEFT]Nvidia 8500GS is a good compromise between cost and performance, 



JK
[/LEFT]

---

### Post by Jerry N on 2010-03-10
You aren't going to get that "glorious" 1200 x 1920 wide screen display you want unless you buy a wide screen monitor capable of 1200 x 1920 in addition to a new video card.

Jerry

---

### Post by zukzuk on 2010-03-10
Thanks, people.  I've re-thunk my previous impressions about NVIDIA.  And now I'm off to do some purchasing research.

Cheers.

---

### Post by zukzuk on 2010-03-10
Point taken, Jerry N.  My Envision 22" 9110 monitor on my Ubuntu box is only good for 1280x1024 @ 85hz.  I'll have to do something about that.  Maybe for Christmas.

Based on info given above, I've just purchased a NVIDIA GeForce 8400 GS 512MB DDR2 PCI Graphics Card.  Thanks for the help.

---

### Post by coffeecat on 2010-03-11
> **zukzuk said:**
> Based on info given above, I've just purchased a NVIDIA GeForce 8400 GS 512MB DDR2 PCI Graphics Card.  Thanks for the help.

Perfect! Just what I've got. Mine works fine.

Enjoy Ubuntu and good luck getting that 1920x1200 monitor. That card will cope with that resolution very well. It does in this household. :wink:

---

### Post by zukzuk on 2010-03-16
So, I thought I was gold - it was not to be.  I've gotten myself into a mess.  The instruction book that came with my new NVIDIA GeForce 8400 GS 512mb PCI graphics card is aimed at Windows, and does not say at any point to remove the old graphics card.

With both cards installed, the old one in the graphics slot and the new one in the adjacent PCI slot, I placed the NVIDIA CD in my CD drive and invoked System > Administration > Hardware.  Ubuntu found and I installed recommended driver 185.  (Did not install other stuff on CD.) It took a long time, but I thought I was gold.  New driver appeared to be activated, I saw no way to inactivate the Ubuntu open-source driver for the old card, and the dialog box requested reboot.  Accomplished normal Ubuntu shutdown.

Changed monitor cable to new card connector.  Perhaps it was too early and this was a mistake, but I thought the old driver was now disabled, and the new one active.

Rebooted.  Got normal Dell splash screen but no further.  Black screen thereafter.

Since I had no display, had to power off with power button instead of graceful shutdown.  Connected monitor cable to old card connector.

Rebooted.  Got normal Dell splash screen, then menu for normal/recovery mode.  Selected "normal" (probably a bad choice).  Got "input not connected" and amber light on monitor, which is NORMAL for this box - always had that temporarily during boot.  But now this continued, the monitor amber light and "input not connected" display.  Monitor is apparently getting no video signal.  I suspect the drivers for the old graphics card are disabled.

Removed new graphics card, leaving old graphics card in.

Rebooted.  Got normal Dell splash screen but no further.  Amber light and "input not connected" box wandering around screen forever.

Removed old graphics card.  Reinstalled new graphics card.  Connected monitor cable to new card.

Rebooted.

Got normal Dell splash screen.  Continuous green light on monitor to signify monitor was receiving video, but continuous black screen.  I would expect new graphics card to adjust to monitor's max resolution of 1280x1024.

If I hold down shift while I boot, (the KK hot-key for boot menu) I don't get the expected normal/recovery mode menu.  Instead I get a short BIOS screen (not the one I'd prefer), and a keyboard failure notice telling me to strike F1 to continue, F2 for setup.  Neither has effect.  I don't really believe the keyboard is bad.  I did check the connection to the computer, and it's okay.  I thought I had a spare keyboard to try, but I don't.

Something I've noticed: when shutting down power with Dell's main power button in preparation for re-trying for the normal/recovery menu, it powers down very quickly, as if it hasn't gone all the way to Ubuntu.

Powered down, removed new graphics card, re-installed old one.  Connected monitor cable to old card.

Rebooted, holding down shift key.  Got same keyboard failure notice.  F1 and F2 inoperative.

Bought a new keyboard, hooked it up.  Still using old graphics card.  Booted.  Dell splash screen.  Keyboard failure notice.  F1 & F2 keys have no effect, so problem is NOT keyboard.

Placed KK demo/install CD in CD drive.  Booted in hope system would boot from CD even though I cannot get to BIOS setup.  Got keyboard failure notice.

Removed old graphic card, installed new one and hooked it up.  Rebooted.  Got keyboard fail notice without invitation to strike F1 or F2, followed shortly by GRUB loading notice, then black screen.  Continuous green light on monitor - says it's getting video - I think.  Depressed monitor menu button, and it briefly said "Autoconfiguring - wait".  Long wait, no joy.  Side note: speakers do not make Ubuntu welcome sound, so I suspect Ubuntu isn't loading.

Bottom line, I obviously screwed up somewhere, but I don't know where and I don't know how to correct it.  [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by coffeecat on 2010-03-16
> **zukzuk said:**
> With both cards installed, the old one in the graphics slot and the new one in the adjacent PCI slot, I placed the NVIDIA CD in my CD drive and invoked System > Administration > Hardware.  Ubuntu found and I installed recommended driver 185.  (Did not install other stuff on CD.) It took a long time, but I thought I was gold.  New driver appeared to be activated, I saw no way to inactivate the Ubuntu open-source driver for the old card, and the dialog box requested reboot.  Accomplished normal Ubuntu shutdown.

Let's stop there. Have I got this right? You installed the Nvidia card next to the ATI card and booted up with the ATI card connected to the monitor and installed the nvidia proprietary driver? :-s That was not the best thing to do.

Point of information - Hardware Drivers did not take anything off the nvidia CD which only has Windows stuff. Hardware Drivers would have downloaded the Linux proprietary nvidia driver from the Ubuntu repository. The nvidia 185 driver is right for the 8400GS card and you don't need to deactivate the open source driver. That's done for you. 

Anyway, most of the rest of your post can be explained by a confused BIOS. Whatever state Ubuntu may or may not be in, you need to reset the BIOS - but take that ATI card out first. You'll have to search the Dell documentation for how to reset the BIOS. On a "normal" motherboard there is a jumper for this, but Goodness know what you do in a Dell. You might want to take out the CMOS battery for a few seconds while you're about it. You'll need to reset the clock when you next reboot if you do this.

Once you've reset the BIOS, boot up (without the ATI card) and go into the BIOS and make sure the nvidia card is being detected by the BIOS. Then see if Ubuntu will boot up.

---

### Post by zukzuk on 2010-03-16
^^ Okay, I copied and pasted your post to a text file so I'd have it in front of me.

Yes, I did install the NVIDIA card next to the ATI card.  Stupid perhaps, but the NVIDIA instruction book never said a word about removing the old one.

I'll google for the Dell reset, not having any original Dell docs because it's an inherited computer.  As for taking out the CMOS battery, if I lose the time, who cares?  I know how to reset that.

I'm off to try your suggestions.  Thanks.

---

### Post by coffeecat on 2010-03-16
Don't beat yourself up about it. Consider it a learning experience. :) I believe that newer machines can cope with parallel graphics cards for dual monitor use, which is perhaps why the instruction book made no mention of taking the old one out. I should imagine that yours wasn't designed for this and maybe this is why the BIOS got confused.

---

### Post by zukzuk on 2010-03-16
^^^ @coffeecat

Worked the problem all evening, with a lot of googling.  I'd already downloaded the manual for the Dell Optiplex GX240.  The file name is 4g172.pdf.  I also have ONLY the NVIDIA card installed, and the monitor is connected to that.  The main front panel power button is faintly lighted with a green LED.  Google suggests a flashing amber LED indicates power supply troubles, so I should be good.

The MB has a password jumper (installed, to enable passwords) and an RTCRST jumper (not installed, real time clock reset & can be used for troubleshooting purposes).  There seem to be no other jumpers, and none that relate to BIOS.

The Dell manual seems silent on the subject of resetting BIOS.  Google suggested that removal of the AC power plug, removal of the battery, and pressing the power button would reset BIOS.  I did this, then powered up.  Screen read:

Invalid configuration information - please run SETUP program.  (It's looking good at this point!)

Performing automatic IDE configuration…
Primary master: IDE Disk Drive
Secondary master: CD-ROM Reader
Time-of-day not set - please run SETUP program
Alert! System battery voltage is low.  (I assume they mean the CMOS battery - it's a 3 volt battery, and I measured it at 3.07 volts under no load)
Strike the F1 key to continue.  F2 to run the SETUP utility (two short beeps from the machine)

No key has any effect.  (Bummer!) Had to power off using power button.  (Remember, I have two keyboards, one PS2 and one brand-new USB).

Rebooted while tapping F2 key.  Should have gotten BIOS SETUP, but it went right on through to a blank screen.

There are four green lights on the back of the machine, used for diagnostic purposes.  Four greens means, according to [http://support.dell.com/support/edocs/systems/opgx240/en/ug/problems.htm#1105025](http://support.dell.com/support/edocs/systems/opgx240/en/ug/problems.htm#1105025), normal operating condition after POST.  No action is recommended.  One to four yellow lights means BIOS, video, or other problems.  BUT solid green lights and a beep code (other than the correct single beep) indicates "A problem was detected while the BIOS was executing."  I have two beeps, so the problem seems BIOS-related still.  But the beep code table at the site above doesn't seem to include two beeps.  The closest it comes is 1-3, which I interpret to be beep(interval)beepbeepbeep.

I removed the password jumper and booted.  It seemed to have the same effect as removing the battery, in that it did another IDE check.  Booting thereafter simply went from Dell splash screen to black screen with monitor LED lit green.

I placed the jumper on the RTCRST jumper pins, thinking I might enter troubleshooting mode.  Depressing the power switch had no effect whatsoever.  No boot, no noise at all.  That jumper inhibits booting.  I saw no screen action, either.

If I can ever get to a BIOS SETUP screen, I'll set the primary video controller to auto (for PCI) instead of AGP.  That MIGHT fix the no-display problem.

Bottom line, I think you've got the right idea in having me to reset the BIOS.  I can reset it seems, but I can't get to a SETUP screen any more.  I'm temporarily out of ideas.

---

### Post by coffeecat on 2010-03-17
The only other idea I have at the moment is that the PS2 keyboard might have really failed - as the BIOS was telling you before. And if that Dell is more than a few years old, the BIOS may not be able to detect a USB keyboard unless you get into the BIOS to change a setting. For which, of course, you need a PS2 keyboard.... You get my drift. It's not the first time I've come across this catch-22. I've had more than one motherboard (not Dell) like this.

Can you borrow a PS2 keyboard to test this theory? You'll need to check that manual again for the setting. It will probably be something unintuitive if it's anything like the BIOS's I've used. I seem to remember it was something like "enable legacy USB" which was a bit odd since USB keyboards are somewhat more up-to-date than PS2 ones.

**Edit:** about the CMOS battery. Your measured voltage suggests it's OK, but if that's the original battery it might be worth changing at some point. It will fail sooner or later. They only cost small change and it might prevent yet another complaint from the BIOS. But i don't think it's critical at the moment.

---

### Post by zukzuk on 2010-03-17
^^^ @coffeecat - I think you may be correct about the keyboard.  See below.

03/17/2010 - Unable to access BIOS SETUP, I took the Dell box to Bad Boy Computers in Orange City.  Told the tech my goals were to get the new NVIDIA card working so Ubuntu boots all the way, and to get access to BIOS SETUP.

Tech took the box to the back room, returned shortly to say he'd accessed BIOS SETUP using the old ATI card.  How he did that, I had no idea, since I couldn't.  After that, I went back and watched.  He then set BIOS to recognize the PCI NVIDIA card, and he installed BOTH the ATI card in AGP and the NVIDIA card in PCI at the same time.  He installed the NVIDIA drivers.  Since Bad Boy doesn't work on Linux, he hooked up the older 20gb HD with Windows XP on it.  Hooked up two monitors, one on the ATI and one on the NVIDIA.  Booted successfully to Windows, with desktop displays/icons on both monitors.  Hooked up the newer 40gb HD, set BIOS to recognize it.  Saw the Ubuntu HD on Windows disk management.

At home, I hooked up two monitors, one to the ATI and the other to the NVIDIA, attempting to duplicate the tech's experience.  Just as the tech learned, I can access BIOS SETUP only on the ATI, not the NVIDIA.  I further learned I can access BIOS SETUP only using an old PS2 keyboard, not a new USB keyboard.  Didn't notice which he used.

First I booted Windows XP.  Found the ATI monitor showed the Dell splash screen, then nothing, then the XP desktop background without icons.  It continued to display this background without icons even when browsing the internet on the NVIDIA monitor.  The NVIDIA monitor displayed no Dell splash screen, did display the XP welcome screen, and finally displayed the XP desktop with icons.  The desktop was fully functional, and I could adjust the monitor resolution using NVIDIA setup.  But I wondered why the mostly useless (except for BIOS access) ATI monitor didn't mirror the NVIDIA monitor.

I speculate the Dell splash screen and any BIOS video shown on any monitor comes from BIOS through the graphics card, but not FROM the graphics card.  Is that correct?

Disconnected the Windows HD, and connected the 40gb Ubuntu HD as primary.  Reinstalled Ubuntu 9.10 from CD.  Rebooted.  I get video only on the monitor connected to the ATI card.  I think I know the reason - I've not yet installed the proprietary NVIDIA drivers.  BUT, installing proprietary NVIDIA drivers will disable the ATI open-source drivers, leaving me no ATI video for BIOS SETUP access (I think).

Question #1: How can I install NVIDIA proprietary drivers WITHOUT disabling Ubuntu's ATI drivers?  Surely Ubuntu's made provisions for dual monitors.

Question #2: When booting Windows as a test, why didn't the two monitors display approximately the same video, since NVIDIA drivers had been installed?

Any replies, assume I'm a total dummy and go step by step.  TIA.

---

### Post by coffeecat on 2010-03-17
> **zukzuk said:**
> I speculate the Dell splash screen and any BIOS video shown on any monitor comes from BIOS through the graphics card, but not FROM the graphics card.  Is that correct?

Yes, the Dell splash and the BIOS text are all generated in the BIOS and passed to the graphics card for output to the monitor.

But for the rest, I'm afraid you've gone beyond where I can help. I have little direct experience of Dells and have only once or twice poked around in a Dell BIOS to help a friend, and I can't remember much of the details and how it differed from the BIOSs I'm used to. Your Dell BIOS is clearly more capable than I had thought - although I'm puzzled as to why you can't get it to recognise a USB keyboard.

As far as Ubuntu dual-monitoring with an ATI and an nvidia card, I don't know. I've never heard of it being done.

Personally, if that was my machine, I would consider the ATI card a distraction, so I would run it with just the nvidia card, see if I could boot up with it (as a default it will use the open source driver), and then install the proprietary driver once I was in the GUI. But it seems that something in the BIOS is stopping you doing this. It's very odd. I'm out of ideas.

---

### Post by zukzuk on 2010-03-17
^^
I'm back where I was, browsing wirelessly and printing wirelessly in Ubuntu.  I'll work with it.  Thanks for all your help.  :P

---

