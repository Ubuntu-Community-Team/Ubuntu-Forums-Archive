---
title: "Scanner Brother MFC 210C no longer works"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by ginestre on 2009-05-26
Until yesterday my scanner worked perfectly with xsane. Now it doesn't- I get an I/O error when I try to scan.

I haven't so far as I'm aware changed anything, though I do generally accept security upìgrades offered me. 

The message I get is 
Failed to start scannr: Invalid argument

The scann ris a Brother MFC 210 C

Any ideas, anyone?

---

### Post by JC Cheloven on 2009-05-26
The fact that it previously worked is a good startpoint ;-)
I'd suggest to reinstall sane, that will probably fix the problem, whatever it is.

But before getting drastic, perhaps you're willing to run a few commands on terminal, to see if the problem shows up:

'sudo sane-find-scanner'
identifies the scanner (vendor, product...). Not meaning that it is working, even supported. Only that sane sees it.

'scanimage -L' 
Lists every scanner that is present, recognized and supported.

'scanimage > myfyle.tiff'
Scans an image straightforward from command line. You can specify other extensions (.png. .jpg ...). If this works, the problem should stay merely in the gui.

---

### Post by ginestre on 2009-05-27
Thanks for the reply. I tried the sane commands, but simply returned a file not found error each time. I also tried substituting sane with xsane, same result. So I reinstalled xsane- same result again.

When I launch the xsane sacnning program, the window titles correctly report the scanner model no as they did before it broke. I presume the report is the same as before it broke but what it says now is 
xsane 0.995 MFC-210C: bus4; dev1

When I ask for a previw or a scan, it returns the message
Failed to start scanner: Invalid argument

Grateful for any more pointers.

TIA

---

### Post by Sef on 2009-05-27
copy and paste in this code:  ```
lsusb
```

Let's make sure that the computer is seeing it.

---

### Post by ginestre on 2009-05-27
> **Sef said:**
> copy and paste in this code:  ```
lsusb
```

Let's make sure that the computer is seeing it.

This is my output:
richard@richard-upstairs:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 04f9:0161 Brother Industries, Ltd 
Bus 001 Device 006: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 001 Device 005: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  
richard@richard-upstairs:~$ 

Looks to me as though Bus 4 Device 1 is empty? Right? 
And Bus 1 Device 8 has an entry for Brother, the MFC being the only Brother device on the USB- but it's a multifunction device- would it have a separate device number for the printer, scanner and fax that are all in it? I can still print, and I've never used the fax.

---

### Post by ginestre on 2009-05-28
Well, ain't that the damndest thing?

I have changed nothing since yesterday. I was waiting for some ideas from the community: but this evening, it works.

I haven't even in the meanwhile reset computer or scanner. It's all as it was yseterday. Except now it works.

Is this the definitive example of the ghost in the machine?

---

### Post by Screwdriver0815 on 2009-05-28
when you get an I/O error then the write/read permissions are set wrong (not sure about but something in this direction). To solve this, try the following:

open the file 

/etc/udev/rules.d/40-basic-permissions.rules 

(I asume its Intrepid Ibex, what you are using) and check the following lines: 

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"
```

if it is written like I posted it, change the MODE into "0666"

so after the modification it should be

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```

to do this, you need root-permission so use the command

```
sudo gedit /etc/udev/rules.d/40-basic-permissions.rules
```

then restart the system and try if it works. Note: if you had to change this file, you need to restart the OS. Trying right after the change without reboot will result in the same I/O error as before.

when it works occasionally, then maybe you have started XSANE with root permissions? This makes it work in the default settings but is dangerous

hope this helps!

---

### Post by JC Cheloven on 2009-05-29
> **ginestre said:**
> Well, ain't that the damndest thing?

I have changed nothing since yesterday. I was waiting for some ideas from the community: but this evening, it works.

I haven't even in the meanwhile reset computer or scanner. It's all as it was yseterday. Except now it works.

Is this the definitive example of the ghost in the machine?

One never ends getting surprised with computers :shock:

Glad it worked, but I'd try a ram memtest, and a surface disk exploration. Just to be sure you can still trust your box. This kind of unpredictable behaviour could be related to a hidden hardware problem, specially if the computer is old.

---

