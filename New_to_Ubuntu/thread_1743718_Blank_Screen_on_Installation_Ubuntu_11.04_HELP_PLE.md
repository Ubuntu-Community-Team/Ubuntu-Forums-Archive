---
title: "Blank Screen on Installation Ubuntu 11.04 HELP PLEASE"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by prodo123 on 2011-04-29
I DO NOT mean after installation. I mean** during the installation process itself.**


[LIST]
[*]Ubuntu 11.04 32-bit
[*]SiS Mirage 3 Graphics M671
[*]3GB RAM
[*]1.73Ghz C2D CPU
[*]1280x800 Screen
[*]4GB USB drive
[/LIST]

I created a bootable USB from both UNetbootin and Ubuntu's USB creator thingy found on the downloads page. For UNetbootin, I tried Netboot. For both, I tried "Try Ubuntu without installing" and "Install Ubuntu on this computer". Both of these options went through a whole lot of text, then the screen that says this:

Ubuntu 11.04
  .   .   .   .

Which I suppose is the loading screen. Then, knowing from previous installations, the installation GUI is supposed to show up. But instead, **a black screen (which is still backlit) shows up.** I read multiple times that the mismatch of graphics drivers on Nvidia chipsets can cause this, but I do not own Nvidia; I own a SiS Mirage 3 M671. Ubuntu 10.10 at least went into a VESA 800x600 mode; this cannot even display a mouse pointer. 

Like all tech issues I post in the forums, there is no error code. Ubuntu does, however, try many different USB methods until it can find the right driver, disabling IRQ 25, 28 and 29 in the process.

Also, whatever boot parameters I use in the Ubuntu-provided USB gives a "No Kernel Image Found", and holding shift brings up a console screen with "boot:" and the same error for whatever I type in.

[B]WILL SOMEONE PLEASE HELP? I REALLY NEED UBUNTU INSTALLED.
[/B]Thanks!

---

### Post by prodo123 on 2011-04-29
Anyone?
Please help!!

---

### Post by prodo123 on 2011-04-30
I could REALLY REALLY use some help right now.

---

### Post by fonsi2099 on 2011-05-04
Just the same problem!!! any solution or idea, Gurubunteros thanks

---

### Post by faizalnex on 2011-05-04
Just the same problem :(
but mine is ubuntu natty 64bit

---

### Post by ubun2warrior on 2011-05-04
i am facing the same problem with 11.04 although this happened on my laptop on my desktop it was ok.. no clue..

---

### Post by grahamdoel on 2011-05-05
Seen this? [http://ubuntuforums.org/showthread.php?t=1741941](http://ubuntuforums.org/showthread.php?t=1741941)

---

### Post by tkelito on 2011-05-05
I've had issues with broken downloads and not having my flash drive formatted in FAT32.  I went to install Kubuntu 11.04 today and it failed 3 times in a row, reformatting from Ext4 to Fat32 was the trick.

---

### Post by EGamerHDK on 2011-05-05
It could be some kind of problem with the USB as it has given me problems before, but running it off of a Live CD always works. I would definitely try that first.

---

### Post by Missi0n on 2011-05-07
I've had the same problem.. you need to boot into recovery mode (hold down shift on boot) and install the drivers in "additional Drivers"

---

### Post by _andsoitis on 2011-07-13
Boot it into GRUB and the press "c" before you do anything else. go down to the second option and press "c" again.

Replace the words "quiet splash" with "nomodeset" and press enter. Then press "b" to boot and it will install. I had the exact same problem and this worked for me. About 6 minutes ago.

---

### Post by _andsoitis on 2011-07-13
Excuse me. Everywhere i said "c" in the last post, use "e" instead. Apparently my memory really is that bad. Don't use the letter c, use e as in "edit".

---

