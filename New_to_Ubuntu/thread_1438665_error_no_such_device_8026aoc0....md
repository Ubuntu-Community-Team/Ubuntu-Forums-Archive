---
title: "error: no such device: 8026aoc0..."
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Pitirim on 2010-03-25
Hi -
I just installed Karmic Koala successfully (I thought) from a live CD.
After  about 20 minutes of black screen after the "Installing System" screen disappears, I tried to remove the CD.  The door didn't open.  So I  decided to restart the computer.
When  I reboot using IDE-0 as the first boot option I get a screen which is  headed 
"GNU GRUB version 1.97~beta4" 
with the following 4  options:
--------------
Ubuntu, Linux 2.6.31-14-generic
Ubuntu,  Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest 86+)
Memory  test (memtest 86+, serial console 115200)
--------------
If I  choose either of the first two options I get:
"error: no such device:  8026aoc0-6ae5-49c9-912d-e6ced9832f7a
Press any key to continue..."
Pressing  a key takes me back to the previous screen ("GNU GRUB version  1.97~beta4").
I searched the forums for this error number but the  thread that seems to apply is beyond my current computing ability:
[http://ubuntuforums.org/showthread.php?t=1301144](http://ubuntuforums.org/showthread.php?t=1301144)

When  I use the GUI from the live CD to install by double-clicking the  "Install Ubuntu 9.10" icon in the virtual desktop, the "Prepare disk  space" page in the "Install" screen tells me "This computer has Ubuntu  9.10 on it".  So I quit that screen.

I have also tried to  reinstall, this time choosing "erase and use the entire disc".
Same  result.

I set the BIOS to boot from my second CD drive.
After the installation this drive would not open either.
Same result.

With both CD drives the drive is active (the hdd is also active) after the screen goes black but eventually this activity stops and the screen remains black.

The Md5SUM is ok and I've checked the CD for integrity.

The  computer has a new hdd.  (A SATA drive with an IDE-to-SATA adapter in the IDE  socket)
Mobo is Gigabyte GA-7DX Rev4.1
Cpu is AMD Athlon 1.4MHz
1028Mb  RAM
I was running Win XP SP3.
I'd been thinking about Linux but  never dared take the plunge.
This is how I finally got here:
I got  the computer with Win ME preinstalled.  I upgraded to XP from the  upgrade CD which came with the computer.  A couple of weeks ago the old  hdd died.  I made what I thought was a slipstreamed (i.e. XPSP3)  bootable CD from my Win (ME to XP) upgrade CD and ran it only to  discover that it is in fact not viable because I need an ME CD at the  EULA stage (and I didn't think of making a bootable CD while my old hdd  was still alive).  I mention this because I suppose it is just possible  that the hdd is somehow hidden to the Ubuntu boot process as a result of  this failed Win XP install (just trying to cover as many bases as I can think of).

Can anyone help please?

---

### Post by Pitirim on 2010-03-25
That should have been 1.4GHz for the AMD processor :)

---

### Post by Pitirim on 2010-03-28
I found the answer here:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408)
(You may need to register first.  The topic heading there is:
"Grub 2 problem, error: no such device")
As a new user of Ubuntu I found the whole thread to be instructive for showing aspects of the community dynamic behind ariving at a solution: a) there is a lot of activity; b) the level of experience with the operating system, both possessed (especially my own) and expected, is typically widely spread; c) the level of communicative ability (including mine) is a complicating factor in deriving benefit from the contributions.  This is well shown in the following:
A meta-suggestion in post #56 (re information management) is taken up in post #96 (which distills the information contained in the entire thread) and then the next post (#97) refines this distillation.
I'm only mentioning this because it brought home to me the fact that, although the resources are defintely here, making the right connections can be a discouraging hurdle, and this thread (link above) seems to neatly encapsulate the ups and downs of the quest.
I know it can be dangerous to generalize but I can't be that peculiar (can I?) :D
Anyway, this particular problem is now solved for me and I'm looking forward to tackling my yet-to-be-revealed shortcomings, which I know will be many...

---

