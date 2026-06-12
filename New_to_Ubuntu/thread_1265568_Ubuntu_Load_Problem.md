---
title: "Ubuntu Load Problem"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Deaia on 2009-09-13
I have installed the new 9.04 ubuntu, install in windows option. Yesturday i didn't have any problems entering ubuntu. Today, the O.S. doesn't load properly, when the bar gets half full, suddenly 4 to 6 images of the logo appear, and everything freezes.

Why do you think this is so? And is there any way to arround this without having to reinstall ubuntu?

P.s: It never reaches the stage when i have to write my name and password....

---

### Post by jbrown96 on 2009-09-13
Did you install any video drivers, if so which ones? You can get to a verbose boot, which may help determine where the system is hanging. When the Grub menu comes up (or says to press Esc), press e to edit the top line, then press e to edit the first line again. You will no have a cursor at the end of a long piece of text. One of the last options should say "splash" change it to nosplash. Then press enter and b to boot. Try to figure out where it freezes.

---

### Post by Deaia on 2009-09-16
thanks for the idea, i'll try it next time. I tried verbose load, to see where the error was comming from, but i couldn't tell exactly where the error originated from because the screan i described earlier poped up quiet fast. But the general idea of the operations taking place at that moment was for the video card. 

So i reinstalled ubuntu 9.04 and tried to install the correct driver ATI Mobility Radeon HD 3470. and i've also installed the ATI Catalist program which is supposed to monitor the driver.
Anyway, long story short, the ATI Catalist program doesn't see the driver, and neither does ubuntu :(

I've run out of ideas, except maby try to install 8.04 which i know is more stable :-??

---

### Post by Megatron3000 on 2009-09-16
I had the same issue, the only way to adequately resolve it seems to be not to install the ati driver. There is a way to install it (after downloading and installing run the recovery mode and enter in the terminal 'sudo aticonfig --initial' and 'sudo dpkg-reconfigure -phigh xserver-xorg' , you may have to try a few times) or to manually compile it into your kernel (which works, and is more or less explained here: [http://ubuntuforums.org/showthread.php?t=756236](http://ubuntuforums.org/showthread.php?t=756236)) 
 
nevertheless, the ati driver does not give you a lot. Yes, it enables the fancy desktop stuff, but your video playback will not be as good, and scrolling becomes very awkward, and affects your machine's performance. With the standard driver, everything works fine, except for 3D stuff (such as the desktop, and presumably games - i don't know too much about that)

---

