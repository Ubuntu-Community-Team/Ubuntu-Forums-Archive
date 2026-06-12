---
title: "Failed upgrade to 10.04 - No boot"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Slownis on 2010-05-05
My machine is connected to a KVM switch and during the upgrade to 10.04 I was switching the keyboard and mouse back and forth because I needed to do some work on my other laptop. Aparently the upgrade program didn't like this. Now the boot process gets to
 
* Checking battery state
 
and freezes.
 
Anything I can do here without having to do a fresh install?
 
thanks!

---

### Post by Peter09 on 2010-05-05
Is this in recovery mode?

---

### Post by Slownis on 2010-05-05
> **Peter09 said:**
> Is this in recovery mode?
 No that was regular boot.  Now I'm trying the 'repair broken packages' option in recovery mode.  Hopefully that fixes it.

---

### Post by Slownis on 2010-05-05
> **Slownis said:**
> No that was regular boot.  Now I'm trying the 'repair broken packages' option in recovery mode.  Hopefully that fixes it.

It worked!  Sort of.....  It got through a large portion of questions and then it got to a 'Y/N' prompt to install an update to some package (don't remember which), but for some reason it wouldn't take a 'Y' or an 'N'.  CTL+ALT+DEL worked though, and I saw it go through some shutdown routines.  When it rebooted, everything seems to be all OK and I'm writing this reply on the machine.  I'm concerned that the 'repair broken packages' process didn't fully complete.  Any advice?

---

### Post by oldfred on 2010-05-05
If concerned you can run these commands:

#refresh
sudo apt-get update
sudo apt-get upgrade
#would upgrade you to the latest kernel in the repositories
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by fatmcgav on 2010-05-06
> **oldfred said:**
> If concerned you can run these commands:

#refresh
sudo apt-get update
sudo apt-get upgrade
#would upgrade you to the latest kernel in the repositories
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

This combined with a dpkg repair from the recovery kernel restored my non-booting laptop to fully functioning :) 

Cheers for the tips. 

Gavin

---

### Post by Neo2 on 2010-05-07
Thanks, will try this, it looks promising, I didn't try the repair option yet!

---

### Post by matt ha on 2010-05-09
Hi - have the same problem but no joy on the fixes

History: 
1) Updated to 10.04 as prompted 
2) Went through the prompts but kept the old grub (new to Linux)

Boot
Switch on and have the grub options including xp 
Select the first Kernel 
Starts to boot Ubuntu 10.04 - for 5 seconds screen goes black and stays that way

What I have done 
- Tried to use failsafe graphics mode - often didn't work but twice did and tried to upgrade the grub - failed to do this now can not get into the failsafe graphics mode - but run repair broken packages and update grub

  - tried booting a 10.04 live CD - Can't get it to work on my toshiba tecra a2 but the cd does work on a much older toshiba... us a 9.10 live cd and can get in and open terminal and try to enter the prompts listed here. But this does not seem to have done anything

- What now - am in the middle of exams so any help would be really appreciated

---

### Post by Peter09 on 2010-05-09
Try getting into recovery mode by holding the shift key down, then try the reconfigure graphics option.

---

