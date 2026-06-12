---
title: "Can't Boot Unbuntu 10.4 Blinking cursor"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by pdetine on 2011-05-29
Hello, looking for some help.
 
I have a dell dimension desktop computer in which I loaded Ubuntu10.4 on it.  Used it for 3-4 months with it being my 8 year olds main computer.  Not sure what had happened but now all I get is a blinking cursor at start-up.
 
In F12 boot I tried to boot the CD drive with the Ubuntu disk I have in it, nothing happens besides it saying retry F1 or got to set-up F12.
 
When I go to F12 reboot this is what I see:
 
On Board or USB CD ROM Drive
On Board or Floppy Drive
On Board SATA Hard Drive
 
*  System Set-up
*  Hard Drive Diagnostics
*  Boot to Utility Partition
 
Any help would greatly be appreciated.
 
Thank You.

---

### Post by Thewhistlingwind on 2011-05-29
You want that first option.

---

### Post by pdetine on 2011-05-29
I did use the first but didn't get any results.  Just the message to "F1 to reboot or F12 to set-up"

---

### Post by drs305 on 2011-05-29
When this started, did you get the Grub menu before the blinking cursor? If not, can you get the Grub menu by holding down the SHIFT key as it boots?

---

### Post by NormanFLinux on 2011-05-29
Download and install PLOP Linux to your hard drive. Very old computers have no provision for booting a USB stick from the BIOS. PLOP will install a virtual second hard drive to your real one so the BIOS will treat a USB stick as a real hard drive and you can boot from it. And of course you can install to the computer's hard drive from the USB stick live environment like you can from an optical disc drive.

---

### Post by pdetine on 2011-05-29
I was able to get to the Grub Menu, and this is what I saw:
 
GNU Grub  Version 1.98-1Ubuntu10
 
Ubuntu, with Linux 2.6.32-30 Generic
Ubuntu, with Linux 2.6.32-30 Generic (Recovery Mode)
Ubuntu, with Linux 2.6.32-28 Generic
Ubuntu, with Linux 2.6.32-28 Generic (Recovery Mode)
Ubuntu, with Linux 2.6.32-27 Generic
Ubuntu, with Linux 2.6.32-27 Generic (Recovery Mode)
Ubuntu, with Linux 2.6.32-24 Generic
Ubuntu, with Linux 2.6.32-24 Generic (Recovery Mode)
 
Memory Test (Memtest86+)
Memory Test (Memtest86+,Serial Console 115200)
 
(The several commands to navigate a selection)
 
What's my next step?
 
Thank you

---

### Post by drs305 on 2011-05-29
> **pdetine said:**
> 
What's my next step?

If it's a video problem, you have several options. First try selecting the first Recovery Mode entry. Select to boot in safe video mode. If you get to the desktop, go into the System menu, Additional Drivers/Hardware, and try to install a video driver for your system.

If that doesn't work, another option to get you to the Desktop would be to highlight the first menu entry, press 'e' to edit it. Go to the 'linux' line and remove *quiet splash* and add *nomodeset*. Then press CTRL-x to boot and again try to install a video driver.

This works fairly often when the issue is a video problem, especially with nvidia cards.

---

### Post by pdetine on 2011-06-04
I tried both options (from both paragraphs) with no success.  The following appeared:
 
A whole bunch stuff . . . . . .  .
 
Begin: running /scripts/ local-bottom . . . . .
Done
Done
Begin: running/ scripts/ init-bottom .  . . . . 
Done
_ (this is a blinking cursor)
 
 
 
And that's it.
 
 
Any other options?
 
Thanks for your help.

---

### Post by drs305 on 2011-06-04
From the LiveCD, download and extract the Boot Info Script. Run it and post the contents of RESULTS.txt.  It will give us an idea of the status of your boot files.

Click on the "BIS" link in my signature line to take you to the script page.

---

### Post by pdetine on 2011-06-05
I'm not sure how you download from the live CD.  I put the Ubuntu CD in the drive with nothing happening due to the fact that I can't even get past the blinking cursor or Boot it from the CD drive.
 
I apologize for my computer ignorance.

---

### Post by drs305 on 2011-06-05
As far as the blinking cursor, when do you see it? Do you see a Grub menu first? (Try holding down the SHIFT key as the comptuer boots to see if the Grub menu appears). The blinking cursor, if it appears after the Grub menu, may mean you need to install a video driver. We can help you with that if necessary.

If you need to use the LiveCD, when you power on the computer does the CD spin up? You want the computer to try to boot the CD before it tries to boot the hard drive. Normally you set this in the BIOS setup, which you enter by pressing a key such as the DEL key or one of the F* keys. Sometimes the screen tells you which key to press.

If you can get into BIOS, then you would find the boot options page and have the system try to boot the CD first.

---

