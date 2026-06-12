---
title: "Dual booting concerns"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Dave W. on 2009-05-24
Hello all,

Well I've jumped in head first and decided to dual boot XP and Jaunty.  It was very easy.  

I've noticed that when using XP and System Mechanic software, the repairs and updates that I make either aren't performed or don't update.  It seems like the instructions to repair are some how lost when I have to choose between the two OS.

Has anyone experienced this?  Does this make any sense to any one?

Is it something that can be repaired.  I'm not quite ready to get rid of XP.

Thanks,
Dave

---

### Post by bennachie on 2009-05-24
I don't know anything about "System Mechanic" and XP. However, I do know that a similar process using Windows Update in Vista routinely requires that various system operations be performed during the shut-down phase after the update was initiated and that further operations be performed during the subsequent restart. I have had no problems with this but, as a matter of belts-and-braces, I have always opted to reboot immediately into Vista to complete the updates before switching back to Ubuntu. I guess that it all depends how, and where, the Windows update process keeps track of what operations remain to be completed at the next restart.

---

### Post by Dave W. on 2009-05-24
Thanks Bennachie..

Is it possible in dual boot to directly specify which OS to jump into without having to make that 8 sec. choice.  IE. have the computer know to go to XP first rather than Ubuntu.  I'm assuming that the default will always be Ubuntu.

Dave

---

### Post by bennachie on 2009-05-24
Yes, that's quite easy. See, for example:

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

---

### Post by Dave W. on 2009-05-24
Thank you.  I'll give it a try and I will post later.

The way the system is set up now it appears that nothing in XP will update, if a restart is required.  

Just a tad frustrating.  ):P    Thanks again!!!

Dave

---

### Post by Dave W. on 2009-05-24
Well, setting XP as my default OS worked great.. 
Much easier than I thought.   
As far as my updates in XP, I am unsure.  
I'm still playing around with it.   
Thank you my friend from down-under for the help.

Dave       :D

---

### Post by Bartender on 2009-05-24
I'm also unfamiliar with System Mechanic.  I believe it's just a maintenance utility, similar to CCleaner and others?

In a typical dual-boot, where you allow GRUB to step in and act as the bootloader, you've only changed two things in Windows.  You've squished Windows into a smaller partition (unless you're using a separate drive for Ubuntu) and you let GRUB tweak the Windows Master Boot Record, which is only accessed by the PC once as it starts up.

Other than that, Windows is not changed in any way.  So I don't understand why updates or other system changes seem to be acting differently than before.

---

### Post by Dave W. on 2009-05-24
I'm thinking that it must be System Mechanic.

Thanks for your response,

Dave

---

