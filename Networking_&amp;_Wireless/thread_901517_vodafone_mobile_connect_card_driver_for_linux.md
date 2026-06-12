---
title: "vodafone mobile connect card driver for linux"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by david sousa on 2008-08-26
Hey! 

I have an HP Compaq 6720s with Hardy Heron and i got an USB 7,2 Mb internet card from a mobile company here in Portugal.

Well the thing is that they don't have support for linux and i would like to get this thing working here.

I installed vodafone-mobile-connect-card-driver-for-linux because it works with other cell phone companys but i don't even know if it's well installed because it should have created a Dip group for me to be added but it doesn't really exist. So when i try do initialize with:

alt + F2 -> vodafone-mobile-connect-card-driver-for-linux -> it says:

" Permession problem

Vodafone Mobile Connect Card driver for Linux needs the following files and dirs with some specific permissions in order to work properly: /etc/ppp/pap-secrets should have 0660 mode, found 0777 /etc/ppp/chap-secrets should have 0660 mode, found 0777 "

I tryed this instructions here:

[http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux](http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux)

but without success because as i said i don't find a dip group for me to be added.

So if someone have a clue, please say something. 

Thanks

---

### Post by david sousa on 2008-08-26
I got the program working reinstalling it with a .deb package wich i found but in an older version. Now i just don't know how to configure it to start using internet from the USB drive.

I have a picture here of my situation:

[[IMG]http://img222.imageshack.us/img222/9900/capturaecrakn1.th.png[/IMG]](http://img222.imageshack.us/my.php?image=capturaecrakn1.png)

---

### Post by GeorgeVita on 2008-08-27
Hi,
most times "device type" is "GPRS/3G" modem, "Data Port" and/or "Control Port" for an only one attached USB modem is "/dev/ttyUSB0".

You can check this from a terminal window by typing:
ls /dev/ttyUSB*

Response without your modem:
ls: cannot access /dev/ttyUSB*: No such file or directory

Plug in the modem to the USB port, wait 5-10 seconds and type again the command: ls /dev/ttyUSB*
now it will shows something like:
/dev/ttyUSB0  /dev/ttyUSB1
(at least ttyUSB0 and possibly more ttyUSBx)
 
If you want to use the s/w you mentioned, try to enter the parameters above. If you would like to use "native" commands from Ubuntu 8.04 terminal window see:
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982&tstart=0&orderStr=9](http://forum.huawei.com/jive4/thread.jspa?threadID=322982&tstart=0&orderStr=9)

bye
G.V.

---

### Post by david sousa on 2008-08-27
Thanks for your reply!

The only option i have at "Device type" is serial. So i can't chose "GPRS/3G".

Then when i type "ls /dev/ttyUSB*" at the terminal without or with the pen plugged in i allways get that message:

"ls: cannot access /dev/ttyUSB*: No such file or directory"

And i went to the directory /dev to find that file and it was not there.

One more last question... What number do i put at the last box?

And finaly, what can i do???

---

### Post by GeorgeVita on 2008-08-27
Can you give some info for the modem? Manufacturer, model etc. Is it USB connected?

Note: there are many ways to connect with a 3G modem like specific program/driver from the manufacturer or provider, wvdial (dialler program which runs unter terminal window), network manager (the 2 pc screen upper right, beside the volume control), gnom ppp, etc
At first we are going to determine the type of your modem in order to find later the appropriate (or most preferable) way to dial.

---

### Post by david sousa on 2008-08-27
USB 7,2 - Option Icon 225 (Large Bandwidth) - Designed in E.U. by Option Made in Ireland

I think it's not important but my cell phone company is TMN - Portugal

---

### Post by GeorgeVita on 2008-08-27
Boot Ubuntu without modem, open a terminal window, execute the command lsusb, copy paste the results. Plug in modem, wait 10 seconds, again lsusb, copy paste the results. If it shows any modem do ls /dev/ttyUSB* and post all results.

---

### Post by david sousa on 2008-08-27
I only have 3 usb doors but the ouput shows me more. Isn't it strange?

First output:

"
david@David:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0af0:6971 Option 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 "

Second output:

"
david@David:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 0af0:6971 Option 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
"
Last ouput:

"
david@David:~$ /dev/ttyUSB*
bash: /dev/ttyUSB*: Ficheiro ou directoria inexistente
"
 
This means that the file or directory doesn't exist.

---

### Post by GeorgeVita on 2008-08-27
Your modem is possibly the [http://www.option.com/products/icon225.shtml](http://www.option.com/products/icon225.shtml)
which gives Bus 003 Device 005: ID 0af0:6971 Option
It is more complicated to see why it does not give you ttyUSBx
We need time to google, and possibly another ubuntu user to give info.

---

### Post by david sousa on 2008-08-27
When i go at /dev i can't find ttyusb

---

### Post by GeorgeVita on 2008-08-27
Can you check and post the result of the following command? (from a terminal window, first plug in the modem to USB port, wait for 10 seconds)

ls /dev/ttyU* /dev/ttyA* /dev/mod*

---

### Post by david sousa on 2008-08-27
david@David:~$ sudo ls /dev/ttyU* /dev/ttyA* /dev/mod*
[sudo] password for david: 
ls: não consigo aceder a /dev/ttyU*: Ficheiro ou directoria inexistente
ls: não consigo aceder a /dev/ttyA*: Ficheiro ou directoria inexistente
ls: não consigo aceder a /dev/mod*: Ficheiro ou directoria inexistente
 
This means:

"ls: I can't access to <something>: File or directory doesn't exist"

---

### Post by GeorgeVita on 2008-08-27
Let's have a summary:

Your modem is attached on USB port, recognized by the system as ID 0af0:6971 Option but the system does not assign any /dev/ttyUSBx or /dev/ttyACMx or /dev/modem

From search to google, found that "ID 0af0:6971 Option" is this modem:
[http://www.option.com/products/icon225.shtml](http://www.option.com/products/icon225.shtml)

Some others (google search "usbserial 0af0:6971 option") have tried the command
modprobe usbserial vendor=0xaf0 product=0x6971
which adds the above ID and assigns a ttyUSBx

I haven't use this command so if you want try it with the modem plugged in. Then you have to **ls /dev/ttyU* /dev/ttyA* /dev/mod***

---

### Post by david sousa on 2008-08-27
Same output...

david@David:~$ ls /dev/ttyU* /dev/ttyA* /dev/mod*
ls: não consigo aceder a /dev/ttyU*: Ficheiro ou directoria inexistente
ls: não consigo aceder a /dev/ttyA*: Ficheiro ou directoria inexistente
ls: não consigo aceder a /dev/mod*: Ficheiro ou directoria inexistente
 
I tried to find this here: [http://www.option.com/support/globetrotter_rc/rc_downloads.shtml#](http://www.option.com/support/globetrotter_rc/rc_downloads.shtml#)

but no download for linux..

---

### Post by david sousa on 2008-08-28
I found the last stable version of this program and instructions here:

[http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux](http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux)

But when start it from terminal with:

"gksudo vodafone-mobile-connect-card-driver-for-linux"

I don't get the first window of configuration so I allways start here: 

[[IMG]http://img337.imageshack.us/img337/6040/capturaecrank4.png[/IMG]](http://imageshack.us)
[[IMG]http://img337.imageshack.us/img337/6040/capturaecrank4.e8d5db34df.jpg[/IMG]](http://g.imageshack.us/g.php?h=337&i=capturaecrank4.png)

The problem is that i can't use the program functions. It's to strange. It seams like it is read only because i can't click the buttons. And if i could i could try to configure this to start working.

---

