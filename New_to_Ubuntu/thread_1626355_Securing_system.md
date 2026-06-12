---
title: "Securing system"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-20
I wanna keep my system secure.I need only security updates,and i dont want to update any other packages..Any suggestions??

---

### Post by guildofghostwriters on 2010-11-20
Open the Update Manager (System/Administration/Update Manager).

There's a settings button in the bottom left corner. Under Ubuntu Updates, you can deselect all but the first option. You could then set it to download security updates without confirmation in the bottom section of the dialogue.

---

### Post by Fableflame on 2010-11-20
Open the Update Manager and click the "Settings" button at the bottom left of the window.

Go to the "Updates" tab of the new window that pops up, and under the heading "Ubuntu Updates" only check the first option: "Important Security Updates"

---

### Post by karthick87 on 2010-11-20
I have heard many users cant able to boot their system after update.Will security updates cause any problem?

---

### Post by Rubi1200 on 2010-11-20
For what it's worth, I have never had a problem with my system using just the "Important Security Updates" feature mentioned by Fableflame.

---

### Post by karthick87 on 2010-11-20
I have installed security updates but now when i boot my system i find two kernels in the grub menu.How to remove the old one?

---

### Post by Rubi1200 on 2010-11-20
After kernel updates a new entry is added to the GRUB menu. 

You can remove the older one if you want. 

However, most experienced users will advise you to keep at least one spare entry in case something goes wrong with an upgrade and you need to boot an older kernel version for troubleshooting purposes.

---

### Post by karthick87 on 2010-11-20
> **Rubi1200 said:**
> After kernel updates a new entry is added to the GRUB menu. 

You can remove the older one if you want. 

However, most experienced users will advise you to keep at least one spare entry in case something goes wrong with an upgrade and you need to boot an older kernel version for troubleshooting purposes.


But i am quite sure that new kernel is working fine.So can i remove the old one?

---

### Post by CharlesA on 2010-11-20
> **Rubi1200 said:**
> However, most experienced users will advise you to keep at least one spare entry in case something goes wrong with an upgrade and you need to boot an older kernel version for troubleshooting purposes.

This. I recommend keeping at least one older kernel in case you run into problems with the newer one.

---

### Post by oldsoundguy on 2010-11-20
> **CharlesA said:**
> This. I recommend keeping at least one older kernel in case you run into problems with the newer one.

+1

I keep two  

Unless you have a very TINY drive, does not take up that much space.  (Last I heard, Kernel itself still fits on a floppy!!)

---

### Post by Megaptera on 2010-11-20
If you're _really_ sure, then it can be done through synaptic

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by Sidewinder1 on 2010-11-20
I agree wholeheartedly with posts 9 & 10, keep the current and preceding kernel; there is absolutely no reason (that I can think of) to delete the preceding one. Although my wife takes great pleasure in reminding me how many times I have been wr...wro... wron..., a little weak on bein' right. :D
Side

---

### Post by karthick87 on 2010-11-20
Oke thankyou :) Also say me what are all the steps you people take to protect your system from hackers,spywares and viruses..?

---

### Post by cmcanulty on 2010-11-20
I only have one version also how can I save a spare grub version

---

### Post by Rex Bouwense on 2010-11-20
> **karthick87 said:**
> Oke thankyou :) Also say me what are all the steps you people take to protect your system from hackers,spywares and viruses..?

Linux was once described as a room with no open windows or doors.  For something to get into the room (your computer running a Linux OS), you have to open a window or a door.  By default they are closed so you are protected.  I read that somewhere and I am sure that I did not do the author justice by paraphrasing his work.  In short you have a firewall installed by default all you have to do is activate it if you want.  I have been using Linux OS for almost two years and have yet felt the need to activate the firewall.  There are less than 100 virus configurations that have been identified in Linux, none of which are active or dangerous to your OS or data.  Enjoy.

---

### Post by CharlesA on 2010-11-20
> **Rex Bouwense said:**
> Linux was once described as a room with no open windows or doors.  For something to get into the room (your computer running a Linux OS), you have to open a window or a door.  By default they are closed so you are protected.  I read that somewhere and I am sure that I did not do the author justice by paraphrasing his work.  In short you have a firewall installed by default all you have to do is activate it if you want.  I have been using Linux OS for almost two years and have yet felt the need to activate the firewall.  There are less than 100 virus configurations that have been identified in Linux, none of which are active or dangerous to your OS or data.  Enjoy.

+1.

There are no open ports on the default install so unless you install something like SSH or enable Remote Desktop, you will be fine.

---

### Post by karthick87 on 2010-11-21
But i have installed ssh in my system.So how to keep it secure?

---

### Post by CharlesA on 2010-11-21
> **karthick87 said:**
> But i have installed ssh in my system.So how to keep it secure?
Read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by wojox on 2010-11-21
> **karthick87 said:**
> But i have installed ssh in my system.So how to keep it secure?

Client or Server?

---

### Post by karthick87 on 2010-11-21
> **wojox said:**
> Client or Server?


Installed Both Server & Client.

---

### Post by QLee on 2010-11-21
Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

If you learn how to use the search function of the forum, in future you'll save yourself a whole lot of time waiting for answers.

---

