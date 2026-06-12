---
title: "hp 1020/cannot clear &quot;out of paper&quot;"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by nire on 2010-11-16
HP1020 is used to print both sides of paper. Worked under XP, but that PC gave up. Under 10.04 LTS, a desktop and a Acer netbook, both indicate "out of paper" when front half is printed, but neither permit clearing of "out of paper" condition. 
HP 1020 is USB connected; 10.04.1 LTS and kernal is 2.6.32-25 generic. Other than this the printers seems to work OK. 
Configue print drop down shows out of paper error and can only be cleared by deleting printer and restarting OS.  
Manage print jobs drop down shows processing, but doesn't have ability to clear status.

---

### Post by plucky on 2010-11-17
> **nire said:**
> HP1020 is used to print both sides of paper. Worked under XP, but that PC gave up. Under 10.04 LTS, a desktop and a Acer netbook, both indicate "out of paper" when front half is printed, but neither permit clearing of "out of paper" condition. 
HP 1020 is USB connected; 10.04.1 LTS and kernal is 2.6.32-25 generic. Other than this the printers seems to work OK. 
Configue print drop down shows out of paper error and can only be cleared by deleting printer and restarting OS.  
Manage print jobs drop down shows processing, but doesn't have ability to clear status.

I don't have your printer,but a useful troubleshooting tool is the CUPS interface.To access it,open Firefox and type into the address bar ```
http://127.0.0.1:631/
``` or ```
http://localhost:631/
``` should give you access to your printer configuration and administration interface.

Good Luck

---

### Post by nire on 2010-11-17
I've been trying to reply to your response for several hours unsuccessfully due to my ineptness as a newbie. I reviewed the CUPS document but I could not discern a probable answer. Ubuntu knows the printer is out of paper but does not give me a way to continue once I've reloaded paper.

thanks in advance for your assistance,

---

### Post by mps_1 on 2010-12-03
Dear all. 

I have the same problem (I'm using a KONICA-MINOLTA pagepro 5650 in a local network).

1. If there's no paper in printer when a job is sent, an "out of paper" warning shows up. Then, the printer is no longer accessible and reamins disconnected. I have to reboot or reinstall the printer to revert the problem.

2. If there is paper in printer when the job is sent, there is no problem and the printer works OK, although it is out of paper during the printing.

It seems that system cannot recover from an "out of paper" warning.

Thanks a lot for the help.

---

