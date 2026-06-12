---
title: "help understanding efax error code"
date: 2023-03-28
forum: Networking &amp; Wireless
---

### Post by yeshua-1 on 2023-03-28
I've just installed efax in Ubuntu 22.04.2 and am using via the -gtk GUI
I have a small external usb fax modem attached
When trying to send a fax for the first time I received the following
I do note that the page which fails is not what I typed, the program seems to have added .001 after the .pdf
The rest I don't understand, but assume it builds of the first failed page
efax is suppose to be able to read pdf files
Advice appreciated
===================================
Socket running on port 9900
efax-0.9a: 19:57:33 opened /dev/ttyS1
efax-0.9a: 19:57:33 failed page /home/vvltr.pdf.001
efax-0.9a: 19:57:33 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:34 Error: fax device write: Input/output error
efax-0.9a: 19:57:36 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:38 Error: fax device write: Input/output error
efax-0.9a: 19:57:40 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:40 sync: dropping DTR
efax-0.9a: 19:57:40 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:40 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:42 Error: fax device write: Input/output error
efax-0.9a: 19:57:44 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:44 Error: fax device write: Input/output error
efax-0.9a: 19:57:44 Error: fax device write: Input/output error
efax-0.9a: 19:57:44 sync: sending escapes
efax-0.9a: 19:57:44 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:44 Error: fax device write: Input/output error
efax-0.9a: 19:57:44 Error: fax device write: Input/output error
efax-0.9a: 19:57:46 Error: fax device write: Input/output error
efax-0.9a: 19:57:48 Error: fax device write: Input/output error
efax-0.9a: 19:57:50 Error: sync: modem not responding
efax-0.9a: 19:57:50 Error: tcgetattr on fd=7 failed: Input/output error
efax-0.9a: 19:57:50 finished - unrecoverable error
===================================

---

### Post by Holger_Gehrke on 2023-03-28
Do you actually have a serial port (USB modems usually are on other device files - /dev/ttyUSB*) and is that port /dev/ttyS1 ? Are you a member of the group 'dialout' (you need to be to be allowed to write to the serial port) ?

Holger

---

### Post by yeshua-1 on 2023-03-29
/dev/ does not list ttyUSB, it does list ttyS1, and efax setting are set to that . my account is a member of the dialout group.

---

