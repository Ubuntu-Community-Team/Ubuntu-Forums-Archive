---
title: "How to upgrade from Ubuntu 8 (Hardy) to Ubuntu 10 (Lucid)"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Cant on 2010-06-11
I've downloaded the .iso, written it to a CD, put the thing in and rebooted the computer but nothing happens. I don't get any instructions or anything when it starts. It just boots normally.

---

### Post by oldsoundguy on 2010-06-11
It should .. it should go to the desktop. BUT the desktop should be a different looking one vs Hardy.
That is unless it is not BOOTING from the CD .. check your bios and make sure your CD is FIRST in the boot up sequence.  When the CD launches you should get a screen asking what you want to do. (always run the disk check and the memory test) and then select RUN (the first option) .. it should just chug along to the desktop.

I did the ON LINE upgrade, but did as you have done, saved the ISO and burned and tested it FIRST .. then did a dump of the ~/home folder to a thumb drive.

THEN I did the on line update. On 4 computers! .. only issue I had was the carry over of an overly filled xorg.conf file that had to be removed (rm /etc/X11/xorg.conf) in terminal, then re-booted and the NVidia default driver worked out of the box for my Cinema display .. even the rotate function (which used to be done by adding a line in xorg) was there!  (no need for the restricted driver .. but I do not game and I don't run a bunch of eye candy .. for that, the restricted driver may be needed.)                

So did NOT need the CD or the back up .. but nice to have JUST IN CASE!

---

### Post by mikewhatever on 2010-06-11
What made you think there were instructions on upgrading on the cd in the first place?
[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

### Post by Cant on 2010-06-11
> **oldsoundguy said:**
> It should .. it should go to the desktop. BUT the desktop should be a different looking one vs Hardy.
That is unless it is not BOOTING from the CD .. check your bios and make sure your CD is FIRST in the boot up sequence.  When the CD launches you should get a screen asking what you want to do. (always run the disk check and the memory test) and then select RUN (the first option) .. it should just chug along to the desktop.

I did the ON LINE upgrade, but did as you have done, saved the ISO and burned and tested it FIRST .. then did a dump of the ~/home folder to a thumb drive.

THEN I did the on line update. On 4 computers! .. only issue I had was the carry over of an overly filled xorg.conf file that had to be removed (rm /etc/X11/xorg.conf) in terminal, then re-booted and the NVidia default driver worked out of the box for my Cinema display .. even the rotate function (which used to be done by adding a line in xorg) was there!  (no need for the restricted driver .. but I do not game and I don't run a bunch of eye candy .. for that, the restricted driver may be needed.)                

So did NOT need the CD or the back up .. but nice to have JUST IN CASE!

Check my bios... :confused:

---

### Post by Ralph L on 2010-06-11
On my Dell Latitude D610, in order to boot from a cd, I press restart and then IMMEDIATELY repeatedly push F12.  This brings up a menu that let's me select the cd for booting.  Other computers I have used work similarly, but may require repeatedly push another key--usually F2.  If you get to the point that booting starts without getting a chance to select the cd as a boot device, press the power/reset button and be quicker in pressing the F12 (etc) key.  Usually the key to push is listed momentarily on the screen after reset but before the boot begins.

Good luck
Ralph

---

### Post by oldsoundguy on 2010-06-11
> **Cant said:**
> Check my bios... :confused:

On most computers, hit F8 during boot up and poke around there until you find the boot sequence .. using the arrow keys and/or the page up page down you can navigate and set the boot sequence (since I have some repair stuff that still lives on a floppy, mine is set for floppy/cd/hd in that order on all of my desktop units) (also makes it nice if you ever have to flash upgrade your bios or chipset to have it in that order.)

---

### Post by bodhi.zazen on 2010-06-11
Lets get this thread going in the right direction. Booting the 10.04 cd is not the way to upgrade.

As pointed out by [mikewhatever]("http://ubuntuforums.org/member.php?u=160645") , upgrade instructions are posted here :

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

You may upgrade Ubuntu 8.04.4 -> 10.04 following those instructions.

I am not sure what iso you downloaded or what makes you think you should  boot the CD to upgrade.

You may upgrade using the alternate cd, instructions are posted here:

[https://help.ubuntu.com/community/LucidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD]("https://help.ubuntu.com/community/LucidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD")

Please take note, these instructions do not include booting the computer to the alternate CD and you can install from the .iso without burning a CD.

---

