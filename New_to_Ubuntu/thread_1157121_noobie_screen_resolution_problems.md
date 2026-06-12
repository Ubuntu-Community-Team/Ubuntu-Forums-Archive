---
title: "noobie screen resolution problems"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by wanderingarticfox on 2009-05-12
I've been playing around with 8.10 for a little while now and can not get my screen resolution or 'window' properly adjusted. I had my proprietary video card installed and I've played with the screen resolution in the System menu. I can not get back to 75Hz and my entire screen is off center to the left. I am using a Samsung SyncMaster 955DF (CRT) and a nVidia GeForce 2 video card in an old 2002 Compaq system. I have not gotten around to learning much about 'command line' stuff because I've been trying on my own to fix this resolution and off-center issue. I would appreciate step by step help. I know that the proprietary driver is most likely best but I just deactivated it for now trying to get the 75 Hz option back in the System>Pref>Screen resolution option and that did not work :confused:

---

### Post by KhaaL on 2009-05-12
I suggest you reinstall the propeitary NVidia driver and use the tool nvidia-settings 
in order to get that refresh rate back, have you used nvidia-settings before?

---

### Post by wanderingarticfox on 2009-05-12
Uh, no :) I'm used to windows so I'm kinda learning on the fly here. I'm having fun but my eyes are burning at 58Hz, I'll be back shortly after I reactivate

---

### Post by wanderingarticfox on 2009-05-12
OOPS, I can not figure out how to get back to reactivate the driver. I actually did not 'uninstal' but selected to 'deactivate'; can you help please ?

---

### Post by wanderingarticfox on 2009-05-12
Found it, under hardware drivers; just reinstalled and going for restart; be back shortly](*,)](*,)

---

### Post by Yvan300 on 2009-05-12
Hey don't some crt sceens come with built in options to adjust screen postion, brightness etc. You know those knobs and what not at the front, maybe they are the root of the problem. Worth a try.

---

### Post by wanderingarticfox on 2009-05-12
OK, back up now. As to the 'knobs and stuff'  that is irrelevent on this issue. I'm dual booting windows XP Home and the resolution is fine there.
 There is a  'nVidia X Server Settings' in the System>Admin pull down menu but I am not sure that is what I want.
  I need a walk through with the nVidia please.:confused:

---

### Post by wanderingarticfox on 2009-05-12
[FONT="Arial Black"][SIZE="3"]OK we got it. Thanks for the help on that Khaal.   The solution was right before my eye's:)  I reinstalled and reavtivated the proprietary driver then went to System>Administrator>NVidia X Server Settings>>X Server Display Configuration. I then used the selection boxes to reset the screen size and resolution. 1024X768 @ 75Hz is perfect. I then tried 1024X768 A Auto and that is even better.

Thank you for the help and I hope anyone else that needs this info can locate it.:guitar:[/SIZE][/FONT]

---

### Post by KhaaL on 2009-05-12
> **wanderingarticfox said:**
> [FONT="Arial Black"][SIZE="3"]OK we got it. Thanks for the help on that Khaal.   The solution was right before my eye's:)  I reinstalled and reavtivated the proprietary driver then went to System>Administrator>NVidia X Server Settings>>X Server Display Configuration. I then used the selection boxes to reset the screen size and resolution. 1024X768 @ 75Hz is perfect. I then tried 1024X768 A Auto and that is even better.

Thank you for the help and I hope anyone else that needs this info can locate it.:guitar:[/SIZE][/FONT]

Glad to hear it worked out, enjoy your stay in ubuntuland :KS

---

