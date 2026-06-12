---
title: "change color depth to 16-bit"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-07-19
Greetings,

I'm trying to get Starcraft to run under Wine.  After having issues with a very slow framerate, I discovered that many suggest decreasing the color depth from 24-bit to 16-bit, and to avoid 8-bit color depth.

How do I do that?  xorg.conf doesn't have a color depth setting anymore, from what i've read.

Any help would be appreciated.  Previous posts asking this kind of question seem to have been dismissed on the grounds of color depth not being very relevant to the issue.  I am also curious as to how to change the color depth settings for my own edification.

Thanks much,

--Red

---

### Post by /usr/sbin on 2009-07-19
Found this on google, it is similar to your problem, hope it helps.



A simple way to set your screen resolution and color depth for most Live Linux distro's is via the use of the vga=parameter boot option. For example at boot you might type: Live vga=795. This would set your system to boot using the Live label with a [COLOR=#009900][FONT=&quot]_screen resolution_[/FONT][/COLOR] to 24bit 1280X1024. Here are some more examples of common vga boot values.
 
**VGA Resolution and Color Depth reference Chart:**
   **[SIZE=2]Depth [/SIZE]** **[SIZE=2]800×600[/SIZE]** **[SIZE=2]1024×768[/SIZE]** **[SIZE=2]1152×864[/SIZE]** **[SIZE=2]1280×1024[/SIZE]** **[SIZE=2]1600×1200[/SIZE]**   [SIZE=2]8 bit[/SIZE] [SIZE=2]vga=771[/SIZE] [SIZE=2]vga=773[/SIZE] [SIZE=2]vga=353[/SIZE] [SIZE=2]vga=775[/SIZE] [SIZE=2]vga=796[/SIZE]   [SIZE=2]16 bit[/SIZE] [SIZE=2]vga=788[/SIZE] [SIZE=2]vga=791[/SIZE] [SIZE=2]vga=355[/SIZE] [SIZE=2]vga=794[/SIZE] [SIZE=2]vga=798[/SIZE]   [SIZE=2]24 bit[/SIZE] [SIZE=2]vga=789[/SIZE] [SIZE=2]vga=792[/SIZE]   [SIZE=2]vga=795[/SIZE] [SIZE=2]vga=799[/SIZE]

---

### Post by Redmage913 on 2009-07-19
Okay, that mostly makes sense to me.

Where/When do I engage this boot option?  And would I have to do this at every boot or does it become the default option when I plug in the boot option the first time?

--Red

---

### Post by /usr/sbin on 2009-07-19
[LEFT]I think that you would only have to set it up once, but i am not completely sure. Your best bet would be to ask someone else about it. Maybe PM someone. I think that you need to open up the terminal and type it in. I am assuiming that you know where the terminal is found. Its either in accessories or administration. 
[/LEFT]

---

