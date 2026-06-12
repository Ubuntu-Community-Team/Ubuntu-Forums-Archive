---
title: "Wireless worked and now does not even recognise card...."
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by unseenmachine on 2007-10-09
I have a edimax 54mbs 802.11 b/g wirelss card, toshiba satillite A30 running Ubuntu Feisty 7.04.

I got the network connected with little problem, brought the laptop into the office and now it wont even pick up the wireless card....

i am a newbie to linux but am a technica\l support manager and have done everything i can think off and checked the forum...someone please help;

also if anyone know how i can get webguide4 working from linux then that would be great too....

thanks

---

### Post by kevdog on 2007-10-09
Can you post

lspci -nn
lshw -C network
iwlist scan

What kind of securtity does the network have that you are trying to connect to?

---

### Post by unseenmachine on 2007-10-10
It uses WPA 128 bit ascii - have no problems connecting when i boot into XP- 

ispci -nn reports : 

03:00.0 Network Controller [0280]: RaLink RT2500 802.11g Cardbus/Mini PCI [1814:0201] (rev 01)

lshw -C network reports: 

*-nertwork UNCLAIMED

Physical Id of: 0 
Bus Info :  pci@03.00.0
Version: 01
width: 32 bits
clock: 33 mhz
Configuration: latency=0
resources: irq:16

iwlist scan reports: 

lo

---

### Post by unseenmachine on 2007-10-10
sorry about that, 

iwlist scan reports:

lo interface doesn't support sanning.


Hope this helps, i have no option to use wireless networking in the network icon and does it matter if the card is in befor boot?

cheers

---

### Post by kevdog on 2007-10-10
This message:


*-nertwork UNCLAIMED

Means no driver is associated with your card.  You are probably going to have to install the serial monkey rt2500 driver to get this to work.  Im pointing you to a link that will advise you how to do this -- but be forewarned the guide is for the rt73 driver.  Follow the procedure except substitute rt2500 where rt73 is listed:


[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by unseenmachine on 2007-10-11
Now , thanks for the hints - i have not tried them as the card drivers are recognized now, i put it in roaming mode when it somehow picked up the card and now no problems with connecting.....cheers for your help bro

---

