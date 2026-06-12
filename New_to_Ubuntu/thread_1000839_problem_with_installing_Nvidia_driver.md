---
title: "problem with installing Nvidia driver"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by eskararriba on 2008-12-03
hi, 
I´m absolutely new to ubuntu (just installed it yesterday running it in windows vista - that dual boot option without repartitioning the hard drive), but I´m havving troubles getting my nvidia-graphics card to run. 
the hardware manager telles me there's an nvidia- driver (173 and 177) available, but won´t download it (while I could download the driver for my wireless card without any problem) - every time I click on "install", a window pops up whcih say "downloading and installing", keeps on 0% for 2 seconds, and then shuts down. 

the graphic of ubuntu is somewhta terrible this way, and the resolution is on 800x640 or something, and I can´t change it. 

I've got an HP pavilion dv2700, nvidia GeForce 7150M / nForce 630M; 

thanks for your help!

---

### Post by LowSky on 2008-12-03
I had this issue as well with a recent install.

you can download the drivers from add/remove and synaptic just fine, just search for nvidia 177

---

### Post by gshockxc on 2008-12-03
I had a similar problem with my custom build the other day.  I have a generic VESA compliant video card (came with the mobo), and even though I installed the appropriate driver, it didn't resolve the problem.  

Reboot, press escape when Grub starts to load, then choose 'b' to boot in recovery mode.  Once you're in recovery mode, then choose XFIX.  Once complete, reboot normally.

Here's my [thread.]("http://ubuntuforums.org/showthread.php?t=999720")  

Another user suggested this to me.  You may want to get some other responses first, b/c I'm VERY new to Ubuntu, but it might solve your problem.  

If it does work, Please give thanks to 'overdrank', as this is not my solution, and I don't want to take credit for someone else's good ideas.

Good luck.

-gshockxc

---

### Post by eskararriba on 2008-12-03
thank you, gshock and lowsky, for your quick answers.
I decided to follow loswkys instructions because they seemed somewhat easier to me - and it worked out perfectly!

great job, cheers

---

