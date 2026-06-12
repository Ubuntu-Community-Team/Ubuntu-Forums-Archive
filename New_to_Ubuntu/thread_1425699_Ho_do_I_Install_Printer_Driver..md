---
title: "Ho do I Install Printer Driver."
date: 2010-03-09
forum: New to Ubuntu
---

### Post by izzybrew on 2010-03-09
I have a Lexmark 7170 printer. The installed drivers don't work with this. I found and downloaded the linux driver for this printer. How do I install this driver? I am not familiar with linux.

---

### Post by halitech on 2010-03-09
Lexmark is not very linux friendly so not sure if you will get it to work or not. What file did you download and where did you download it from?

---

### Post by izzybrew on 2010-03-09
[http://www.opendrivers.com/driver/231844/lexmark-x7170-all-in-one-printer-driver-v1.0-1-linux-free-download.html](http://www.opendrivers.com/driver/231844/lexmark-x7170-all-in-one-printer-driver-v1.0-1-linux-free-download.html)

---

### Post by halitech on 2010-03-09
so is the file a tar.gz file?

---

### Post by izzybrew on 2010-03-09
X7170SampleSANE- 1.0-1.tar.gz

---

### Post by chaanakya_chiraag on 2010-03-09
First, you will have to right-click on the file and select "Extract Here" and wait.  It should create a folder.  Please post the contents of that folder here.

---

### Post by izzybrew on 2010-03-09
/home/izzy/Downloads/X7170SampleSANE-1.0-1/adfutil
/home/izzy/Downloads/X7170SampleSANE-1.0-1/backend
/home/izzy/Downloads/X7170SampleSANE-1.0-1/daemon
/home/izzy/Downloads/X7170SampleSANE-1.0-1/include
/home/izzy/Downloads/X7170SampleSANE-1.0-1/lexmark
/home/izzy/Downloads/X7170SampleSANE-1.0-1/sanei
/home/izzy/Downloads/X7170SampleSANE-1.0-1/setapps
/home/izzy/Downloads/X7170SampleSANE-1.0-1/acinclude.m4
/home/izzy/Downloads/X7170SampleSANE-1.0-1/aclocal.m4
/home/izzy/Downloads/X7170SampleSANE-1.0-1/AUTHORS
/home/izzy/Downloads/X7170SampleSANE-1.0-1/config.guess
/home/izzy/Downloads/X7170SampleSANE-1.0-1/config.log
/home/izzy/Downloads/X7170SampleSANE-1.0-1/config.sub
/home/izzy/Downloads/X7170SampleSANE-1.0-1/configure
/home/izzy/Downloads/X7170SampleSANE-1.0-1/configure.in
/home/izzy/Downloads/X7170SampleSANE-1.0-1/COPYING
/home/izzy/Downloads/X7170SampleSANE-1.0-1/install-sh
/home/izzy/Downloads/X7170SampleSANE-1.0-1/ltmain.sh
/home/izzy/Downloads/X7170SampleSANE-1.0-1/Makefile.in
/home/izzy/Downloads/X7170SampleSANE-1.0-1/mkinstalldirs
/home/izzy/Downloads/X7170SampleSANE-1.0-1/README

---

### Post by chaanakya_chiraag on 2010-03-09
Try this:
```
chmod +x /home/izzy/Downloads/X7170SampleSANE-1.0-1/install.sh
sudo /home/izzy/Downloads/X7170SampleSANE-1.0-1/install.sh
```

---

### Post by halitech on 2010-03-09
> **chaanakya_chiraag said:**
> Try this:
```
chmod +x /home/izzy/Downloads/X7170SampleSANE-1.0-1/install.sh
sudo /home/izzy/Downloads/X7170SampleSANE-1.0-1/install.sh
```

I don't see an install.sh file listed in the list of files the OP gave us. I see an install-sh but no install.sh. I'm thinking they are going to need to do ./configure, make, make install. 

Best thing to do is open the README file and see how it says to install the driver.

---

### Post by chaanakya_chiraag on 2010-03-09
> **halitech said:**
> I don't see an install.sh file listed in the list of files the OP gave us. I see an install-sh but no install.sh. I'm thinking they are going to need to do ./configure, make, make install. 

Best thing to do is open the README file and see how it says to install the driver.
Sorry I didn't see that :P  Yes, you are absolutely right - he will have to do configure, make and make install.
@izzybrew: Do these commands instead:
```
 cd /home/izzy/Downloads/X7170SampleSANE-1.0-1
./configure
make
sudo make install

```
Tell me how that works out.
- Chiraag

---

### Post by arunsub on 2010-04-14
> **chaanakya_chiraag said:**
> Sorry I didn't see that :P  Yes, you are absolutely right - he will have to do configure, make and make install.
@izzybrew: Do these commands instead:
```
 cd /home/izzy/Downloads/X7170SampleSANE-1.0-1
./configure
make
sudo make install

```
Tell me how that works out.
- Chiraag

WHen I tried the above mentioned steps, I got the following error. I would appreciate if you can help me.

error: lexmark-H/scannerdevice.h: No such file or directory
In file included from llpddk.cpp:51:
saneportmonitor.h:51:35: error: lexmark-H/portmonitor.h: No such file or directory
In file included from llpddk.cpp:52:
scanerrorcommunicator.h:47:42: error: lexmark-H/scanerrorinterface.h: No such file or directory
In file included from llpddk.cpp:51:
saneportmonitor.h:55: error: expected class-name before ‘{’ token
saneportmonitor.h:62: error: ‘PM_Error’ does not name a type
saneportmonitor.h:63: error: ‘PM_Error’ does not name a type
saneportmonitor.h:71: error: ‘PM_Error’ does not name a type
saneportmonitor.h:73: error: ‘PM_Error’ does not name a type
saneportmonitor.h:75: error: ‘PM_Error’ does not name a type
saneportmonitor.h:78: error: ‘PM_Error’ does not name a type
saneportmonitor.h:80: error: ‘PM_Error’ does not name a type
In file included from llpddk.cpp:52:
scanerrorcommunicator.h:49: error: expected class-name before ‘{’ token
scanerrorcommunicator.h:54: error: ‘ScanErrorInterface’ has not been declared
scanerrorcommunicator.h:54: error: expected ‘,’ or ‘...’ before ‘error’
scanerrorcommunicator.h:55: error: ‘ScanErrorInterface’ has not been declared
scanerrorcommunicator.h:55: error: ISO C++ forbids declaration of ‘UserDecision’ with no type
scanerrorcommunicator.h:55: error: expected ‘;’ before ‘GetUserDecision’
llpddk.cpp:56: error: expected constructor, destructor, or type conversion before ‘*’ token
llpddk.cpp: In function ‘SANE_Status llpddk_init()’:
llpddk.cpp:74: error: ‘sd’ was not declared in this scope
llpddk.cpp:74: error: expected type-specifier before ‘ScannerDevice’
llpddk.cpp:74: error: expected ‘;’ before ‘ScannerDevice’
llpddk.cpp: In function ‘void llpddk_attach_matching_devices(const char*, SANE_Status (*)(const char*))’:
llpddk.cpp:90: error: ‘class SanePortMonitor’ has no member named ‘PM_AttachDevice’
llpddk.cpp: In function ‘void llpddk_destroy()’:
llpddk.cpp:99: error: ‘sd’ was not declared in this scope
llpddk.cpp:100: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
llpddk.cpp: In function ‘SANE_Status llpddk_open_device(const SANE_Char*)’:
llpddk.cpp:114: error: ‘PortMonitor’ has not been declared
llpddk.cpp:114: error: expected ‘;’ before ‘pmerr’
llpddk.cpp:116: error: ‘pmerr’ was not declared in this scope
llpddk.cpp:116: error: ‘class SanePortMonitor’ has no member named ‘PM_SetDeviceName’
llpddk.cpp:117: error: ‘PortMonitor’ has not been declared
llpddk.cpp:120: error: ‘class SanePortMonitor’ has no member named ‘PM_Open’
llpddk.cpp:121: error: ‘PortMonitor’ has not been declared
llpddk.cpp: In function ‘void llpddk_close_device()’:
llpddk.cpp:130: error: ‘class SanePortMonitor’ has no member named ‘PM_Close’
llpddk.cpp: In function ‘SANE_Status llpddk_start_scan(Option_Value*)’:
llpddk.cpp:138: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:138: error: expected ‘;’ before ‘sderr’
llpddk.cpp:139: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:139: error: expected ‘;’ before ‘sdprop’
llpddk.cpp:142: error: ‘sdprop’ was not declared in this scope
llpddk.cpp:142: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:145: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:148: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:151: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:153: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:157: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:159: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:161: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:164: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:170: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:173: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:176: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:179: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:182: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:185: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:188: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:191: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:194: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:197: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:200: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:240: error: ‘sderr’ was not declared in this scope
llpddk.cpp:240: error: ‘sd’ was not declared in this scope
llpddk.cpp:241: error: ‘ScannerDevice’ has not been declared
llpddk.cpp: In function ‘long int llpddk_read_scan_data(SANE_Byte*, SANE_Int, int*)’:
llpddk.cpp:252: error: ‘sd’ was not declared in this scope
llpddk.cpp: In function ‘SANE_Status llpddk_abort_scan()’:
llpddk.cpp:261: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:261: error: expected ‘;’ before ‘sderr’
llpddk.cpp:264: error: ‘sderr’ was not declared in this scope
llpddk.cpp:264: error: ‘sd’ was not declared in this scope
llpddk.cpp:265: error: ‘ScannerDevice’ has not been declared
llpddk.cpp: In function ‘SANE_Status llpddk_end_scan()’:
llpddk.cpp:274: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:274: error: expected ‘;’ before ‘sderr’
llpddk.cpp:277: error: ‘sderr’ was not declared in this scope
llpddk.cpp:277: error: ‘sd’ was not declared in this scope
llpddk.cpp:278: error: ‘ScannerDevice’ has not been declared
llpddk.cpp: In function ‘SANE_Status llpddk_get_adf_status(unsigned char*)’:
llpddk.cpp:287: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:287: error: expected ‘;’ before ‘sderr’
llpddk.cpp:290: error: ‘sderr’ was not declared in this scope
llpddk.cpp:290: error: ‘sd’ was not declared in this scope
llpddk.cpp:293: error: ‘ScannerDevice’ has not been declared
llpddk.cpp: In function ‘void llpddk_report_error(int)’:
llpddk.cpp:302: error: ‘ScanErrorInterface’ has not been declared
make[1]: *** [llpddk.o] Error 1
make[1]: Leaving directory `/home/prabha/Downloads/X7170SampleSANE-1.0-1/lexmark'
make: *** [all-recursive] Error 1

---

### Post by arunsub on 2010-04-14
The README says
X7170 SANE Scanner Driver package requires the following:
      - sane-backend 1.0-13 development libraries
      - Lexmark USB scanner device driver (LEXUSB-SCANNER-1.0-1.TAR.GZ)
      -	X7170 LLPDDK binary (x7170llpddk-2.0-4.i386.rpm)

---

### Post by mal1958 on 2010-04-14
For what ever good this does, I copy/pased this from the README file that was included.  I don't have the printer/scanner but I figured this may help so I dl'ed the thing.

```
BASIC INSTALLATION
==================

    To install the X7170 SANE scanner driver, run the following commands:

      - ./configure
      - make
      - make install

    Make sure to have an entry for "lexmark" in /usr/local/etc/sane.d/dll.conf 
    for SANE to recognize the lexmark backend.

    To run the daemon which catches the scan button press event:
      - /etc/init.d/x7170d start
    To stop the daemon:
      - /etc/init.d/x7170d stop

    To run the x7170adfutil utility tool in command line to support PDF file format on ADF scanning:
      - x7170adfutil no_of_pages filename [or]
      - x7170adfutil no_of_pages [or]
      - x7170adfutil
    
    Note: This scanner driver was tested and verified in the following
          distributions:

      - Red Hat 8.0
      - Red Hat 9.0

      - Mandrake 9.0
      - Mandrake 9.1
      - Mandrake 9.2

      - SuSE 8.1
      - SuSE 8.2
      - SuSE 9.0

```

This is the Basic install in the README of the file.

---

