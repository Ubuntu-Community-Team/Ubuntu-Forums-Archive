---
title: "Networked printer"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by gerryex on 2010-05-09
Hi ALL,
 
I just bought a new Canon printer (MX870) with built-in WiFi and it works perfectly with my main desktop running Win 7. My laptop dual boots to Win 7 (where it also works) and U 9.10 where I'm having trouble getting anything to work with the printer. I know there may not be a U driver for the printer but I would assume there should be some sort of generic driver that would at least allow basic printing.
 
When I go to SYSTEM - ADMIN - PRINTING and click on NEW - PRINTER it says it searching but nothing is found. Then I try to SELECT DEVICE and choose NETWORK and then FIND NETWORK PRINTER but then it asks for HOST. What do I put there. The printer is networked via WiFi through an Actiontec router WiFi access point which is the standard equipment for Verizon FiOS. Both my desktop and laptop (when running Win 7) find the printer with no problem and I never had to enter any kind of host.
 
Thanks,
Gerry

---

### Post by cjazz on 2010-05-09
You might want to try [this driver]("http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html").

---

### Post by gerryex on 2010-05-10
> **cjazz said:**
> You might want to try [this driver]("http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html").
 
Hi cjazz,
 
Thanks for the link to a driver. I'm still relatively new to U so I'm not quite sure how to install the driver. Do I just run it or do files need to be extracted. Will it automatically find the printer over the network or do I have to do something else.
 
Is there a primer somewhere on how to install a driver? Any other help would be greatly appreciated!!
 
Thanks,
Gerry

---

### Post by narendraD on 2010-05-10
At the bottom of the page linked above, the download option for the driver is given. Download and save it. Once downloaded right click and select extract. Once extracted double click and follow the instructions.

---

### Post by gerryex on 2010-05-10
Hi ALL,
 
Well, I'll be darned - IT WORKED!!! After I extracted it there was a couple of folders and a single file. I doubleclicked on the single file and chose RUN. But nothing seemed to happen. Then I tried it again but selected Run in Terminal, and that seemed to do the trick! It asked me for my password then ran through a few things and then asked if it was locally connected or networked. When I selected networked it said it was searching for printers and within a few seconds it found it and then a few more questions and when it finished I went into the printing application and low and behold the printer was there. I tried a test print and a print from Open Office and they both printed just fine.
 
I wish I was more familiar with U. I'm a retired software engineer and I am very familiar with Windows as I have been using it since Win 3.1!!! I also used Unix way (way) back when it first came out but it never my primary system. In those days it was strictly a text only environment and I found the syntax very user UN-friendly. Today's Linix-es are more user friendly with their graphical interfaces, but there are still too many times you need to drop back to the text only environment which is still to user UN-friendly!!!
 
But. . . . thanks to all for your help!!!!!
Gerry

---

### Post by narendraD on 2010-05-11
Thats Good. Now Pl mark the thread as SOLVED.

---

### Post by cjazz on 2010-05-11
Gerry,

As a software engineer, I'm sure you know this far better than I do, but it's amazing how familiarity with a system tends to increase its user friendliness. I've gotten to the point where generally the way things are done in Linux just seem to make more sense to me.

Anyway, I'm really glad to hear your printer driver is functioning. Good work.

---

