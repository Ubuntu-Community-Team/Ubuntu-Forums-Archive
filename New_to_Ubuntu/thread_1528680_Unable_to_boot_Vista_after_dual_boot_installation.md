---
title: "Unable to boot Vista after dual boot installation"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Kadyx on 2010-07-11
[SIZE=2]I'm aware that this problem is probably at least as much caused by something I did with Vista than anything to do with Ubuntu, but I figured I'm much more likely to find someone here that has a sense of how the systems interact and what the issue might be than by looking for Vista-related sites.  My basic problem is that after repartitioning the hard drive on a Dell Inspiron desktop that was running Windows Vista and installing Ubuntu 10.04 from a CD, I am no longer able to boot into Windows.  [/SIZE][SIZE=2]When I turn on the computer, it goes through a  Dell loading screen at first, then straight into Grub.  Grub gives the  options of the correct drives for Linux and Windows, but the Windows  option is labeled as "Windows Recovery Environment (loader)" instead of  "Windows Vista."  When I select that, it goes to the same Dell loading  screen and then, when that's done, straight back into Grub.  Ubuntu will  boot just fine, and mounting the Windows partition there seems to show  that the filesystem is still there and intact.  I've found that Ubuntu isn't registering  any of the wireless networks that the computer used to be picking up, so I can't get it online (I'm assuming that problem's  unrelated, but don't really know what to do about that or what's causing it either), but  otherwise seems to be functioning normally.[/SIZE]
[SIZE=2]
How I got to this point:  I started out by shrinking down the Windows partition using Vista's  built-in tool for partition management, though I did have to use a downloaded defragger  (called PerfectDisk, found at [http://www.perfectdisk.com/](http://www.perfectdisk.com/)), which was able to move some of the system files  that the built-in Windows defragger won't, in order to actually shrink  the partition by a useful amount.  I then booted up the Ubuntu Live CD  and used GParted to rearrange the existing partition (moving the  partition that Windows was in to fill the space left by a previously  deleted recovery partition, but not adjusting its size at all), and add  the necessary new partitions.  And then I installed Ubuntu in the space  left for it.

I didn't actually test booting up Windows between any of these steps,  which in retrospect I very obviously should have, so I don't know at what point the problem began.   I do have a reinstallation DVD  for Windows Vista, and I'm assuming that reinstalling that and then  reinstalling Grub should get everything working properly, but the computer's been used for a while and as such has a lot of data and settings that I'd rather not go through restoring, so if anyone has suggestions for a less drastic solution, I would certainly appreciate it.  If there's any further information I can provide to make suggesting a solution easier, please let me know.
[/SIZE]

---

### Post by Pizack on 2010-07-11
try this:
```
sudo update-grub
```
then reboot
looks like grub lost sight of windows, this is the quickest and easiest route to get it back into it.

---

### Post by Kadyx on 2010-07-11
Thanks for the suggestion, Pizack, but the problem continues exactly the same as before.

---

### Post by Pizack on 2010-07-11
> **Kadyx said:**
> Thanks for the suggestion, Pizack, but the problem continues exactly the same as before.

Then we are beyond my area of expertise I'm afraid.  I'll have to leave this one for someone else.

---

### Post by Mark Phelps on 2010-07-11
As you have already admitted, you should have tested your shrunk Vista install BEFORE installing Ubuntu, that way, you could have fixed it then.

Since you probably do NOT have a Vista DVD, go to the link below and download the proper Vista Repair CD image, burn that to CD, and boot from that.  Run  System Repair three times to attempt to fix your Vista boot loader:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Kadyx on 2010-07-11
Thanks, that seems to have done it.

---

