---
title: "Grub 2 stopped booting XP"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Old and Rusty on 2009-11-25
Karmic 64 and XP were working well together and grub 2 seemed to have everything under control.  I decided to physically swap drives so that my large one, with Karmic on it was the first drive and my elderly xp installation was on my smaller one.  Grub accepted the changes and worked perfectly.   

An upgrade for Grub 2 appeared and was installed with a number of other Karmic refinements.  The next time I tried to boot xp, it would not boot.  Some kind of map error was referred to and the Grub interface asked me to press any key and it returned me to the menu which now only works for Karmic.

My theory is that the earlier release of Grub 2 let me do something which I should not have done.  Any ideas for an easy way to clean up this mapping mess?  

I can follow instructions but have limited skill in comprehending what is going on.  I dislike xp but need it for a couple of minor applications which can not run in Ubuntu.  Even an awkward boot set-up would satisfy my for the odd time I need xp.

Grub seems to expect xp to be on the first drive now.  How can I point it to the other drive?   Should I just physically swap the drives back to the original position?     It worked perfectly for a week or so before getting 'confused'.

---

### Post by drs305 on 2009-11-25
There are several ways to go about this, but the preferred way would be to change the boot order in BIOS to match what it was previously. That should not only restore GRUB 2 but will prevent a long delay when the computer boots to a drive on which the /boot folder is not located.

To change the BIOS, the user usually presses the DELETE key or F12 as the computer powers up. Go to the boot section and reverse the boot order of the drives. 

Another option would be to run "sudo dpkg-reconfigure grub-pc" and specify the device on which Grub 2 is installed. You might experience the delays on displaying the Grub menu if you do it this way or reinstalling G2 to the secondary drive.

Added:
Rereading your post, I see you did a update after swapping the drives. If the above doesn't restore things, refer to this post to get XP back:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Old and Rusty on 2009-11-25
Grub 2 loads quickly.  Karmic boots rapidly.  No problems at all with them. 

 It is the XP option on the grub 2 interface which does not work.  All of my drives are sata drives.  The system seems to treat whichever drive is plugged in to the SATA 1 slot as the primary or boot drive.  What I did was unplugged my small drive from the SATA 1 slot on the motherboard and switched it to another slot. I then plugged in my large drive into the SATA 1 position.  All worked fine.  I performed the Grub install procedure and it worked.  Windows booted well repeatedly as did Karmic. 

Perhaps a week or so later, after an update,(perhaps a coincidence, perhaps not), the Grub 2 interface quit working and runs an error message everytime I try to run xp.

I will try "sudo dpkg-reconfigure grub-pc" and see what happens but I think I already did this with no effect. I can't remember, so I'll try it and see.


OKAY I ran it and get the same error message as with the Grub interface: 

ie    Found Microsoft Windows XP Professional on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

done


Thanks for your help.

---

### Post by drs305 on 2009-11-25
At some point after the problems have you run "sudo update-grub"?

As it runs, you can watch the terminal window and it should say something like "Found Windows ..."

You can also check the device map file. It's /boot/grub/device.map and see what it shows for drives. You can post it here if you don't understand it. I'll check back in the morning (US time).

---

### Post by Old and Rusty on 2009-11-27
I have 'sudo update-grub'ed a number of times.

It finds windows, Grub creates a listing for it and then can't boot it.  I may just give up and use XP on my wife's computer.  Her dual boot works just find but then very few changes have ever been made on it.

---

