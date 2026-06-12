---
title: "LATEST WIRELESS EnGenius ADAPTOR"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by nabilsatvilkar on 2008-04-14
I have brought a latest EnGenius EUB9701 Wireless USB Adapter :), got a macbook pro with ubuntu installed:guitar:.Ubuntu seems not to recognize this adapter:(... can anyone advise how to install this adapter in Ubuntu:confused:

---

### Post by chili555 on 2008-04-14
Usually, when a card is not recognized, it's because a driver can't be found or loaded. Sometimes, there is a driver and we need to identify it and load it up. Sometimes, in new cards, no Linux driver exists yet, and we must use a wrapper and the Windows driver.  First, let's find out what we have. Please plug in the device, open up a terminal and do:```
lsusb
lshw -C network
```Post the data that relates to your EnGenius and we'll go from there.

---

### Post by nabilsatvilkar on 2008-04-15
thanks a lot  ...will post the output result once i am back from office...

---

### Post by Chase1230 on 2008-04-23
I am also having the same problem with the USB wireless adapter (model:eub-9701). I see there was something said about "wrapping" it or something?  Is there a way to get this to work still?  Any assisstance woudl help.



I typed 'lsusb' in a terminal in ubuntu...

    
    Bus 001 Device 007: ID 148f:2870 Ralink Technology, Corp. 


...that's what it said we were dealing with.


-typing 'lshw' said I should be a power user to run it (or something like that).

---

### Post by chili555 on 2008-04-23
Please try:```
sudo lshw -C network
```with the device plugged in and post the result. Thanks.

---

### Post by Chase1230 on 2008-04-24
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 003: ID 148f:2870 Ralink Technology, Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c032 Logitech, Inc. MouseMan iFeel
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ sudo lshw -C network
ubuntu@ubuntu:~$          



It looked like it was thinking about something for a second - scanning or something - but nothing happened.

---

### Post by chili555 on 2008-04-24
> I see there was something said about "wrapping" it or something?Ndiswrapper! There are hundreds of posts about this on this forum, not necessarily about your exact card. It involves installing the ndiswrapper packages and associating them with the Windows driver from the disk you got with the device. You will want to get the .inf and .sys files from the disk or a Windows installation and copy them to your /home/user (/home/chili? /home/chase-laptop? whatever?) directory.

Here is a good tutorial: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It concentrates on the Broadcom chip, but the steps are the same. You probably will not have to worry about the 'blacklist' step.

Good luck.

---

