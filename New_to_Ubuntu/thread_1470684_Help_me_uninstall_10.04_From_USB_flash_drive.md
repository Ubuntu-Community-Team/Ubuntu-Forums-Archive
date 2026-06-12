---
title: "Help me uninstall 10.04 From USB flash drive"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Herbernator on 2010-05-03
Hi all,
I'm a total Ubuntu newbie here.

I have installed Ubuntu 10.04 LTS on a 4gb Flash Drive from the Desktop Live CD. (via the install procedure)

After using it for about 3 hours, I've decided that using Ubuntu on MY flash drive is way too slow.

So I would like the computer back the way it was.
The system previously had 1 Windows XP partition.

I have searched forums etc.etc. but there doesn't seem to be a step by step guide to uninstall from a USB flash drive.

From my VERY limited experience with ubuntu (3 hours) it seems as though something needs to be changed in Grub.

Could someone please help?
Thankyou very much in advance.

Herb

---

### Post by WinterRain on 2010-05-03
Plug it in and go to system-administration-startup disk creator and hit the erase button.

---

### Post by Herbernator on 2010-05-03
> **WinterRain said:**
> Plug it in and go to system-administration-startup disk creator and hit the erase button.

Thanks heaps for replying so quick.

I'll give it a go.... 

Kind regards

Herb

---

### Post by Herbernator on 2010-05-03
well I've done what you suggested. No luck at all.
I tried booting up with the usb (ubuntu) and system admin-startup-disc creation hit the delete on the 4gb drive.
I then rebooted. no luck it came up with grub rescue>
Where's my windows XP partition please?
All I want is to get rid of ubuntu and make the windows xp partition the one. So that when I press the on button on the pooter, it boots to xp

Thanks in advance.

herb

---

### Post by Herbernator on 2010-05-03
c'mon all you ubuntu/grub experts. It has to be a simple command at the grub rescue> prompt.

Please help

Herb

---

### Post by bumanie on 2010-05-03
You probably installed grub to the internal hard drive mbr. If you have an xp disk, boot in to repair and in console mode type FIXBOOT, followed by FIXMBR - this will remove grub from the mbr and xp will boot again.

---

### Post by Herbernator on 2010-05-03
Well, after a bit of mucking around I finally fixed the problem.
As I said from the start I am a linux newbie. so I had to look at the problem from a Windows perspective.

For others that might have the same problem. try this.
Insert the windows xp installation cd.
boot into the cd.
get to the recovery console.
you may need to type in the administrators password
type fixboot and select y
type fixmbr and select y
type exit

Now the system boots to windows xp.... yeeha!

Thanks to all that replied
Herb.

Forum Moderators, could you please mark this thread as SOLVED
thanks.

---

### Post by Herbernator on 2010-05-03
> **bumanie said:**
> You probably installed grub to the internal hard drive mbr. If you have an xp disk, boot in to repair and in console mode type FIXBOOT, followed by FIXMBR - this will remove grub from the mbr and xp will boot again.

Yep, You and I must have been typing at the same time.
As for installing grub onto the internal hard drive, I wasnt given an option..... I would have liked to have everything on the usb flash but no harm.... 
I still would like to persist with Ubuntu, I'll just wait till I can get my hands on another hard drive... the usb flash I was using was just tooo slow..
Thanks for taking the time to answer. problem solved.

Herb

---

### Post by bumanie on 2010-05-03
If you do it again, one needs to choose advanced button where it says it is going to set up grub to /dev/sda. You can choose to install grub to root partition on the external drive eg choose to install grub to /dev/sdb1 (or whatever the partition designation is)- it is the last or second last step of setting up installation. Grub will boot from within a root partition whereas windows will not (without a lot of effort). 
Ubuntu is always going run slower off an external device, but a hard drive is much faster than a usb pen-drive. If you have a e-sata external drive with e-sata input on your xp computer, that would probably run fairly quickly.
You should now mark this thread as solved.

---

