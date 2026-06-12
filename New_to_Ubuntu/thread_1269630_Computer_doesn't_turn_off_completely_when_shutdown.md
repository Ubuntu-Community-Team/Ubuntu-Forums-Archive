---
title: "Computer doesn't turn off completely when shutdown selected"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by flamefury on 2009-09-18
Hey all.

Every time I finish using Ubuntu (9.0.4) and try to shutdown my computer, the OS does everything with the splash screen and the loading bar. When that's finished, the computer appears to glitch and displays 6 black screens and a blinking underscore at the top-left corner. I believe pressing the Enter key here causes all six lines to move down one line from where they are. It doesn't turn off after this, so I'm forced to push and hold down the power button.

Any ideas of what could be causing this? The terminal command for shutdown doesn't work either and neither does restart. I'm dual-booting with Vista64 if this is important, and the computer also turns off after using Vista's shutdown button.

---

### Post by FreewheelinFrank on 2009-09-18
My laptop never shuts down completely on its own. It does with Windows. I think it's because hardware makers tailor BIOS settings to Microsoft's interpretation of the standards, rather than the actual standards themselves. I've heard that Microsoft's erratic implementation of BIOS standards was deliberate. Don't know if there's any truth to the story.

[http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf](http://antitrust.slated.org/www.iowaconsumercase.org/011607/3000/PX03020.pdf)

There may be a solution for your hardware- try Google.

---

### Post by flamefury on 2009-09-21
Well, I'm running this on an ASUS G50Vt-X5, which apparently as a secondary Linux-based OS called Express Gate (that I touched for about five seconds before saying it's not worth much time)...I don't see why Ubuntu would be shot off the block in terms of shutting down ability, but I don't think Express Gate was meant to do very much besides act as shortcut links to access (supposedly) common locations.

If it really is a Microsoft request for the hardware manufacturer's, that's a sneaky and dirty thing to do, especially considering Linux still works fine (for the most part) and they're only hindering things like shutting down and sound (which I'm missing, but I do believe that's possible to fix).

---

### Post by anewguy on 2009-09-21
Something to try:

edit (as su) the /boot/grub/menu.lst file:

find the "kernel" line that is being selected when you normally boot, then go to the end of it, press the space bar and add:

acpi=force

then save the file, reboot and try to shutdown again.

If that doesn't work, can always try the oppposite:

In the same file on the same line, change "acpi=force" to "acpi=off pci=noacpi apm=force", save the file, reboot and try to shutdown again.

I *think* it's ACPI but not not positive.  At any rate, I had this problem with an older PC.  Adding this option fixed it for me on that old PC.  You might also have an option in your system's BIOS setup for power management.

Dave :)

---

### Post by browng on 2009-09-21
I had this exact same problem, dual boot with vista 64 and using ubuntu 64 Jaunty.  Just "acpi=force" worked for me, thanks a bunch!

---

### Post by flamefury on 2009-09-22
That works occasionally, although since I'm trying to fix my sound, the consistent amount of changes I'm using to try and get that to work may be interfering.

Thanks for the tip, though!

---

### Post by anewguy on 2009-09-23
Guess I skipped over what your initial problem is - the black screens.  If you can never get to a readable window, then this suggests that you may need a video driver.  If it's only at shutdown, that would be another issue. 

What brand/model of computer are you using?

Can you get access to the command line? (when you get your black screens, try holding down ctrl, alt and pressing F1 and see if you get a logon prompt).

If you can get access to the command line, do the following and post the results back here:

lspci <press enter>

lsusb <press enter> (if this is a laptop - some laptops' video show up as usb devices)


Post the information back here and we'll go from there.  BTW - what type of audio problems are you having and what have you been doing to try to get it to work?

Dave :)

---

### Post by browng on 2009-09-23
I spoke too soon...

Should I ask about this in a different thread?

I wasn't having the exact same issue, when my computer was shutting down it would display the splash screen, then when the bar finished (un)loading the colors would glitch for a second before the whole screen was black and just a white underscore in the top left. Only one screen and underscore, not six. But no matter how long I waited there the computer didn't shut down.

Adding "acpi=force" fixed that some of the time, but whenever I close the lid during any part of shutdown the same thing happens. When I close the lid, the current setting is to blank the screen.

Ideas?

I also included lspci output.
[SIZE=1]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
[/SIZE]

---

### Post by flamefury on 2009-09-24
> **anewguy said:**
> Guess I skipped over what your initial problem is - the black screens.  If you can never get to a readable window, then this suggests that you may need a video driver.  If it's only at shutdown, that would be another issue. 
Yes indeed, only at shutdown.
> What brand/model of computer are you using?
Think I said before, ASUS G50VT laptop.

I'd continue on, but I just switched to Karmic Koala Alpha6, and it seems the issue's been fixed on that end. I put up the output for lspci on this thread:
[http://ubuntuforums.org/showthread.php?t=1273802](http://ubuntuforums.org/showthread.php?t=1273802)

Maybe I shoulda stuck with Jaunty awhile longer to find a fix for this issue...

> BTW - what type of audio problems are you having and what have you been doing to try to get it to work?
I have two other threads ATM that I've mentioned this. I don't really mean to shoot so many off at once, but I can't help but mention my sound issue in every post (>_>, craving the fix, methinks). If only that were fixed, Ubuntu would be puuuurfect.
In short, there is no sound. No splash start up, no MP3 playing, no audio in flash videos or java games, just, silence.

However, both speakers and microphone are functional. This is the most odd thing, but if I stick up the iMic and Speaker levels high enough in alsamixer, the microphone picks up sounds in my room (more often than not, the keyboard and mouse) and projects it out the speakers. I can hear my own voice out of the speakers if I talk. This was while I was on Ubuntu 9.10. The beeping noises also play if I hold backspace in terminal or do something similar.

To try and fix this, I attempted just about everything mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689)

The two main methods there was to add irqpoll in the boot loader and to add lines in alsa-base.conf specifically aimed at snd-hda-intel options. In addition, I tried updating alsa-occ, tried uninstalling and reinstalling alsa related packages, tried uninstalling pulseaudio, and tried installing RealTEK drivers (although I may want to attempt this one again), and most recently, tried switching to Ubuntu 9.10. People claimed success with Alpha5, haven't heard much about Alpha6...

---

