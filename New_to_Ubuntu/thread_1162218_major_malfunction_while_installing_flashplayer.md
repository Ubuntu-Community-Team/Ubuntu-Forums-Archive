---
title: "major malfunction while installing flashplayer"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Leapin_Lee on 2009-05-17
Hi. I really messed up last night. I'm puter illiterate so I'm scared that I won't ever have this jaunty 64 bit working right now. Some nice people on here gave me ways to install adobe flash last night and I messed it up. A guy had me do a download that was awesome with all this extra stuff so I did. When it was finished it wanted me to agree to the terms for java but I couldn't figure out how to get the agreement ok button to work. I clicked on th "ok" but it didn't work so I hit enter and that didn't work. Eventuall I just closed the window all this stuff downloaded in. It told me to verify agreement before closing but I couldn't figure out how so I went ahead and closed it. Then a white X in a red circle appeared at the top right of screen where the volume control and internet connection icon is. It said "an error occured, please run Package Manager from the right click menu or apt-get in a tutorial to see what is wrong. The error message was "Error: Broken Count >O This usually means that your installed packages have unmet dependecies. " 
        Iran the right click package manager and there was so much stuff, not neccessarily errors I don't believe but anyway I didn't know what it all was. I closed it after it warned me a couple of times that there were errors. I know this is a long complicated mess. I installed Jaunty 64 bit dual bott after spending many hours reading but I'm still kinda in the dark. I would appreciate any help I can get. I feel really stupid after those people went out of the way to help me and I screwed it up.

---

### Post by oldos2er on 2009-05-17
Open a terminal, and run
```
sudo dpkg --configure -a
```
 When the Java license comes up, use the Tab key to highlight "ok", then press Enter.

---

