---
title: "XP/Ubuntu Dual-Boot &amp; LiveCD Problem"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by SuaSwe on 2009-11-04
Hi everyone!

I'm trying to help a friend with a somewhat desperate boot situation. He's dual-booting XP and Ubuntu, and for some fascinating reason he's only been able to boot into XP if he's logged into Ubuntu first to mount the drive. For the past few weeks he's simply been hibernating XP and so has not had to do this, however yesterday he accidentally rebooted normally and now he cannot access either operating system. Windows XP loads up to the splash screen and no further, and Ubuntu loads straight into the desktop login prompt.

Before it loads, we get something like this:

[font="courier new"]
  sbin/usplash: symbol lookup error: undefined symbol: animation_needed_fd
  19+0 records in
  19+0 records out
  kinit: name_to_dev_t dev(8,6)
  kinit: trying to resume from [something something, missed this bit]
     No resume image, doing normal boot...
[/font]

It then goes through all the checks, OK-ing everything (except PulseAudio config has an orange star by it instead of a white one). Not sure if that's relevant.

Finally, screen goes black, followed by the desktop login CLI prompt (under tty1, which seemed odd to me?), then goes black again, then the following appears:

[font="courier new"]
Failed to start X Server (your graphical interface). Likely it is not set up correctly. Would you like to view the diagnostics?
[/font]

Hit OK, and it returns the following error:

[font="COURIER NEW"]
  debconf: DbDriver: "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
[/font]

Once that's OK'ed, it suggests restarting GDM - am however not sure how to do this.

Now, back at the prompt it does allow us to log in, including with sudo privileges. Before I ask suggestions for what to try in there, however, I do want to make a note of one thing: 

The LiveCD does not work. When popping it in, it will go past selecting language and 'Try Ubuntu without making any changes' (opting via F4 for Graphical Safe Mode) - the splash screen then loads but the progress bar moves *chronically* slow, and I mean that the bar takes several minutes to cross from one side to the other. Finally it ends up at the following:

[FONT="Courier New"]
  BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
  Enter 'help' for a list of built-in commands
  (initramfs)_[/FONT]

He has already tried swapping out the memory; I told him to run a memory check via the disc just in case, which appears to work normally, however I don't expect it to return anything. Similarly he has attempted the Windows installation CD, but it will not recognise the hard drive - still, the Ubuntu LiveCD should surely load OK with or without a healthy hard drive?

Any suggestions on what may be causing this at all, guys? Much obliged!

---

### Post by SuaSwe on 2009-11-05
Bump? ;_;

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Try [this](http://prdownload.berlios.de/supergrub/grub-rescue-cdrom.iso) just to see if you can get into Ubuntu with it.

Let's start there unless someone with more beans than me comes along with a better idea.
Just burn this to disc, make sure the optical drive is first boot, and I don't think this gives you any options besides starting Ubuntu.

---

### Post by SuaSwe on 2009-11-14
Thanks for the reply on this - my neighbour lost patience and decided to install Vista instead (each to their own :D). 

I now have problems with my laptop following upgrade to Karmic (X freezes as soon as I try to run an app); assistance would be most appreciated:

[http://ubuntuforums.org/showthread.php?t=1326507](http://ubuntuforums.org/showthread.php?t=1326507)

---

