---
title: "Ubuntu Natty on Hybrid Card (intel/Nvidia)"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by sanT520 on 2011-08-17
I have  Thinkpad T520 (core i5) with hybrid graphic card. Hi, I'm very new in Ubuntu, but pretty happy with it. Trying to learn my first steps. But I,m having the following problem. I first installed Ubuntu Natty setting off the optimus option and choosing over the BIOS the built in Graphic card (Intel HD 3000). I did work fantastic.  
 Changing once more the BIOS, I selected the Discrete Graphic card (Nvidia NVS4200 M) and downloaded the proprietary driver. It works, with minor problems. I don't have any video playback and I cannot regulated the brightness of the screen.
 But the major problems turns out when I selected over the BIOS the built in graphic card once more. Then I automatically logs in the Ubuntu without effects, and running glxinfo, turns back it doesn't finds any graphic card.
 
[LIST=1]
[*]Is there any solution to this 	problem, namely, Ubuntu working properly with both graphic cards. I 	don't need the optimus technology, but I would be happily when I can 	switch the graphics cards and having full functionality over the 	system. Should I use this tutorial:  	
[*][https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[/LIST]
 I deeply appreciate any help for a beginner.
 

 Best regards,
 San

---

### Post by LowSky on 2011-08-20
The problem is the Nvidia Optimus technology. The link you provided is for hybrid graphics.. think AMD fusion line, not nvidia optimus

what you want is bumblebee, see this
[http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/](http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/)

---

