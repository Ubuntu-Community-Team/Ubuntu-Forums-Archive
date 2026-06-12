---
title: "Graphics card problem with install of 10.10"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by gilbot53d on 2010-12-30
I have installed Ubuntu 10.10 on two old Dell machines that I am going to give to a hard-up friend for her children.  I had installed, in each of them, a PCI graphics card:

Dell Optiplex GX60 + ATI Radeon 9250
Dell Dimension 2350 + NVidia GeForce 6200

My kids have been running Windows XP on them for years with no problem.

When I tried to run the install from the Ubuntu 10.10 CD, on both machines, the system hung when displaying the Ubuntu logo with the colour-changing dots. I tried disabling the graphics cards in BIOS to no avail and then succeeded with the install by removing the cards from their slots completely. I now have Ubuntu 10.10 installed on both machines minus their graphics cards.

I did try installing the Radeon card into the Optiplex and resetting the BIOS Graphics to 'Auto' in the hope that Ubuntu would recognise it and load the appropriate driver. However, Ubuntu refused to load at all on reboot and I had to re-install it completely, minus Radeon card of course.

I really would like to install these graphics cards as the PCs are so ancient and feeble they need all the help they can get.

Any advice would be welcome.

Please let me know what information would be of value and I will post it. I am a complete Linux noob and I am struggling to understand most of the terminology used on these boards.

---

### Post by XeonBloomfield on 2010-12-30
If you can try older Ubuntu LiveCDs...

I have situation with old Dell laptop where only Ubuntu 8.04 LTS and olders worked.

---

### Post by alzie on 2010-12-30
If you have a copy of 10.04 you might want to try that.  As it is a Long Term Support (LTS) release its not like you using an old version.

XeonBloomfield's idea of using an older distribution (8.04 LTS)should work.  It was released when the video cards you are using were far more common and should have better driver support.  I think Envy was available in the repos at that time to aid in the install of both ATI and nVidia drivers.

---

### Post by gilbot53d on 2010-12-30
Many thanks Xeon and Alzie, I've got the idea. I did try 10.04 early on in my attempts on the Optiplex but it failed. 

I am currently downloading 8.04, I will try that with the cards in situ.

---

### Post by cariboo on 2010-12-30
You could also try setting the nomodeset option from the menu screen. Press any key when you se the screen with the two icons at the bottom, then press F6, select nomodeset using the arrow keys, then press esc, then press Enter.

---

### Post by sparker1 on 2010-12-30
> **cariboo907 said:**
> You could also try setting the nomodeset option from the menu screen. Press any key when you se the screen with the two icons at the bottom, then press F6, select nomodeset using the arrow keys, then press esc, then press Enter.
 
Yes, I would recommend this. I had a similar problem and this worked. However to make the change permanent follow the instructions on this thread:
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9795785#post9795785](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9795785#post9795785)
 
See the posting by davidryderuk in the thread.

---

### Post by gilbot53d on 2010-12-31
Wow, thanks everybody. 

I have a plan, however my wife is not sharing as we need to prepare for family visitors this weekend and the PCs were on the kitchen table. Activity is suspended for a day or two.

Many thanks again, happy new year to you all.

---

### Post by gilbot53d on 2011-01-01
I managed to sneak some time with one of the machines. In the hope that I could retain 10.10 I did the following:
[LIST=1]
[*]Changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
[*]Shut down and installed the graphics card in the PCI slot
[*]Booted up into BIOS changing the primary graphics device to 'Auto' 
[/LIST]
The result is that the graphics card is providing the output to the monitor, but what I am getting is a list of what look like errors followed by:

Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have requested /sbin/init.
No init found. Try passing init= bootarg

Below this is a utility called Busybox with a prompt = (initramfs)

I removed the graphics card and reset the Primary Video Adaptor in BIOS to 'Onboard'. I now get a GNU GRUB screen with recovery mode options. I have tried recovery mode and non-recovery mode options and I get the same 'Killed' message as before. Looks like I have trashed the installation.

Can I remedy this situation?
If no, is it worth continuing to try with 10.10 or should I attempt to install the 8.04 version with the graphics card in situ?

---

