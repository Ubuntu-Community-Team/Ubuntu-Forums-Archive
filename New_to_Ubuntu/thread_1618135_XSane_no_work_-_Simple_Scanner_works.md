---
title: "XSane no work - Simple Scanner works"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by mlempenau on 2010-11-10
HP scanjet 2400
Ubuntu 10.10

Using XSane I get a series of error messages.  First Error during CMS conversion:  Could not open scanner ICM profile.  Second same as the first.  Then Failed to start scanner:  Invalid argument.  

Simple scan works ...  I would like to first of all understand what the errors are telling me.  Then maybe I can understand why one works and the other doesn't.  thanks

---

### Post by HermanAB on 2010-11-10
Howdy,

Copy and paste the error messages into [http://google.com/linux](http://google.com/linux)

---

### Post by rburkartjo on 2010-11-11
mle, this link might help

[http://bobthegnome.blogspot.com/2010/11/using-latest-sane-drivers-in-ubuntu.html](http://bobthegnome.blogspot.com/2010/11/using-latest-sane-drivers-in-ubuntu.html)

---

### Post by mlempenau on 2010-11-11
Can someone tell me what I need to do to correct this problem?  
scanimage -L is telling me that the port I'm using is wrong.  Gphoto2 seems to agree.  How do I change this to a correct port?


mikee@mike-desktop:~$ gphoto2 --list-ports
Devices found: 9
Path                             Description
--------------------------------------------------------------
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:                             Universal Serial Bus            
usb:002,005                      Universal Serial Bus            
usb:002,004                      Universal Serial Bus            
usb:002,003                      Universal Serial Bus            
mikee@mike-desktop:~$ scanimage -L
[gphoto2] init_gphoto2: error: serial:/dev/ttyd1 is not a valid gphoto2 port.  Use "gphoto2 --list-ports" for list.
device `test:0' is a Noname frontend-tester virtual device
device `test:1' is a Noname frontend-tester virtual device
mikee@mike-desktop:~$

---

