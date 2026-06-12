---
title: "Can't synch my modem please read!"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by bar8080 on 2007-07-25
I have tried everything to connect to the internet but it's just impossible! 
I have a ALE 150 modem and have tried all synch files. With  two of them, gs7470_synch20.bin and gs7470_synch21.bin, the link light flickers but is never steady. I tried creating my own synch file with the command:eciadsl-vendor-device.pl usbsnoop.log -chipset=GS7470 
but get this error massage:
Can't open -chipset=GS7470: No such file or directory at /usr/local/bin/eciadsl-vendor-device.pl line 334, <> line 757773. 
WARNING : interrupt packet not detected. file gs7470_synch999.bin generated anyway but should not be correct 
And I also tried it the this command:eciadsl-vendor-device.pl usbsnoop.log 
and got this error(which is, I think, pretty much alike):
WARNING : interrupt packet not detected. file synch999.bin generated anyway but should not be correct  

My log file, with which I created the synch is about 25MB maybe I didn't create it correctly, eventhough I followed all the steps in the ECIADSL website.

I have no idea what to do next! I thought about using the gs7070 chipset files but figured I should ask for help before...
If anyone has any idea please help me!
Thank you...

---

### Post by bar8080 on 2007-07-25
C'mon guys can't anyone help! I am thinking of giving up linux!

---

### Post by bar8080 on 2007-07-27
... I am disapointed...

---

### Post by bar8080 on 2007-08-10
HELP OMFG!!!:mad:

---

