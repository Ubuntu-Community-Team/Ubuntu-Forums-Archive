---
title: "sound help"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by jadgarul on 2011-04-11
first off I would like to say I am most definitely 
 an "Absolute Beginner" I installed 10.10 last night.. every application I have added or tried to run... so far has worked great.... with one exception.... I have no sound...  no sound online, no sound in programs.. no sound whatsoever...  I got this distribution right from the Ubuntu Home site...   and after doing some research ended up installing "Pulse Audio"
 but again I dont have a clue what I am doing...I installed it directly from the software center...  I have entered no code yet... because I dont know what I am suposed  to be entering or where.... I am at the moment looking at the  home siter for Pulse audio, and am on the  "[SIZE=2]List of Compilation Dependencies (Distro-Specific)" page.  Can anyone please help me... I need sound.
[/SIZE]

---

### Post by chris282 on 2011-04-11
Hi Jadgarul,

If this doesn't work, I've got nothing, but it was suggested to me when I first set up Ubuntu and had the same problem.  Open the Terminal and type:

sudo adduser $USER audio

Then restart, and keep your fingers crossed.  Best of luck!

---

### Post by LADmaticCA on 2011-04-11
Check under System>Preferences>Sound and make sure the volume is not muted. Also make sure your sound card is selected in the "Output" tab.

---

### Post by mastablasta on 2011-04-12
have a look here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 
it's a nice step by step troubleshooting & solutions guide.
 
i owuld also try alsamixer in terminal to see if all volumes are on high.

---

