---
title: "Many Problems"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-10-22
I love Ubuntu and the Linux community but I am having major issues that is probably more to do with my hardware than Ubuntu but it is still shutting me down.  I have a 2 HD system with XP on one and Ubuntu on the other.  I tried to upgrade to 10.10 this morning and it failed on reboot and would not boot into Ubuntu or XP.  I finally reloaded XP from the disc and I am on the Windows OS now.  I downloaded 10.10, burned a disc, but my computer won't recognize it.  I have an older 10.04 Ubuntu disc that I tried.

This one gets to the little man on the bottom of the screen but unless I hit enter at that point it goes to a flashing cursor and then the monitor shuts down.  If I hit enter I get the language screen and then the disc menu.  If I try to run from the disc without installing I get the blinking cursor and then the monitor shuts down. If I try to install it, the same thing, blinking cursor that the monitor goes to sleep.

I have done a memory check - pass, HD check - pass.  I don't know what else to do.  I don't want to give up on Linux and I can't spring for a new computer right now.  Any suggestions?  Could this be a video driver issue?  Windows XP runs and loads fine.

---

### Post by Hippytaff on 2010-10-22
Have you tried a live usb with 10.04 or 10.10?

---

### Post by Sef on 2010-10-22
What are your hardware specs?

---

### Post by dondiego2 on 2010-10-22
> **Hippytaff said:**
> did that work?

Have you tried a live usb with 10.04 or 10.10?


No the 10.04 disc did not work.  The disc drive works then the monitor goes to sleep, the disc drive keeps working, the monitor flashes going to sleep a few more times then after a while the disc drive stops working and everything just sits there.

Why would a usb be any different?  What do I do, load the iso on a usb?  I then would have to change my boot order I am guessing to include one of the usb ports in the boot sequence.  Is it worth it to do that?

---

### Post by dondiego2 on 2010-10-22
> **Sef said:**
> What are your hardware specs?


I have a Compag Pressario, with an AMD Athlon processor 3800+
2.41Ghz, 960 MB of RAM according to the Windows system information.

---

### Post by Hippytaff on 2010-10-22
> **Sef said:**
> What are your hardware specs?
  maybe answer this first...because there is experience talking and offering help

I was thinking if your having problems with the live  cd then it might be worth trying live usb, same procedure, but you  would need to use something like unetbootin to make a live usb...you  would change the boor order in the bios to usb

---

### Post by dondiego2 on 2010-10-22
> **Hippytaff said:**
> maybe answer this first...because there is experience talking and offering help

I was thinking if your having problems with the live  cd then it might be worth trying live usb, same procedure, but you  would need to use something like unetbootin to make a live usb...you  would change the boor order in the bios to usb


I know the 10.04 disc works on other computers because I have tried it.

---

### Post by Hippytaff on 2010-10-22
try 10.04  live usb 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by dondiego2 on 2010-10-22
> **dondiego2 said:**
> I have a Compag Pressario, with an AMD Athlon processor 3800+
2.41Ghz, 960 MB of RAM according to the Windows system information.


I have two 512mb memory banks in my computer.  I just opened it up and checked.

---

### Post by Sylslay on 2010-10-22
For me it is video driver issue.
Before boot from Cd,

turn acpi=off
and press Tab and edit grub boot line, delete

"quite splash" and add

If  Your card is made by intel try boot with that parametr?

i915.modeset=1

Or searach on web for " i915.modeset=0 nvidia.modeset=1" it's expalin better than me.

Goodnight/

Ps. I had borken packege in 10.10 but didn't turned off PC. just fixed with Synaptic, and download other upgrates. It works!!

PS. Usually I got the same errors from liveUSB as from liveCD. But is worth to check with unetbootin.

---

### Post by dondiego2 on 2010-10-22
> **Sylslay said:**
> For me it is video driver issue.
Before boot from Cd,

turn acpi=off
and press Tab and edit grub boot line, delete

"quite splash" and add

If  Your card is made by intel try boot with that parametr?

i915.modeset=1

Or searach on web for " i915.modeset=0" it's expalin better than me.

Goodnight/

Ps. I had borken packege in 10.10 but didn't turned off PC. just fixed with Synaptic, and download other upgrates. It works!!

PS. Usually I got the same errors from liveUSB as from liveCD. But is worth to check with unetbootin.


You kind of lost me.  Where do I turn acpi off and what is it?  Or set i915.modset=1?  Is that in set-up in the BIOS?

---

### Post by Sylslay on 2010-10-22
Is not in Bios.

It is in Cd menu.
After You chose lenguage with arrows, than 
probably F6 give You option to turn off some option

And than when You press "Tab" , then cursor jump to and of line,

than add parametr for Intel GPU 845, 915, 945, 

i915.modeset=1, 

with i915.modeset=0 my laptop sometimes boot to black sreen.

---

### Post by dondiego2 on 2010-10-22
> **Hippytaff said:**
> try 10.04  live usb 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


My computer BIOS does give me an option to boot from usb.

---

### Post by dondiego2 on 2010-10-22
> **Sylslay said:**
> Is not in Bios.

It is in Cd menu.
After You chose lenguage with arrows, than 
probably F6 give You option to turn off some option

And than when You press "Tab" , then cursor jump to and of line,

than add parametr for Intel GPU 845, 915, 945, 

i915.modeset=1, 

with i915.modeset=0 my laptop sometimes boot to black sreen.


I did all that and got the same result.

---

### Post by dondiego2 on 2010-10-22
I've been at this all day with no success.  Any more suggestions?  I'm pretty sure I have 10.10 installed on the other HD but no grub menu to boot from so I can't boot into it.

---

### Post by dondiego2 on 2010-10-23
> **dondiego2 said:**
> I've been at this all day with no success.  Any more suggestions?  I'm pretty sure I have 10.10 installed on the other HD but no grub menu to boot from so I can't boot into it.

bump  - still not working.

---

### Post by dondiego2 on 2010-10-23
> **dondiego2 said:**
> bump  - still not working.


OK I'm ready to give up on this computer.  I finally did a complete new install by downloading 10.10 again, making another disc, checking nomodeset and it worked.  Then after the install it told me to reboot my computer, which I did.  The grub menu comes up and I can boot into windows no problem.  When I try to boot into ubuntu my monitor craps out again and goes to sleep.  WTF- I give up unless someone can help I am regretfully going back to windows.

---

### Post by Rendrago on 2010-10-26
Guess what? I have the exact same computer as you and I am having the exact same problem but I am using one HD.

I just installed Windows XP SP2 from CD. It works fine. Then I boot from the 10.10 CD and install using all the default options. Ubuntu works fine.

I reboot and try to boot into Windows and get a blinking cursor. I tried the Windows recovery fixboot and then a update-grub from Ubuntu. Same thing. I pretty sure the MBR is screwed up somehow. I'll try a few other things and repost in this thread.

Bump! Anyone have any ideas?

Compaq Presario SR1330NX:

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=ca&docname=c00280664&product=443740&dlc=en&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=ca&docname=c00280664&product=443740&dlc=en&lang=en")

---

### Post by albert s on 2010-10-26
try 10.04
10.10 seems to be having problems for some systems

---

### Post by Old Codger on 2010-10-26
I'm having similar problems on my 21" iMac 10,1: I can install and boot Ubuntu 10.04 ok, but when I install the 333 updates in Update Manager, the reboot hangs. When I manually shutdown and reboot, the wireless/bluetooth keyboard and mouse don't work, so I can't boot. After installing and reinstalling a couple of times the partition table looks a bit chaotic, which I can fix.

Even when I didn't download and install the updates, the iMac would freeze during booting. When I tried to install directly from the 10.10 live CD, the keyboard and mouse wouldn't work either.

I think I'll erase the partitions and go back to square 1...and perhaps wait until the many bugs are ironed out before I try again.

Ironically, I had no serious problems installing Ubuntu 9.10 and 10.04 on my black MacBook and then upgrading later to 10.10. Is hardware and/or software the problem with the iMac? Both are running Snow Leopard 10.6, so  
I know that iSight is a problem, but I'll fix that after I have both computers running the same distro and I can sync them.

---

### Post by Rendrago on 2010-10-26
I'm going to start my own thread over in Installations and Upgrades as I think I have a much more detailed analysis that may not be appropriate for this section. I'll link a solution if I get one.

[http://ubuntuforums.org/showthread.php?p=10031680]("http://ubuntuforums.org/showthread.php?p=10031680")

---

