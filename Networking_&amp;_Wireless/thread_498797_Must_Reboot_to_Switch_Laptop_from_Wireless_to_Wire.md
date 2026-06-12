---
title: "Must Reboot to Switch Laptop from Wireless to Wired"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by masinger53 on 2007-07-11
When attempting to change from wireless to wired through the GUI tool, when the change is made, the new connection doesn't work, e.g., wireless was working fine originally, went to a class with only wired connections, changed to wired, no connection.

Reverse is also true, had wired connection working, changed to wireless using the GUI tool, no connection.  Reboot, wireless comes up.

Recent install of 64 bit Feisty on Sager NP5760 laptop with Intel Pro Wireless, both wireless and wired work fine on Win XP dual-boot, so it is not a hardware issue.  

This happened on the original install of 32 bit Feisty on this laptop as well.  I reinstalled to address another issue (if you're interested, see this [thread]("http://ubuntuforums.org/showthread.php?t=495219")).

Not sure what the fix is for this; it is rather annoying in a laptop to have to reboot to switch.  If Windoze can handle it, I'm sure Linux can, too.  ;-)

---

### Post by scrooge_74 on 2007-07-12
/etc/init.d/ sudo sh network restart

can you use network manager from the bar on top? I sometimes when comming from hibernation it wont connect to my wireless so I disable network and then enable back and it works

---

### Post by masinger53 on 2007-08-08
Sorry for the delayed response - work and such got crazy. 

Doesn't seem to matter if I use the command line to restart networking; I spent 20 minutes of class time doing both CLI and GUI attempts to get the wired connection working to no avail.

At home, I've pretty much given up and left the wireless connection as the "default" with the roaming profile.  Not sure what I'll do if I'm forced to use a wired connection. =(

---

