---
title: "Printer spams"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Kreazulle on 2010-07-07
Hello! My problem is:
I have a Hp LaserJet 4250 installed on a XP network (and this I cannot change). I also have a computer that runs Ubuntu 10.04 and I need to print from that computer also. All the XP running computers print without problems but the Linux one spam the task. For example: If I try to print a test page from Ubuntu, will print that page over and over again until U physically cancel the task from the printer. It does not stop the respective queue even if it runs out of paper :p. 
Can anyone please tell me what may cause this problem?

PS: I have run a troubleshot from the CUPS menu and there I got the following answer:
"There is no obvious solution to this problem"
and has generated a report that is to long for me to post here but I will if anyone deems to be necessary. 

Tank you in advance.

---

### Post by SoFl W on 2010-07-07
I am not sure if I would call that "spam"

Check your printers configuration.
System-> Administration-> Printing, right click on the printer, select properties.  Select job options.  What number is next to "copies"?

---

### Post by Kreazulle on 2010-07-07
The number is 1  to copy.

---

### Post by SoFl W on 2010-07-07
How about Policies, Error Policy.  If you switch that to abort job or stop printer what happens? **I don't know much about those two options**, I would try abort job first.

---

### Post by Kreazulle on 2010-07-08
First of all I would like to thank you for your advices but unfortunately it did not work.
I have changed the error policy to cancel jobs and it still spams. After that I have tried stop.
I`ve tried a 2 page test and it prints only the first page over and over again until canceled from the printer menu. This I`ve tried with and without the "collate" option from the OpenOffice printing menu. Same result.

Any ideas? Please?

Thank you so much!

---

### Post by Kreazulle on 2010-07-08
I have also installed Ubuntu 10.04 on another computer in the same network and has the same problems with the printer (same printer). This suggests to me one of two things:
- either I have installed Ubuntu wrong on both systems which I highly doubt it (I may be NOOB to Ubuntu but not to computers in generally) and both Ubuntu sys are up to date with the updates.
- or, there may be something wrong with the native printer server but this is only in regard to Ubuntu because all the XP systems work just fine. (The printer is on a stand alone IP adress on the network and has it`s own managing system) which does not get along very well with Ubuntu so far. 

My question is: Is this an Ubuntu issue which probably can be solved, or is it a firmware problem of the printer and I should probably drop it?

Thank you!

---

