---
title: "old battery"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by pdlethbridge on 2009-07-06
My computer is getting slower on the boot. In particular the bios part. I'm thinking that the battery on the mother board is getting weak. Any thoughts and suggestions are welcomed and appreciated. I have an MSI 865 pe board with a 2.6 gig p4

---

### Post by HermanAB on 2009-07-06
Uhmm, no.  Not the little battery no...

---

### Post by wojox on 2009-07-06
You can disable the services you don't need to make your system boot faster.

---

### Post by nhasian on 2009-07-07
things to make your bios boot faster:

1) update to the latest motherboard bios
2) enter the bios and have it autodetect your hard disk(s) and cdrom.  then set the unused channels on the hard disk controller to DISABLED so it doesnt poll them for new drives every time you turn your computer on.
3) disable floppy seek

The battery on the motherboard only has one function to power the real time clock and save your bios settings.  if the battery fails your date and time will get reset every time you power off your computer and you'll lose any bios settings you've made.  Luckily the battery is easy to replace if you need to.

> **pdlethbridge said:**
> My computer is getting slower on the boot. In particular the bios part. I'm thinking that the battery on the mother board is getting weak. Any thoughts and suggestions are welcomed and appreciated. I have an MSI 865 pe board with a 2.6 gig p4

---

### Post by expatCM on 2009-07-07
As the system starts you see white letters on a black screen.  Does the system pause for a long time at any one particular line?  If it does this would give you a good idea about what is wrong.   It could for example be that your hard drive is in the process of failing ......

---

### Post by pdlethbridge on 2009-07-07
Actually it pauses before it even gets to the bios. My monitor stays yellow and when it finally starts in the bios the monitor light goes green. Thats why I thought it was the battery. I have Ubuntu 9.04, Now I'm thinking power supply. Once the computer is running it seems fine. I don't hear any unusual sounds and I have seen no problems of any kind.

---

### Post by LowSky on 2009-07-07
it could  be a bad capacitor, most likely onthe motherboard. Check your motherboard for capicotrs that are leaking or if the look swollen or about to burst, Its a classic sign that a motherboard is about to go bad. Those older P4 board dont last very long. Too much heat.

 A power suppply tester like these
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=power+supply+tester](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=power+supply+tester)
Can see if your power supply is good. cheap investment for expensive parts

---

### Post by expatCM on 2009-07-07
A bad capacitor on the motherboard ...  yes, that is a nice idea.  Not seen one of those for a while though.

It could also perhaps be a bad power supply.  It may be a good idea to swap out the existing supply and test.  That is easy to do and would then narrow down the cause of the problem.

---

