---
title: "I want help please help me"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by hindustani.india on 2009-11-22
HI FRIENDS I AM A NEWBIE.. iam using 9.10 ubuntu, i have 2 issues.1) i am using motorola motorkr e6 and operator is aircel india.i want connect my phone to internet . i dont know how to connect please tell me step by step i also tried internet. please do not give any other links.. please help me help 2) yesterday i internet using time suddenly changed my password reset and system restart what is problem.. i want more details about my phone connection

---

### Post by poohman on 2009-11-22
[http://infoqueue.wordpress.com/2009/11/11/aircel-gprs-in-your-pc/](http://infoqueue.wordpress.com/2009/11/11/aircel-gprs-in-your-pc/)   
Try the above given link.
I have tried and connected to the net using a nokia 3500c using an airtel connection. I the biggest mistake that I made when doing that was trying to connect before subscribing for a grps connection from airtel, so even when I got all the settings in the system right I could not connect because of the subscription to airtel gprs. So make sure u call the aircell call centre to clear up with that.

Then u need to have wvdial installed, it can be done by apt-get install wvdial, but if u have absolutely no internet connectivity then u will have to download wvdial and its dependencies using the mobile through gprs and then transfer it to the system connecting it to the system.

Refer the following link for wvdial installation:
[http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html)

please ask the aircel support team for the access point,username, password to configure wvdial.conf

---

### Post by Elfy on 2009-11-22
Moved to Absolute Beginners.

---

### Post by praveesh on 2009-11-22
Connect your phone to computer using a usb or serial port or whatever you wish. You can refer your phone's manual to know how to connect to get internet (Since that's motorola , I don't know how to connect. In my nokia phone, I need to choose nokia mode , when the phone ask to select the mode). 

Then, at the top panel, at the right end, you can see an applet named network manager , just next to the volume control applet . Click on it  , then choose 'add new connection' . When Ubuntu ask to choose operator, select aircel . If you can't find aircel , you may want to add it . To know gprs settings, visit [http://forums.techarena.in/india-broadband/1159140.htm](http://forums.techarena.in/india-broadband/1159140.htm)   . To set proxy, system->preferences->network proxy  Done . You are connected .  

Was that helpful ? Do you want further explanation?

---

### Post by praveesh on 2009-11-25
when typr after lsusb this command root@sameer:~# lsusb
Bus 001 Device 003: ID 22b8:3802 Motorola PCS C330/C350L/C450/EZX GSM Phone (AT)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@sameer:~# sudo /sbin/modprobe usbserial vendor=2x2b8 product=3x802
FATAL: Error inserting usbserial (/lib/modules/2.6.31-15-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

what to do ? Can anyone please help?

---

