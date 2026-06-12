---
title: "installed NVIDIA driver,black screen after waking up?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by soryu on 2009-12-11
when my pc wakes up i get a black screen. i installed  the driver so i could use compiz.
compiz  is working, but  i dont wake up after hibernating. 
how do i fix this  or

do i have to chose between compiz Or waking up normally?

---

### Post by walt.smith1960 on 2009-12-11
Here is a thread that might interest you.
[http://ubuntuforums.org/showthread.php?t=1323449](http://ubuntuforums.org/showthread.php?t=1323449)

This solution hasn't been 100% for me.  This system resumes correctly probably 80-85% of the time but I'm suspicious of the MoBo and/or RAM as well. This system is old enough that I don't want to spend too much on it.

---

### Post by ssulaco on 2009-12-11
> **soryu said:**
>  but  i dont wake up after hibernating. 

soryo.........I had the same problem in Jaunty,try using "suspend",it saves your current state to ram and powers down the fans,and your power button should start flashing, your computer is now  essentially turned off,it is using very little power, to bring it out of suspend just press the power button.
"hibernate" ,I believe copys your current state to disk and then you can power off .hibernate has been an issue in ubuntu for sometime now.

---

### Post by soryu on 2009-12-11
nothing happens when i click suspend.

---

### Post by ssulaco on 2009-12-12
what are you running jaunty,karmic?
since neither hibernate/suspend work, this may work for you:
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)

---

### Post by soryu on 2009-12-14
i upgraded from jaunty to karmic, does it matter if i have a desktop?

---

### Post by soryu on 2009-12-14
> **walt.smith1960 said:**
> Here is a thread that might interest you.
[http://ubuntuforums.org/showthread.php?t=1323449](http://ubuntuforums.org/showthread.php?t=1323449)

This solution hasn't been 100% for me.  This system resumes correctly probably 80-85% of the time but I'm suspicious of the MoBo and/or RAM as well. This system is old enough that I don't want to spend too much on it.

[LIST]
[*]
[*]In gedit open /etc/x11/xorg.conf and add this line to the "devices" section:  Option     "NvAGP"      "1" and save.
[/LIST]
how do i do this?

---

### Post by soryu on 2009-12-15
i'm unable to save.don't have permission, how do i get permission?

---

### Post by soryu on 2009-12-16
Bump
:confused:

---

### Post by walt.smith1960 on 2010-01-21
> **soryu said:**
> 
[LIST]
[*]In gedit open /etc/x11/xorg.conf and add this line to the "devices" section:  Option     "NvAGP"      "1" and save.
[/LIST]
how do i do this?

You have to open  /etc/x11/xorg.conf with root priveleges. From a terminal type gksu nautilus then navigate to the subject files. If you click them they should open in gedit. Edit & save. It's not a terrible idea to open a file, save it as <filename>.old then  save a copy. That way, if you make a mess of the current file, you can delete the current file, remove the .old file suffix, save that and you're back to the original. I've played with this problem for the past month or so and found I had an intermittent hardware problem in RAM. I found incorrectly reported amount of installed RAM. The POST was reporting approximately 512 Mb rather than 1024 Mb. I found that System-Aministration-System Monitor showed the incorrect amount of installed RAM as well.  Either one stick was loose in the slot or one slot was intermittent. I move one stick of RAM to an used slot and removed and reinstalled the other stick.(I have 2 512 Mb. sticks) I also found that if power preferences were set to other than "never suspend" my machine would come out of suspend if it had been in suspend for minutes but it would not come out of suspend if it had been in suspend for hours. I hope this is of some help.

---

### Post by soryu on 2010-07-17
i solved this thou i switched over to mint 
i just added "1" to "nvagp" 
there is a how to on the mint forums.

---

