---
title: "Out of Range Monitor"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Antonio Pedro on 2011-06-07
Hello everybody. I installed **Ubuntu 11.04 Server** in my desktop PC, but now when it tries to load the graphics, after the GRUB initial screen, my monitor shows ***"OUT OF RANGE FREQUENCY - SET RESOLUTION LOWER OR SEE USER'S MANUAL"***.

The monitor's user manual says to boot in safety mode [F8] and switch to VGA mode, but that only applies to Windows. I searched the Internet for some help but apparently nothing works for me; i tried to edit the boot options and even use the command line, but apparently i don't even know how to use the command line, type the commands and then change back to the GRUB loader screen for them to take effect. :(

My monitor is a **CRT, HP v72 model**; i have a **GeForce FX 5200** graphics card and also  an onboard AGP VIA graphics card. I even tried disabling the PCI graphics card and use only the AGP OnBoard, but the problem remains. Some posts in other forums end up recommending to use another monitor, but that is really not an option for me. 

Can anyone please help me? I'm going insane over this.

Thaks!

---

### Post by I8NY on 2011-06-07
if grub doesn't show a list of OSes to boot from press esc to show them.  right under ubuntu there should be a recovery option.  it will boot and give you several options, chose low graphics mode or something like that.  It will get you to the desktop at some working resolution so you can set ubuntu back to a resolution that is in range.

---

### Post by GWBouge on 2011-06-07
> **I8NY said:**
> if grub doesn't show a list of OSes to boot from press esc to show them.  right under ubuntu there should be a recovery option.  it will boot and give you several options, chose low graphics mode or something like that.  It will get you to the desktop at some working resolution so you can set ubuntu back to a resolution that is in range.

> **Antonio Pedro said:**
> **Ubuntu 11.04 Server**

I haven't had this issue, but I found this:
[http://ubuntuforums.org/showthread.php?t=1751950]("http://ubuntuforums.org/showthread.php?t=1751950")

---

### Post by wildmanne39 on 2011-06-07
> **Antonio Pedro said:**
> Hello everybody. I installed **Ubuntu 11.04 Server** in my desktop PC, but now when it tries to load the graphics, after the GRUB initial screen, my monitor shows ***"OUT OF RANGE FREQUENCY - SET RESOLUTION LOWER OR SEE USER'S MANUAL"***.

The monitor's user manual says to boot in safety mode [F8] and switch to VGA mode, but that only applies to Windows. I searched the Internet for some help but apparently nothing works for me; i tried to edit the boot options and even use the command line, but apparently i don't even know how to use the command line, type the commands and then change back to the GRUB loader screen for them to take effect. :(

My monitor is a **CRT, HP v72 model**; i have a **GeForce FX 5200** graphics card and also  an onboard AGP VIA graphics card. I even tried disabling the PCI graphics card and use only the AGP OnBoard, but the problem remains. Some posts in other forums end up recommending to use another monitor, but that is really not an option for me. 

Can anyone please help me? I'm going insane over this.

Thaks!Hi, I just fixed that problem on my system last night, Just wait and it will boot then follow these instructions and it works perfect.
```
gksudo gedit /etc/default/grub
```
and change this line:
#GRUB_GFXMODE=640x480
to this
GRUB_GFXMODE=640x480
Then save and exit the document.
Then do:
```
sudo update-grub
```Restart and see if it worked.

---

### Post by Antonio Pedro on 2011-06-09
Thanx guys, but that didn't really help. I need to change the monitor's  resolution (or vertical frequency, to 60Hz or something like that)  **before** linux loads the graphical interface; your tip seemed to change  pnly the GRUB load screen's resolution, not the graphical interface that  comes after that. 

I guess that some hardware manufacturers try their best so that people  don't use linux or free software, and that just makes me want to do it  even more, but i just haven't changed definitely from windows to linux  because of this problem. Is there some place where i can ask the  developers of ubuntu to try to fix this in the next version release?  That would be great. 

Anyway, if some of you guys have any other tip about how to fix this problem, please do post it here. Thanx.

---

### Post by wildmanne39 on 2011-06-09
> **Antonio Pedro said:**
> Thanx guys, but that didn't really help. I need to change the monitor's  resolution (or vertical frequency, to 60Hz or something like that)  **before** linux loads the graphical interface; your tip seemed to change  pnly the GRUB load screen's resolution, not the graphical interface that  comes after that. 

I guess that some hardware manufacturers try their best so that people  don't use linux or free software, and that just makes me want to do it  even more, but i just haven't changed definitely from windows to linux  because of this problem. Is there some place where i can ask the  developers of ubuntu to try to fix this in the next version release?  That would be great. 

Anyway, if some of you guys have any other tip about how to fix this problem, please do post it here. Thanx.
Hi, did you try what I mentioned in my previous post it works for booting, it will show the screen in 640 x480 but you will have the boot menu, it work great for me
and I tried all the other methods first none of them worked.

---

### Post by Antonio Pedro on 2011-06-14
> **wildmanne39 said:**
> Hi, did you try what I mentioned in my previous post it works for booting, it will show the screen in 640 x480 but you will have the boot menu, it work great for me
and I tried all the other methods first none of them worked.


Yes, mate. I tried that and it didn't work. The only difference is that, before the *OUT OF RANGE* message appears, the PC hangs for a couple of seconds with a purple screen. 

I'm stuck. Thanx anyway.

---

