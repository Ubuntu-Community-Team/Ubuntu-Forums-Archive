---
title: "W7 won't work/Multi OS's won't work/I&quot;M GOING CRAZY!"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by TheGuyBehindTheGuy on 2010-10-02
Hi all! I'm new to these forums and I got in for a specific reason. :guitar:

          A while back I was testing out multiple OS's on a single external harddrive (Ubuntu, Open SUSE, and Element OS) While I wouldn't call it a failure, it didn't work out the way I hoped (only ubuntu works and the rest don't) Here ends the first problem.

         The second issue is that while this was going on, my internal harddrive was touched (even though I made sure I messed with the external one only) and windows wouldn't boot (the message "GRUB loading/error: no such disk/grub rescue>_" came up) This wasn't much of a problem because I was able to boot to windows from the GNU GRUB menu in ubuntu by selecting "WIndows 7 (loader) (on /dev/sda2)" and it loaded and ran perfectly. At this point, I only had ubuntu working and w7 half working. I should have stopped here, but I didn't.

         I had bought the recovery disks with the computer (gateway) and put them it to recover. Unfortunately, the disks did didily squat. Worse yet, I could no longer boot to windows through the previously described way. (the message "error: no such device: c0d8543dd854343e/ error: no such partition/ Press any key to continue." and from there it took me back to the menu)

        So here is where I stand: Windows won't boot, Ubuntu/Element OS/Open SUSE won't cooperate, and I just lost $60 on fail recovery disk! Help!!!!!!
(I'd like to fix windows first then get triboot working)

---

### Post by jtarin on 2010-10-02
[This one is on me.]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by Rubi1200 on 2010-10-02
Use the Ubuntu CD (or any LiveCD) and post the results of the boot-script linked at the bottom of my post.

The results will give us a clearer overview of your current setup and make offering solutions easier.

Thanks.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
Jtarin: Do I use a dvd or cd?

Rubi: What the H.E double hockey sticks it that?

---

### Post by Rubi1200 on 2010-10-02
At the bottom of my post is a link to a script which can be run either from a LiveCD or within a Linux distribution.

It gives information on the setup of your drives, where bootloaders are installed etc.

If you would like us to offer advice, run the script and post the results please.

---

### Post by Quark718 on 2010-10-02
> **TheGuyBehindTheGuy said:**
> Hi all! I'm new to these forums and I got in for a specific reason. :guitar:

          A while back I was testing out multiple OS's on a single external harddrive (Ubuntu, Open SUSE, and Element OS) While I wouldn't call it a failure, it didn't work out the way I hoped (only ubuntu works and the rest don't) Here ends the first problem.

         .....
        So here is where I stand: Windows won't boot, Ubuntu/Element OS/Open SUSE won't cooperate, and I just lost $60 on fail recovery disk! Help!!!!!!
(I'd like to fix windows first then get triboot working)

DUDE>
Ok well since you don't have any data you need to recover I'm assuming (since you used a factory disc) this is ezpz lemmon squeezy.  By the sound of it you have no problem booting from a live disc.  So with no other drives hooked up external or otherwise make sure your messed up internal is the only drive connected.  

Then boot a live disc and goto system and then pull up the partition manager.  It's called Gparted.  Right click on your swap partition and turn swap off.  The select each partition logical first then extended and delete each partition until it says unallocated on everything.  Then hit apply to make it actually occur.  With no allocated space there should be no active partitions and thereby no grub.  Windows should install just fine from a recovery disc or fresh install.

You could also use a program like FDISK if you're feelin oldschool.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
quark: I do have a lot of data on the drive that I would like to keep, so I'll try jtarin's idea first.

Rubi: I will try the idea out right after I fix windows (unless it concerns windows) I'd like to get that fixed first. :popcorn:

---

### Post by Quark718 on 2010-10-02
Well even so if you do have a lot of data that's really only one more step.  Boot a live disc, mount your other partitions i.e. windows and ubuntu whichever ones have ur stuff.  Then save them off to your external or a network drive ect.  Then wipe the partitions then restore windows.  Then just pull ur data off of your backup.  The tools that come built in with the ubuntu live disc are better than most available commercially.  I use live discs to get into windows machines where the client forgot their password.  I've used live discs to fix problems with windows viruses.  You name it the live disc is the way to go.

I even have a persistent live disc on a 8gb thumb drive with tons of my programs and files on it.  That's even more practical to do than the original idea you were going for.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
I have some back up data already, but how do I recover windows after I wipe it clean?

---

### Post by Quark718 on 2010-10-02
Well with ur data backed up and ur drive wiped clean of any partitions the restore disc should work just fine on autopilot. Depending on the factory u got ur rig from the disc should setup a new primary partition and then start copying ur disc image back over.  Personally I prefer to do a fresh install from an actual windows disc but I can understand using an image if there's just so many programs on there that u need.  This is why I use virtuals though.  This might be an even better way for you to go if you wan multiple oses.

---

### Post by jtarin on 2010-10-02
> **TheGuyBehindTheGuy said:**
> Jtarin: Do I use a dvd or cd?

Whatever is appropriate for your hardware and/or budget.Either will work.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
Quark: I used the recovery disks the manufacturer gave me. It didn't work. I'm guessing I bought faulty disks. Would the disk jtarin suggested work as well?

---

### Post by jtarin on 2010-10-02
The one I suggested will repair your Windows installation and allow it to boot.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
New Problem..... idk what to do with the disk. I come to the menu to choose recovery tool. 
1. I don't know which one to pick
2. None of them work
3. "startup repair" seems to be the obvious choice, but the message "If you had recently attached a device......" comes up, and won't let me do it :( ](*,)

---

### Post by jtarin on 2010-10-02
Your assuming we are sitting there in front of the monitor alongside you.You will have to provide more information on messages than that. What choices are offered and why can't you select them. We're helpful here....not psychic.

---

### Post by jtarin on 2010-10-02
The first part of [this post]("http://ubuntuforums.org/showthread.php?t=740221") should help you make this decision.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
Oops, you're right. Sorry! #-o

The choices come up in this order
1. Startup Repair= Worked once after I unplugged EVERYTHING (power cord, headset, mouse, everything) but w7 still didn't work :( [I tried it again and the message "If you have recently attached a device to this computer, such as a camera or portable device, remove it and restart your computer. If you continue to see this message, pay a lot of money to contact your system admin or manufacturer" appears]
2. System Restore = No restore points on computer
3. System Image recover = No idea how to work
 
The other two are just a memory test and command prompt.

---

### Post by jtarin on 2010-10-02
You say command prompt....are you sure its not the recovery console?
Use these commands```
bootrec /fixmbr
bootrec /fixboot
```which will restore the bootloader.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
If only I would have learned that earlier, then I wouldn't have tried those stupid recovery disks. I can now boot to windows, but after the "starting windows" screen, a little white bar appears at the bottom of the screen with little white words above it saying "setup is starting services" after which a window appears "Windows could not complete the installation. To install windows on this computer, restart the installation"

btw thanks for all the help so far ):P:biggrin:

---

### Post by jtarin on 2010-10-02
> "Windows could not complete the installation. To install windows on this computer, restart the installation"That's because there is no bootloader....which you can repair now, hopefully.
Once you get Win repaired...look to my signature an explore EasyBCD as a way to boot rather than Grub.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
Ok, downloaded. Now what?

---

### Post by jtarin on 2010-10-02
You have now only downloaded the recovery disk? Then burn it to a CD and boot with it and get to the recovery console as I instructed in my last post and issue the two commands.

---

### Post by TheGuyBehindTheGuy on 2010-10-02
No, I already had the recovery disk and did those two commands in the command prompt. I just downloaded the EasyBCD 2.0.2 and now i'm wondering what to do with it.

Edit: HOLD EVERYTHING! IT WORKS FINE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! I think I'll start a new thread for the tri boot.

Edit2: oh btw thanks for all your help!

---

### Post by jtarin on 2010-10-02
So you can boot into windows now? Just install EasyBCD and no need to do anything else with it right now until you have installed Ubuntu.Before you install Ubuntu use the "TRY" mode of the Ubuntu CD and make your way to the desktop and run Gparted from the System menu and take a screen shot of it and post.Then we can see what you have to work with.

---

