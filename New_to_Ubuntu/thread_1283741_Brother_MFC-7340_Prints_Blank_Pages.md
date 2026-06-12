---
title: "Brother MFC-7340 Prints Blank Pages?"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2009-10-05
Afternoon,

It seems a have a teething problem with this printer. Whenever I send a document to print, whether its from OpenOffice or just a text editor the printer just prints out pages and pages of blank sheets?

I have followed the instructions here:
[http://raywoodcockslatest.blogspot.com/2009/09/installing-brother-mfc-7340.html](http://raywoodcockslatest.blogspot.com/2009/09/installing-brother-mfc-7340.html)

And they haven't helped at all, still have the same problem.

```

terry@terry-desktop:~$ dpkg -l | grep Brotherii  brmfc7340lpr                               2.0.2-1                                                 Brother MFC-7340 LPR driver
ii  cupswrappermfc7340                         2.0.2-1                                                 Brother MFC7340 CUPS wrapper driver
terry@terry-desktop:~$ 

```

Extra Information:
Running 9.04 64bit
Printer is Brother MFC-7340
Connected Via USB

If anyone can help/offer advice it would be gratefully appreciated.

Thanks,
Terry

---

### Post by falconindy on 2009-10-05
Is there any ability of the printer to create a test page on its own? The evidence you've provided isn't enough to put the blame on the OS.

---

### Post by terrykiwi83 on 2009-10-05
Yeah I have printed a test page, and again its totally blank and keeps printing until cancelled.

---

### Post by terrykiwi83 on 2011-05-12
Ok couple of years later and it still prints just blank pages, hopefully in the 3 years I have waited someone has a solution lol

?

```



$dpkg -l | grep Brother
ii  brmfc7340lpr                          2.0.2-1                                                    Brother MFC-7340 LPR driver
ii  cupswrappermfc7340                    2.0.2-1                                                    Brother MFC7340 CUPS wrapper driver


```

```


terry@terry-X58A-UD7 ~ $ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04f9:01e7 Brother Industries, Ltd 
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 004: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Anson S on 2011-05-26
I had the exact same problem as you, Terry, for a while. The printer problem was the only thing keeping me from switching totally to Ubuntu. How I got it fixed was to change the printer driver from the correct one for the printer (Brother HL-2140) to Brother HL-2030. Now it prints great. :P

---

### Post by jtarin on 2011-05-26
Do you have ghostscript installed?
Have your tried using the browser manager for CUPS?
As was mentioned it could quite possibly be a driver problem.

---

### Post by migs73 on 2011-05-26
I think these are all 32 bit drivers from Brother.

If you are still using the 64 bit OS you need the following installed;

**ia32-libs **or** lib32stdc++**

check that either of these is installed (use synaptic) if not install them and try again.

Hope this helps

Mike

---

### Post by plizzba on 2011-07-26
Dear Anson S,

Thank you so much! I switched to the Brother HL-2030 driver and I can finally print! (I've had the printer for over a year, and haven't been able to print until now.)

**EDIT:** After using this further, I realized that the system was not working perfectly. It printed a successful test page, but when I tried to print a pdf document, I had strange lines appearing under the letters. Later I had some success; see [this thread]("http://ubuntuforums.org/showthread.php?p=11092790#post11092790")

---

### Post by humanform on 2011-09-18
Anson S, you rock!
I previously found a long and complicated terminal command solution. This was so freaking easy. Thank you!

---

### Post by TedinOz on 2011-10-15
Same problem here using Brother HL 2040. I have just upgraded to 11.10 32bit. The printer is USB connected. It was working fine before the upgrade but now it just spits out blank pages until I turn it off. I have read a lot of the suggested solutions here but they all seem to relate specifically to the printer scanner in the thread title and I am not confident in adapting them to my printer. I tried to install cupswrapper hl2030 but it didn't change anything. I uninstalled it in Synaptic but it is still showing in the following 'dpkg -l | grep Brother'after I had removed it and installed the HL2040 drivers downloaded from Brother. I'm unsure what to do now as I feel I may have messed up more than I have fixed so hoping someone can set me straight please. I need my printer please :(

```
~$  dpkg -l | grep Brother
ii  brhl2040lpr                                   2.0.1-1                                    Brother HL-2040 LPR driver
rc  cupswrapperhl2030                             2.0.1-2                                    Brother HL2030 CUPS wrapper driver
ii  cupswrapperhl2040                             2.0.1-2                                    Brother HL2040 CUPS wrapper driver
ii  ptouch-driver                                 1.3-0ubuntu11                              CUPS/Foomatic driver for Brother P-touch label printers

ted@ted-Satellite-L300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 005 Device 002: ID 0d62:0530 Darfon Electronics Corp. 
Bus 006 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 014: ID 04f9:0028 Brother Industries, Ltd Printer


```






Hoping someone can help me get a handle on this. I know the printer is working fine as was able to run a test page from the machine itself but not from the computer when connected. Thanks in advance...


EDIT : I kept on searching and found a solution here [http://ubuntuforums.org/showthread.php?p=11345930#post11345930](http://ubuntuforums.org/showthread.php?p=11345930#post11345930). Thanks so much Ubuntu Forums.

---

