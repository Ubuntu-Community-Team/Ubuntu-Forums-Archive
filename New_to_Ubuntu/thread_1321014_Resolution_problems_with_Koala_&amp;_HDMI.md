---
title: "Resolution problems with Koala &amp; HDMI"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by big_-_red on 2009-11-09
Hi,
 
I've just come over to Linux from the dark side (:-D) but i'm having some problems with the video settings.
 
I'm using an ATI X1950 on an ASRock 939Dual-SATA2 Mobo with a Fujitsu plasma TV. I've got it connected using a DVI-HDMI adaptor -> HDMI switch -> HDMI input. I'm not scared of the terminal as I started on DOS 6.22, I just dont know any of the commands in linux. 
 
Anyway, the problem I have is that I can only get 640x480, 800x600, or a garbled screen. 
 
I initialy installed in safe graphics mode and then spent hours trying to get more than 640x480. I came to the conclusion it was because I installed in safe mode, so I reloaded using a borrowed 19" TFT (can you only select 640x480 when installed via SGM?).
 
It works fine on the TFT but when I connect the Plasma back up I got 800x600 once, after reboot it's too garbled to use. I think its because my screen will only take wierd screen modes via HDMI. I can use a VGA cable BUT then I get 2 massive bars down both sides and can only go to 800x600 (this is due to my old plasma, not Ubuntu).
 
I have tried messing with xorg.conf but (I think) 9.10 no longer has this... so my question is [finally I hear you cry]:
 
How can I force Ubuntu to use 1360 x 768, like it does in W*nd*ws :-)
 
I think I can find the HDMI screen mode input settings Im using in XP, or in the TV manual if required. I've browsed a load of forums and tried manually creating screen modes but I dont know the syntax.
 
Sorry for the essay, just wanted to give as much info as poss
 
Thanks in advance,
 
Jamie

---

### Post by big_-_red on 2009-11-09
Oops I forgot the other important point, now I cant see what i'm doing without connecting another screen. is there a command I can use to load the GUI at a certain resolution.
 
Would downgrading to 8.04 help?
 
J

---

### Post by jbrown96 on 2009-11-09
try to set it with ```
xrandr -s 1360x768
``` If that works, then we can make a startup script to run that.

---

### Post by big_-_red on 2009-11-09
Thanks for the reply jbrown96, I found that on another site and tried it but it didn't work.I think I got an 'unsupported mode' or something. I'll try it again tomorrow morning and let you know exactly what error msg I get.
 
Any idea how I can boot into a shell and change the screen res back to 640 x 480, or else i'll have to dig out the other screen again :)?

---

### Post by jbrown96 on 2009-11-09
When you boot the system, there should be a grub menu. If not try pressing escape or shift when the system first boots. You should get several kernel entries. Choose the second one (it will say recovery). Once that boots, you should get an option to fix graphics or fix packages (dpkg). There should be a process to walk you through the process. That should at least get you back to low resolution. If I'm not mistaken, it should also create a xorg.conf file, and you should be able to create a mode for your resolution in there.

---

### Post by big_-_red on 2009-11-11
Okay, I've done a bit more experimenting and this is what i found.
 
I tried booting into the recovery mode and running dpkg - fix packages, then rebooted, but still get a garbled screen. I think ubuntu is under the impression that my screen will display the resolution OK.
 
I then rebooted (into recovery) and tried the following commands:
 
xranr -s 640x480 : cannot open display
sudo gedit /etc/X11/xorg.conf : cannot open display
sudo dpkg -reconfigure --xorg.conf : conflicting parameters...
 
Then I had a brainwave; I managed to get into the desktop, open a terminal (I can only see the top left corner in b/w and a bit garbled, but just about readable). I then entered:
 
```
xrandr -s 640x480
```
 
Now the screen mode changed, it was now full screen and in color but even more garbled than before! I can also get 720x480 (which is the same) but no other res.
 
I even tried booting into the live CD but I got exactly the same problems (i.e. b/w, top left visible) to start with, and the same thing using randr -s 640x480 or xrandr -s 720x480 (goes full screen and colour but even worse!).
 
I think i will have to connect another screen again to perform further diags, unless anyone has any other suggestions?

---

### Post by jbrown96 on 2009-11-11
ATI produces very poor drivers (not just for linux). they made the decision to drop support for "legacy" devices in April-May of this year. The obvious idea is to use an older version of the driver, but of course that won't work because the older drivers don't support the x-server that 9.10 uses. Your best bet may be to downgrade to 9.04 and try to install ATI's proprietary driver. 

The driver that 9.10 uses is an opensource driver that is not completely stable and complete. It needs a few more months.

---

