---
title: "MAdwifi driver patch not working"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Renegade60 on 2007-08-04
Have a system with a built in Atheros based wireless adapter, plus I have an external PCMCIA Orinoco Gold card I want to be able to put into Monitor mode to be able to run Kismet.

My default install of Feisty Fawn goes fine and both cards are recognized via the ifconfig command.  I understand that I have to patch and compile the madwifi-ng driver set to obtain the Monitor mode capability, so I follow to the letter the steps outlined in this thread:  

[http://ubuntuforums.org/showthread.php?t=454005]("http://ubuntuforums.org/showthread.php?t=454005")

Everything from the svn madwifi-ng trunk download, to the patching, etc.  Everything seems to run fine through the make and make install, etc.  The only error I get is when I try to run the **modprobe ath_pci** command at the end:

[I]Error inserting ath_pci (/lib/modules/2.6.17-11-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[/I]

I did a reboot to see if that would force the load of the new drivers and now when I check ifconfig, I have no wireless interfaces listed at all.  I'm assuming the rebuilt madwifi-ng drivers   aren't loading or something, but as I'm relatively new to Linux, I'm not sure what I should do next..

I've tried a reinstall of Feisty from scratch twice and followed the same steps with the exact same results.  What am I missing?  Is there an additional  step I need to perform to bring the interfaces back?

Thanks..

---

