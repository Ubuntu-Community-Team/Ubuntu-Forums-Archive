---
title: "Difficulty getting connected (dual-boot)"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by Jimpdx on 2007-09-21
Recently, after several months of trouble-free co-existence between Ubuntu and XP Pro, I was unable to establish an internet connection in Ubuntu.  After much trial-and-error, I found a workaround:  booting first into XP then rebooting into Ubuntu using the restart button on the front of the box (not from the Windows menu).  This works, but it's not really a solution, and it's inconvenient.  I want to have an internet connection when I select Ubuntu from Grub.

I have a static IP address, my network device is a Realtek 8139, and my BIOS is Phoenix 6.00.

Does anyone have any suggestions how I might fix this, short of a reinstall?  Thanks.

---

### Post by Jimpdx on 2007-09-21
It just took a little judicious searching.  The problem is in Windows XP (and apparently Vista, as well), a possibility that didn't seem plausible to me when the problem first became known to me.  Windows has the capability to turn off the NIC, and does so as it pleases.  If the Linux distro doesn't know how to turn it back on, you're screwed.  Fortunately, the Windows Device Manager does provide the option to modify how the OS handles the NIC.  I suspect the problem was brought on by a Windows "patch".  Just can't trust 'em!

---

### Post by noob12 on 2007-09-21
Yes.  Here's a recent HOWTO: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

