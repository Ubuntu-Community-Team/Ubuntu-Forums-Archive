---
title: "lost 1024x768 resolution with monitor change"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-03-18
I have Ubuntu 10.04 LTS on this hard drive. It was cooking along fine with 1024x768 resolution until I pulled it and popped it into another machine (different monitor but requires the same resolution) now Poof - no more 1024x768. Seems like I go through this every time I upgrade Ubuntu or change monitors, etc but now I can not remember how to fixed it before and the directions I found for using xandr to add the 1024x768 option do not work (I run into a 'command not found' right in the middle of it). I've found a file xorg.conf.save  that was made in January, the computer had the right resolution then, can I use that somehow to fix this?

thanks so much, any help with this is appreciated.


mystmaiden

---

### Post by sydbat on 2011-03-18
> **mystmaiden said:**
> I have Ubuntu 10.04 LTS on this hard drive. It was cooking along fine with 1024x768 resolution until I pulled it and popped it into another machine (different monitor but requires the same resolution) now Poof - no more 1024x768. Seems like I go through this every time I upgrade Ubuntu or change monitors, etc but now I can not remember how to fixed it before and the directions I found for using xandr to add the 1024x768 option do not work (I run into a 'command not found' right in the middle of it). I've found a file xorg.conf.save  that was made in January, the computer had the right resolution then, can I use that somehow to fix this?

thanks so much, any help with this is appreciated.


mystmaidenLet me see if I understand you correctly - you have taken the hard drive out of one computer and put it into another, yes?

Do both computers have the same, exact, graphics cards? If not, this is likely the problem.

Please tell us the specs of each computer - eg. CPU, RAM, Graphics card, etc.

---

### Post by mystmaiden on 2011-03-18
Thanks for the reply. Yes, I pulled the drive from one and stuck it in the other and then today I put it back in the original machine. The resolution held until I put it back in it's original machine.

No graphics card on either machine, onboard graphics only.

Machine 1 - amd xp cpu, K7S41GX motherboard with Integrated Mirage Graphics. Max. 64MB


Machine 2 - amd duron cpu, MS 6738 combo motherboard,[FONT=inherit][FONT=inherit] Integrated Savage 8 2D/3D Graphic Controller

both monitors are crt requiring 1024x768 resolution, one is just a bit bigger than the other.

[/FONT][/FONT][FONT=inherit][FONT=inherit]Edited to add - It just dawned  on me that I have a clone of this hard drive, so I hooked it up to  another box and voila... it is set up and working with the correct resolution. If I know what to look for maybe I can copy it over to this machine...[/FONT][/FONT]
[FONT=inherit][FONT=inherit]
I solved this by just dragging the second monitor in here and plugging it in, it booted with the right resolution so I shut down, plugged the first monitor in and its working fine. Correct resolution and all the resolution choices are now showing on System/Preferences/Monitors. I do not know why that would work but it seems it did. Hopefully it will persist.


[/FONT][/FONT]

---

