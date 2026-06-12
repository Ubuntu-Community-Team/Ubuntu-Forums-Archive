---
title: "ubuntu freeze installation"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Imatech64 on 2010-03-24
Hello ,
 
I am trying to install ubuntu 9.10-Desktop and I am encountering troubles during installation.
 
My laptop is an AcerTM8003
Pentium-M Centrino Processor **1.6GHz **
15" SXGA+ TFT Screen 
60GB Hard Drive 
1.5 GB DDR SDRAM
running with windows XP.
 
I have already tried and followed the instruction for the LiveCD and burned the ISO it with ISORecorderV2RC1.msi program on a blank CD several times with different buring speeds (x2 to x24).
 
The trouble is that the installation hangs/freeze at a certain step of the installation , keyboard being completely inactive and non responding at all, the mouse/cursor moving by steps and not smoothly as up to that point.
 
I chosed the memory test (memtest86+) from the initial liveCD installation menu. The memtest begins each time normally and achieves pass from 24% to 58% and then the laptop simply shut down by it self !! 
 
I have also tried the 8.04 LTS with exact same result.
 
I have had no trouble of hanging or freezing in XP. Nevertheless having tried so many times the ubuntu installation, I decided to format the HD with the original winXP, installed all drivers , checked the good function of all but did not updated XP and left it to SP1.
 
If anyone has an idea, I will be greatfull for an assistance

---

### Post by mastablasta on 2010-03-24
Have you tried alternate (non graphical) install?
 
You didn't provide your graphics card in the specs.

---

### Post by Imatech64 on 2010-03-24
Sorry, you are right
 
Graphic card is a ATI MOBILITY RADEON 9700 with 64MB

---

### Post by mastablasta on 2010-03-24
You should try alternate install (it's a non graphical installation, but later on you get into GUI) and also install proprietary drivers from ATI. Maybe it will work. I read some similar issue being resolved with alternate install. 
 
It might also be the issue of swithing something in bios, but i don't know exactly what (i think it's HDD controler from SATA to IDE or something like that). Acer computers seem to have strange compatibilities (they are cheap though). I know in some of them you also needed to do this just to get WinXP on them.
 
I am sure someone could help more here, i am just a beginner in Linux, but i've been reading the forums a lot. And i see others had similar issues only on a different laptops.
 
Also does the LiveCD boot up propperly? Have you tried booting linux from CD?
 
Also if you are trying to do a dual boot (with WinXP) make sure you defragment the disk first and do a ```
chkdsk /r /f
```

---

### Post by Imatech64 on 2010-03-24
OK, I will try the alternate CD. 
 
Answering your question. Yes the CD boot up very properly, the unbuntu comes just fine, I chose install ubuntu and at the graphic steps it frezes randomely.
 
And Yes I did defragment the HD before booting to the liveCD.
 
Prior to the Acer I did the same operation on a VAIO laptop but with Vista on and everything went so smoothly and was extremely happy with the result (some buttons didnt work but of no importance to me). 
 
I am reading also the forums as much as possible but up to now I havent seen any similar trouble.

---

### Post by Imatech64 on 2010-03-25
Hello everybody,

I did used the alternate CD, without real success since when it came to installation almost all files were announced as corrupted !.

Nevertheless, I used the main menu to delete the "ubuntu partition". Obviousely this helped since I retried afterwards to boot from the ubuntu 9.10 liveCd and everything worked very smoothly with an excellent final result.

---

