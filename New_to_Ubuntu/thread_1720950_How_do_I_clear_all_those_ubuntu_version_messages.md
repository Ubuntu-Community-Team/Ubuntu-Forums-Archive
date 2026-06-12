---
title: "How do I clear all those ubuntu version messages?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by flopwich on 2011-04-03
I have my netbook set up as a dual-boot machine with Windows 7.  When I boot, the machine offers me a list of options:  Ubuntu, Windows Vista (which I've never installed) and Windows 7, which I use.  The thing is, the first choice is Ubuntu, giving me the version number with the Linux version number and "generic mode", followed by the same line with the added text "(recovery mode)".  Those two lines appear over and over and they multiply as I continue to log in.  It seems that it adds those two lines when I log in to Windows.

So, the question is, how do I get rid of all those added lines?  The list keeps getting longer and longer, so that I have to scroll down a couple of screens now to get to the Windows options.  A little help would be much appreciated.

---

### Post by TBABill on 2011-04-03
Each of those should be due to different kernel versions. You have probably received several updated kernels over the past months and they each show up. I always recommend a user to keep the current and one older kernel (known working one) and remove the others if not needed. You can go into synaptic and search "kernel", then remove the oldest ones, leaving the newest 2.

---

### Post by drs305 on 2011-04-03
This guide should cover it - it explains what the extra entries are, whether you should keep them, and how to remove them. I'd recommend using Ubuntu Tweak, which is also discussed.
[HOWTO: Remove Older Kernels via GUI ]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by blueridgedog on 2011-04-03
They are older kernel versions, there in case a newer kernel breaks you system and you need to boot on a prior one.  You can remove older ones with synaptic.

System -> Administration -> Synaptic Package Manager, then select "System Administration" on the menu on the left and you can scroll down on the right and un-select any older kernel that you no longer want to have on the list.  I recommend you leave the current (newest) and at least two prior ones.

---

### Post by 311005901 on 2011-04-03
**This is (almost) foolproof.**
Each time Ubuntu updates the Linux kernel, it keeps the old one on your computer - just in case the new one doesn't work. Over time, the kernels will accumulate and take up space on your harddrive, and in your boot menu.

To clean up both, [download]("http://ubuntu-tweak.com/") and install Ubuntu Tweak. Run the program and: 
[LIST=1]
[*]Click on the left panel on "Package Cleaner"
[*]Click "Unlock" on the bottom right of the window and enter your password
[*]Click on "Clean Kernels" on the right side of the window
[*]Click on the "Select all" checkbox
[*]Click "Cleanup" on the bottom right of the window
[/LIST]
When it completes, you can close the application.

Don't worry about bricking your system. Ubuntu Tweak automatically detects the kernel you're using and doesn't let you remove it.

After that, reboot and the menu (and some extra HD space) should be looking better.

---

### Post by madmax75 on 2011-04-04
> **311005901 said:**
> **This is (almost) foolproof.**
Each time Ubuntu updates the Linux kernel, it keeps the old one on your computer - just in case the new one doesn't work. Over time, the kernels will accumulate and take up space on your harddrive, and in your boot menu.

To clean up both, [download]("http://ubuntu-tweak.com/") and install Ubuntu Tweak. Run the program and: 
[LIST=1]
[*]Click on the left panel on "Package Cleaner"
[*]Click "Unlock" on the bottom right of the window and enter your password
[*]Click on "Clean Kernels" on the right side of the window
[*]Click on the "Select all" checkbox
[*]Click "Cleanup" on the bottom right of the window
[/LIST]
When it completes, you can close the application.


+1. Ubuntu Tweak is easy and fairly reliable, I use it myself as well. Although I tend not to delete ALL the kernel entries, I keep the two most recent ones and delete the older ones. But I guess it's a matter of taste.

---

### Post by flopwich on 2011-04-04
> **madmax75 said:**
> +1. Ubuntu Tweak is easy and fairly reliable, I use it myself as well. Although I tend not to delete ALL the kernel entries, I keep the two most recent ones and delete the older ones. But I guess it's a matter of taste.

Thank you, everyone.  That's MUCH better now.  It has only one line for the current kernel and one for recovery mode.  Ubuntu boots much faster and runs better, as apparently all those kernels were loading and clogging up memory (?).

Thank you very much.:D

---

### Post by Chronon on 2011-04-04
Only one kernel is loaded by the bootloader (grub2).  The others take up disk space but shouldn't otherwise affect the boot process or the subsequent operation of the system.

---

### Post by flopwich on 2011-04-05
Ah, thank you.  I must have imagined the improved performance, then.  Either way, I'm glad to have it fixed up.  At the very least, it makes booting to Linux that much easier.

---

