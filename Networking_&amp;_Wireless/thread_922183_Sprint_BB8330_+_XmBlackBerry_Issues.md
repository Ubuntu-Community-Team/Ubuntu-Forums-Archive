---
title: "Sprint BB8330 + XmBlackBerry Issues"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by shupej on 2008-09-17
I just changed to a new Blackberry 8330 from Sprint and am working on setting up tethering with Ubuntu 8.04. I've set up berry and made sure that the phone is being detected via USB, and yet XmBlackBerry errors out. I'm thinking it may be a driver issue since I can't find any definite information on using the 8330 phone and it doesn't specify the model number in the btool output. I had to use a CVS snapshot of berry to even get it to detect it, and I've tried both stable and CVS versions of XmBlackBerry as well. Any ideas where to start?

shupej@htcli1:~$ sudo btool -l
Blackberry devices found:
Device ID: 0x80677f0. PIN: <removed>, Description: RIM BlackBerry Device
shupej@htcli1:~$ sudo XmBlackBerry 
XmBlackBerry.c:OptionPopupCallback(1026) - GPRS modem device Not available

---

### Post by ryeknow on 2008-10-10
> **shupej said:**
> I just changed to a new Blackberry 8330 from Sprint and am working on setting up tethering with Ubuntu 8.04. I've set up berry and made sure that the phone is being detected via USB, and yet XmBlackBerry errors out. I'm thinking it may be a driver issue since I can't find any definite information on using the 8330 phone and it doesn't specify the model number in the btool output. I had to use a CVS snapshot of berry to even get it to detect it, and I've tried both stable and CVS versions of XmBlackBerry as well. Any ideas where to start?

shupej@htcli1:~$ sudo btool -l
Blackberry devices found:
Device ID: 0x80677f0. PIN: <removed>, Description: RIM BlackBerry Device
shupej@htcli1:~$ sudo XmBlackBerry 
XmBlackBerry.c:OptionPopupCallback(1026) - GPRS modem device Not available

Can you use the 8330 curve for internet access or only sync with the computer?

---

