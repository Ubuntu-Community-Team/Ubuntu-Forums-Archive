---
title: "won't see my webcam at all"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by super kim on 2009-08-28
```
$ lsusb
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1b3b:2937  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

```there is nothing, i don't know where to start even :confused: someone please help, it is so my mum can talk to my sister with skype.

the camera is made my 'ikasu' and the ubuntu version is jaunty

---

### Post by rajeev1204 on 2009-08-28
> **super kim said:**
> ```
$ lsusb
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1b3b:2937  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

```there is nothing, i don't know where to start even :confused: someone please help, it is so my mum can talk to my sister with skype.

the camera is made my 'ikasu' and the ubuntu version is jaunty


I believe sunplus is your webcam.Ubuntu detects the chip inside the webcam and the actual model name doesnt matter.Sunplus chips are used in a lot of webcams.
Have you tried installing the software cheese and tried if it can detect it?

---

### Post by super kim on 2009-08-28
yes sunplus is the webcam.

"How to get your camera working:
To get your camera working with cheese, you will have to ensure that it works
with the Gstreamer Framework and Video4Linux2 (V4L2) or Video4Linux (V4L). To
test this, you can use the 'gstreamer-properties' tool."

i tested it and it didn't work with the Gtreamer Framework. so there is no point to installing cheese.
at least i know that it is called "Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc."

---

### Post by rajeev1204 on 2009-08-28
> **super kim said:**
> yes sunplus is the webcam.

"How to get your camera working:
To get your camera working with cheese, you will have to ensure that it works
with the Gstreamer Framework and Video4Linux2 (V4L2) or Video4Linux (V4L). To
test this, you can use the 'gstreamer-properties' tool."

i tested it and it didn't work with the Gtreamer Framework. so there is no point to installing cheese.
at least i know that it is called "Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc."

What do you get when you test it in skype?

---

### Post by super kim on 2009-08-28
> **rajeev1204 said:**
> What do you get when you test it in skype?
oh it just doesn't work, or ekiga.

---

### Post by rajeev1204 on 2009-08-28
> **super kim said:**
> oh it just doesn't work, or ekiga.

Can i see the output of dmesg.

---

### Post by super kim on 2009-08-28
> **rajeev1204 said:**
> Can i see the output of dmesg.
all of it???

---

### Post by rajeev1204 on 2009-08-28
> **super kim said:**
> all of it???

yes!go to paste.ubuntu.com and paste it there,give me the url.

---

### Post by super kim on 2009-08-28
> **rajeev1204 said:**
> yes!go to paste.ubuntu.com and paste it there,give me the url.
the terminal output is larger than i can scroll,

---

### Post by rajeev1204 on 2009-08-28
> **super kim said:**
> the terminal output is larger than i can scroll,

do this  dmesg > dmesg.txt

This copies contents of it to a file called dmesg.txt on system. then try it.

---

### Post by super kim on 2009-08-28
> **rajeev1204 said:**
> do this  dmesg > dmesg.txt

This copies contents of it to a file called dmesg.txt on system. then try it.


tried it, done that.
[http://paste.ubuntu.com/261147/](http://paste.ubuntu.com/261147/)
heres dmsg.txt link
thanks :P

---

### Post by rajeev1204 on 2009-08-28
Unplug the webcam,then plugin again to another usb port then in terminal

dmesg | tail

You should see a gspca module loaded or something,

In any case do this in terminal  

modprobe gscpa_sunplus

i go sleep ,cu tomorrow.

---

### Post by super kim on 2009-08-28
```
dmesg | tail
[58838.271557] usb 4-2.1: configuration #1 chosen from 1 choice
[58838.326503] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2.1/4-2.1:1.0/input/input11
[58838.329693] generic-usb 0003:045E:00E1.0002: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.2-2.1/input0
[58839.115744] input: btnx keyboard as /devices/virtual/input/input12
[58839.117806] input: btnx keyboard as /devices/virtual/input/input13
[58839.118043] input: btnx mouse as /devices/virtual/input/input14
[58839.207184] input: btnx mouse as /devices/virtual/input/input15
[58881.568066] usb 2-2: USB disconnect, address 5
[58883.884039] usb 2-1: new full speed USB device using uhci_hcd and address 6
[58884.111149] usb 2-1: configuration #1 chosen from 1 choice
``````
modprobe gscpa_sunplus
FATAL: Module gscpa_sunplus not found.
```
i sleep now too :)

---

### Post by rajeev1204 on 2009-08-29
> **super kim said:**
> ```
dmesg | tail
[58838.271557] usb 4-2.1: configuration #1 chosen from 1 choice
[58838.326503] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2.1/4-2.1:1.0/input/input11
[58838.329693] generic-usb 0003:045E:00E1.0002: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.2-2.1/input0
[58839.115744] input: btnx keyboard as /devices/virtual/input/input12
[58839.117806] input: btnx keyboard as /devices/virtual/input/input13
[58839.118043] input: btnx mouse as /devices/virtual/input/input14
[58839.207184] input: btnx mouse as /devices/virtual/input/input15
[58881.568066] usb 2-2: USB disconnect, address 5
[58883.884039] usb 2-1: new full speed USB device using uhci_hcd and address 6
[58884.111149] usb 2-1: configuration #1 chosen from 1 choice
``````
modprobe gscpa_sunplus
FATAL: Module gscpa_sunplus not found.
```
i sleep now too :)


ok type modprobe gspca and press tab until you see some options.

---

### Post by super kim on 2009-08-29
> **rajeev1204 said:**
> ok type modprobe gspca and press tab until you see some options.
no, getting nothing when i press tab, or if i hold it down. i am off out for the weekend but i will pick this up again on monday. thanks ranjeev for your time and what not :)

---

### Post by aljoriz on 2009-08-29
Sir, 
would you consider downloading easycam?  found it somewhere in the net (google) it installs the needed driver for your webcam based on the chip it uses.  It might help.

---

