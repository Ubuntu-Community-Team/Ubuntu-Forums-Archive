---
title: "HP Laserjet 1000 problem"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Kirk202 on 2009-04-21
I'm new to Ubuntu and have installed 9.04 Jaunty.  Installation discovered my Laserjet 1000 but it won't print.  It says that the file/page has printed but didn't.

I installed hplip using the Synaptic Package Manager, set the printer up with 'sudo hp-setup' and the problem is still the same, although I got a message that the "Printer is ready to Print."  I do have the HPLIP Tool Box now under the Preferences menu but it won't open, it flickers like it's opening but disappears.

Any help is appreciated.

thanks,

-Kirk

---

### Post by bumanie on 2009-04-21
You could try using the HP self-extracting installer from [here]("http://hplipopensource.com/hplip-web/index.html"). It will take about 20 minutes. If there are any dependency issues, it will tell you what they are and stop the installation. I guess you have checked that your printer is supported - the majority of HP's have good support, but there are few that don't.

---

### Post by LowSky on 2009-04-21
> **bumanie said:**
> You could try using the HP self-extracting installer from [here]("http://hplipopensource.com/hplip-web/index.html"). 

+1, its the best way to get HP printers working

---

### Post by Kirk202 on 2009-04-21
Thanks, I did as you suggested and the problem still exists.

I got a message at the end of the installation that said:

HPUDEXT could not be loaded. Please check HPLIP Installation.

I don't know what I should look for or where.

Anyway, it added the printer and the HPLIP Tool Box disappeared from the Preferences menu, but I still have the same problem.

Appreciate your help,

-Kirk

---

### Post by tundraquad on 2009-05-26
A very _**easy**_ & clean way **which worked** in Jaunty:
unplug usb > del any printer
> from Synaptic, remove any foo, foomatic, hp , hplip , hpoj
> reboot > install hplip-3.9.4b (just double-click the *.run)
> plug usb when rqrd > close all printer config windows > 
> set hp-Laserjet-10002 as default printer > open HP Device Mgr > Actions > Install required plugin > select ...from HP authorized...    => printer should spool.
> reboot cpt (should spool during start) > perform a printing test > del printer hp-Laserjet-1000

---

### Post by bhoeneis on 2009-06-14
I am using Jaunty an ran into a similar problem. I changed from foo2zjs PPD driver to hpijs driver as follows:
-> System -> Administration -> Printing
-> Settings -> [Change] (Make and Model)
-> HP -> [Forward]
-> Laserjet 1000 -> HP Laserjet 1000 hpijs [en] -> [Forward]
-> Use the New PPD as is -> [Apply]

This works for me!

(You might need to unplug the USB Cable for a moment and/or switch your Printer off and on to force a reset.)

Good luck!

More about this problem:
- [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722)
- [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722/comments/11](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722/comments/11)

---

### Post by TRANQU111TY on 2009-07-01
> **bhoeneis said:**
> 
-> System -> Administration -> Printing
-> Settings -> [Change] (Make and Model)
-> HP -> [Forward]
-> Laserjet 1000 -> HP Laserjet 1000 hpijs [en] -> [Forward]
-> Use the New PPD as is -> [Apply]


This works for my hp LaserJet 1000 Series! Thank you!

---

### Post by TRANQU111TY on 2009-09-13
> **TRANQU111TY said:**
> This works for my hp LaserJet 1000 Series! Thank you!

Unfortunately it didn't work for me in 64-Bit so I went [here]("http://hplipopensource.com/hplip-web/install/install/index.html") and followed the instructions and it works!

---

### Post by gregtomko on 2010-07-14
The post by bhoeneis using the printer settings gui WORKED for me using the 32bit ubuntu 9.10    Thanks so much!!!!!

---

### Post by anant_crp on 2010-12-26
Hello,
 
I also tested the same thing on ubuntu 10.04 on PII with 512MB RAM. system with minimum packages loaded on. The Ubuntu is installed on that system using APTonCD.
 
The procedure what you are suggesting has been tried out & it was not working.so we our self made the experiment & succeeded.
 
 
Thanks
Anant
 
> **bhoeneis said:**
> I am using Jaunty an ran into a similar problem. I changed from foo2zjs PPD driver to hpijs driver as follows:
-> System -> Administration -> Printing
-> Settings -> [Change] (Make and Model)
-> HP -> [Forward]
-> Laserjet 1000 -> HP Laserjet 1000 hpijs [en] -> [Forward]
-> Use the New PPD as is -> [Apply]
 
This works for me!
 
(You might need to unplug the USB Cable for a moment and/or switch your Printer off and on to force a reset.)
 
Good luck!
 
More about this problem:
- [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722)
- [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722/comments/11](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/136722/comments/11)

---

