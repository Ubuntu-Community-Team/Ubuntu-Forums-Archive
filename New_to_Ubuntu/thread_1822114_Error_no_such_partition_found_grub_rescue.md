---
title: "Error: no such partition found grub rescue"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by pandaking1987 on 2011-08-10
I have searched everywhere to try and fix this but have come up empty on all fronts.

I have a Sony Vaio W series netbook which came pre-installed with Windows 7 starter and to which I dual booted with Ubuntu Netbook remix.

I decided to sell the netbook and did a factory reset in windows 7 without realizing I had to uninstall Ubuntu first.

The result: After factory resetting, Windows erased ubuntu completely, will not boot into Windows 7 and displays the Error: no such partition found grub rescue> prompt every time I try to boot

Things I have tried:  I heard I could do a fresh install of Ubuntu 11.04 so I made a usb of the latest Ubuntu but the boot screen went to a flashing cursor and never booted the ubuntu.

I am out of options and need this solved as quickly as possible.  I am new to Ubuntu and know nothing about code or command prompts. 

If anyone could help me figure out what to do I'd greatly appreciate it.  I just want to restore the netbook back to windows 7 starter without ubuntu.

---

### Post by coffeecat on 2011-08-10
It sounds as though the factory resetting omitted re-installing Windows code to the hard drive mbr. This means that you still have grub code in the mbr looking for the now non-existent Ubuntu partition for the rest of itself.

You need to repair the Windows mbr. Are you able to borrow a Windows 7 installation DVD (it needs to be a Microsoft one) or a Windows 7 repair CD? If not and you have a friend/colleague with a working Windows 7 installation you can prepare a Windows 7 CD from that. This is quite legal. All you need is the recovery console from when you boot up with the repair CD. You would also need a USB CD/DVD drive and set the BIOS to boot from that. If you can get hold of a Windows 7 repair CD or installation DVD, choose recovery console and then command prompt. Then run "bootrec /FixMbr". More here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you can't get hold of a Windows 7 disc, you can install code to the mbr which does the same as the Windows code, using a live Ubuntu CD or USB. Three methods described here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

You'll need internet connectivity in the live session. Most people use the lilo method.

**EDIT**: by the way, I see that you are running a Sony machine. The Sony recovery utility (on its own partition, and not to be confused with the Windows recovery console) is usually more sophisticated than other manufacturer's recovery utilities. Try booting into the recovery partition again and see if there is anything about repairing booting problems.

---

### Post by pandaking1987 on 2011-08-10
Thank you so much.  I popped into the vaio recovery partition and it did the trick.  I didn't know it had it's own space,  THANK YOU!!!!!!!!!

---

