---
title: "Problem booting - drops to a shell"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by chrislang on 2009-12-15
I'm using a zonbu mini and ubuntu 8.10. Recently moved house and in the new house the computer won't boot. The ubuntu logo appears but after a while the screen goes black and a message appears.
[COLOR="Blue"]
ALERT! /dev/disk/by-uuid/xxxxxxxxxxxxxxxxx does not exist. Dropping to a shell![/COLOR]

Then I get a message about BusyBox and an (initramfs) prompt.

It doesn't stop there. A whole series of messages appear, including this one:
[COLOR="Blue"]
[  422.447349] ata2.01: revalidation failed (errno=-5)[/COLOR]

And this one:
[COLOR="Blue"]
Buffer I/O error on device sda, logical block 0[/COLOR]

(There's pages and pages of this sort of message - I'm not sure what I'm looking for.)

I've tried a live CD and a usb stick, but got the same problem.

I've spent a long time trying to fix this, including following the suggestions about editing grub in [this thread]("http://ubuntuforums.org/showthread.php?t=1338461") - but without any success. 

Any suggestions would be great. Thanks!

---

### Post by chrislang on 2009-12-15
This just got a lot more interesting - I managed to boot from a live CD (after changing the time and date in BIOS). I tried to install from the CD and things went fine until it got to partitioning the hard drive (which is a 4.1 GB flash drive). The "Prepare partitions" bit is blank and if I click on "Forward" I get an error message:

"No root file system is defined.
Please correct this from the partitioning menu."

When I look in GParted, it says "No devices detected".

---

### Post by sandyd on 2009-12-15
im afraid it seems like your flash drives dead.

---

### Post by chrislang on 2009-12-15
Hi carlee, thanks for this - I'd agree with you, except that late last night I tried one more time and the computer seemed to boot more or less normally. While it was booting a message came at the bottom of the screen along the lines of Incorrect shutdown, checking /dev/sda1. That all went fine and there I was in glorious technicolour ubuntu! I tried another flash disk and that worked as well.

Only trouble is that when I switched the computer on this morning, I got this error message:

[COLOR="Blue"]Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key[/COLOR]

I'm back to square one - anyone got any ideas? Thanks!

---

### Post by sandyd on 2009-12-16
> **chrislang said:**
> Hi carlee, thanks for this - I'd agree with you, except that late last night I tried one more time and the computer seemed to boot more or less normally. While it was booting a message came at the bottom of the screen along the lines of Incorrect shutdown, checking /dev/sda1. That all went fine and there I was in glorious technicolour ubuntu! I tried another flash disk and that worked as well.

Only trouble is that when I switched the computer on this morning, I got this error message:

[COLOR=Blue]Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key[/COLOR]

I'm back to square one - anyone got any ideas? Thanks!
missing bootsector / bootloader

---

### Post by chrislang on 2009-12-22
Thanks Carlee. I've looked for ways of solving the missing bootsector / bootloader. The problem is that they all seem to need me to be able to [boot into the live CD]("http://ubuntuforums.org/showthread.php?t=224351") - which I can't do. Is there any way of installing grub without booting the computer? Or is there something I'm missing?:confused:

---

### Post by chrislang on 2009-12-23
OK, I can boot from a live CD, as long as I first go into BIOS and reset the computer time. (It keeps resetting to 01/01/2002.)

I've installed grub, [following the instructions here]("http://ubuntuforums.org/showthread.php?t=224351").

Everything is fine, until I switch the computer off and pull the plug out of the wall. Then when I try to reboot, I get the error message:
[COLOR="Blue"]
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key[/COLOR]

Back to square one, again.

One more piece of information - while I was getting into BIOS, I saw this error message flash past: 

[COLOR="Blue"]CMOS checksum bad[/COLOR]

Sorry this is all coming in bits and pieces, but that sounds to me like it could be the problem - in which case, have any zonbu users also had this problem? And if so, what did you do?

---

### Post by chrislang on 2010-01-01
My computer now works fine as long as I don't pull the plug out of the wall. I asked Zonbu whether they had any suggestions - here's the reply I got:

> Dear Chris,

I'm sorry to hear you're having problems with your Zonbu Mini. Unfortunately, that's most likely a hardware problem, in which case there's nothing we can do. You can try reinstalling Ubuntu, which will resolve the issues if it's software-related, but I'm skeptical.

Best,
David for the Zonbu Team

---

### Post by iMisspell on 2010-01-01
sounds like your bios battery is dead.
If you open your computer up, look for a small battery that looks like a watch-battery and test it if you have a volt meter or buy a new one (there normaly cheap, 5-10 bucks - bring the battery to the store with you - almost any where would have them, food-shopping store, local deily, watch store ;) anywhere).

---

### Post by QIII on 2010-01-01
Sounds like one of the following (in descending order of likelihood):

Your CMOS battery is dead or getting there.  (Clock change makes me most suspicious of this.)

Your CMOS memory contents are corrupted.

Your BIOS needs to be updated.

You have some other problem with your motherboard.

There is a sinister possibility that you have a deep virus (even before your OS loads).

First thing I'd do is check that the battery hasn't jangled loose.  If that's not the case, the cheapest first step in diagnosis would be to replace the battery.

---

