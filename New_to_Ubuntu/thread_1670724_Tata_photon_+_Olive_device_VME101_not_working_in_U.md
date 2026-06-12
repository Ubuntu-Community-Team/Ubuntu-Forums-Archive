---
title: "Tata photon + Olive device VME101 not working in Ubuntu 10.10"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by mehulphy on 2011-01-19
Hi,
I have recently bought Tata photon + Olive VME101 device, but it is not at all detected in the system. When I run "lsusb" it is not listed. I have followed all the steps given in user manual for the linux version but still not working. I am using ubuntu 10.10 right now. Someone help me....

---

### Post by mehulphy on 2011-01-21
Hey, 

Actually, I solved it by myself after putting some effort...what I did is as below...

On command line....
1) Write "cd /etc/usb_modeswitch.d"
2) Write "sudo gedit"
3) Text editor will get open.....paste the following text.

####################################################### 
# Haier CE 100 

DefaultVendor=  0x201e 
DefaultProduct= 0x2009 

TargetClass=    0xff 

MessageContent="5553424312345678000000000000061e000000000000000000000000000000" 
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000" 

NeedResponse=1 

CheckSuccess=10 

------------------------------------------------------------------

4) Click "Save" and name the file: "201e:2009" then close the file.
5) Now go to home folder and run: 

"sudo usb_modeswitch -c /etc/usb_modeswitch.d/201e\:2009"

Give root password, when asked and 

You will see the following output....

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 004 on bus 005 ...
Using endpoints 0x07 (out) and 0x86 (in)
Using endpoints 0x07 (out) and 0x86 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Qualcomm
   Model String: MMC Storage     
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Qualcomm, Incorporated
     Product: USB MMC Storage
  Serial No.: 000000000002
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x07 for message sending ...
Trying to send message 1 to endpoint 0x07 ...
 OK, message successfully sent
Reading the response to the message (CSW) ...
 OK, response successfully read (13 bytes).
Trying to send message 2 to endpoint 0x07 ...
 OK, message successfully sent
Reading the response to message 2 ...
 OK, response successfully read (0 bytes).
Resetting response endpoint 0x86
 Error resetting endpoint: -71
Resetting message endpoint 0x07
 Error resetting endpoint: -71

Checking for mode switch (max. 10 times, once per second) ...
 Waiting for original device to vanish ...
 Original device can't be accessed anymore. Good.
 Searching for target devices ...
 Searching for target devices ...
 Found correct target device

Mode switch succeeded. Bye.

Enjoy............:)

Every time you have to run the command as below, after plug in...

sudo usb_modeswitch -c /etc/usb_modeswitch.d/201e\:2009

---

### Post by amity2kare on 2011-02-15
mehulphy - thanks for the detailed instructions, but when i try to follow them step by step, I get stuck at the command

sudo usb_modeswitch -c /etc/usb_modeswitch.d/201e\:2009

The error it gives me is

Error: MessageContent hex string has uneven length. Aborting.

Any workaround for this? Any help would be greatly appreciated. This is the only place where I have got stuck. Everything else on my laptop is working great in Ubuntu 10.10. Just to update you, when i run 

lsusb

this is the output I get

amit@amitsharma:~$ lsusb
Bus 002 Device 010: ID 201e:2009  
Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 5986:0148 Acer, Inc 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amit@amitsharma:~$

---

### Post by euyakim on 2011-02-15
hey amity, try removing the single space from both the messagecontent strings,(MessageContent and MessageContent2), I had the same problem and it worked for me, in the sense that i got rid of the error. btw, i am using  Tata photon + Olive device on ubuntu 9.04

I could not get my modem detected however, sudo usb_modeswitch ... gives me "no devices found..nothing to do, bye" , hope it works for you.

thank you mehulphy for sharing the info. much appreciated.

---

### Post by mehulphy on 2011-02-22
Yes, Kindly remove that blank space in both the string. Hope it works.

---

### Post by mehulphy on 2011-02-22
Actually, if you don't want to run the command 

sudo usb_modeswitch -c /etc/usb_modeswitch.d/201e\:2009 

every time after you plug in, then do the following.

1) Open terminal
2) Write "gedit" and press "enter key"
3) Text editor will open, now paste the command

sudo usb_modeswitch -c /etc/usb_modeswitch.d/201e\:2009

4) Click "Save", and name the file "tata.sh" (You can give your own name)
5) Now, every time you don't have to run that long command, instead run 

./tata.sh

Enjoy......:)

---

### Post by Dekma on 2011-03-23
Thanks a lot mehulphy. Absolute genius. No hitches BUT (yes there always is a but :-)) I used the Network Connection icon to connect.  On Mobile Broadband I selected TATA PHOTON but I simply cannot connect. It keeps showing the "waves" of trying to connect & ultimately show "Network Disconnected" HELP !!!

---

### Post by Dekma on 2011-03-23
Solved !! In the Network Connections in the Mobile Broadband tab I inserted Username "internet" & password "internet". Checked the boxes "Connect Automatically" & "Available to all users". Voila !! It immediately connected. But still thanks to you I was encouraged to do the last itsy bitsy stuff myself. Take care.

---

### Post by pranesh on 2011-04-10
I followed all the steps and something went wrong in the mode switch. I get the following o/p


shap@pranesh:~$ sudo usb_modeswitch -c /etc/usb_modeswitch.d/201e\:2009
sudo: unable to resolve host pranesh

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 Found default devices (1)
 Found a default device NOT in target class mode
Accessing device 005 on bus 003 ...
Using endpoints 0x07 (out) and 0x86 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Qualcomm
   Model String: MMC Storage     
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Qualcomm, Incorporated
     Product: USB MMC Storage
  Serial No.: 000000000002
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x07 ...
 OK, message successfully sent
Reading the response to the message ...
 OK, response successfully read (13 bytes).

Checking for mode switch (max. 10 times, once per second) ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Original device still present after the timeout

Mode switch most likely failed. Bye.


lsusb o/p

shap@pranesh:~$ lsusb
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 201e:2009  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 024: ID 19d2:0108 ONDA Communication S.p.A. 
Bus 001 Device 003: ID 064e:c108 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Could anyone suggest something?

---

### Post by saurabhkamshetty on 2011-08-26
Just a simple method...
install WINE software 1.3 version...
it supports all windows applications in linux..
plug in n start surfing ....:P

---

### Post by kounserkhalid on 2012-04-29
hi ... could u please tell me what is messagecontent and messagecontent...
i did exactly as u posted but get this 

```
khalid@laptop:/etc/usb_modeswitch.d$ sudo usb_modeswitch -c /etc/usb_modeswitch.d/22f4\:0021

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 003 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x07 (out) and 0x86 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Qualcomm
   Model String: MMC Storage     
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Qualcomm, Incorporated
     Product: USB MMC Storage
  Serial No.: 00100_DATACAR
-------------------------
Setting up communication with interface 0
Using endpoint 0x07 for message sending ...
Trying to send message 1 to endpoint 0x07 ...
 OK, message successfully sent
Reading the response to message 1 (CSW) ...
 OK, response successfully read (13 bytes).
Trying to send message 2 to endpoint 0x07 ...
 OK, message successfully sent
Reading the response to message 2 (CSW) ...
 OK, response successfully read (13 bytes).
Resetting response endpoint 0x86
 Could not reset endpoint (probably harmless): -71
Resetting message endpoint 0x07
 Could not reset endpoint (probably harmless): -71
 Device is gone, skipping any further commands

Checking for mode switch (max. 10 times, once per second) ...
 Searching for target devices ...
 Searching for target devices ...

Found target device, now opening
 Found correct target device

Mode switch succeeded. Bye.
```

i changed product id and vedor id as in my case the are 0021 and 22f4

thanks in advance

---

### Post by oldos2er on 2012-04-29
Old thread closed.

kounserkhalid, please start a new thread. Since this one is old and marked 'Solved' it's not the best place to post a new question.

---

