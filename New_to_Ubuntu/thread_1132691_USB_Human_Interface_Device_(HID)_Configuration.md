---
title: "USB Human Interface Device (HID) Configuration"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by drdave69 on 2009-04-22
I have a "Gyration Wireless RF Keyboard" and "Gyration Ultra Cordless Optical Mouse" combo. When I plug in the "USB Mini Dual Receiver" (GP9000-001) that comes with this set, nothing happens, Ubuntu does not recognize it at all. I know the unit works because I checked it on a Windows machine & it recognized it & installed the drivers automatically. After lots of research, I have come up with conflicting information on whether this product is Linux compatible or not.
I found this information:

Installing USB Devices on Linux
 Click here for USB Human Interface (HID) Configuration. 
Note: Gyration does not support use of its devices under the Linux OS. The link above has been provided as reference only. User assumes responsibility for installation under this OS.

Here: [http://www.gyration.com/t-TroubleShooting.aspx](http://www.gyration.com/t-TroubleShooting.aspx)

Which leads me to believe that it is possible to use this product in Ubuntu.

The above information links to here: [http://www.linux-usb.org/USB-guide/x194.html](http://www.linux-usb.org/USB-guide/x194.html)

After reading the above information, I do not understand how to > turn on USB Human Interface Device (HID) support in the USB support and Mouse Support in the Input core support
I am such a noob that the info above is way over my head.
Can someone please help me with this issue?
Thanks in advance, 
Dave

---

### Post by skymera on 2009-04-22
Hello :)

Can you plug in your devices and please post the output of

```
 lsusb 
```

---

### Post by drdave69 on 2009-04-22
> **skymera said:**
> Hello :)

Can you plug in your devices and please post the output of

```
 lsusb 
```
The strangest thing just happened. I plugged in my wireless keyboard/mouse, Ubuntu recognized it this time, but then my computer went absolutely crazy, new windows started popping up, new tabs, firefox switched to a "zoom out" view, and I'm sure other things I did not notice. I had to logout to regain control of the computer.
I forgot to mention that earlier today I installed "Wine" because I heard it would let me run windows applications. But I tested the wireless keyboard/mouse after this install and nothing worked. I have rebooted since then, so maybe it installed some drivers, I'm not sure.
I regained control, plugged the unit back in, and here is the output you requested:

david@DRDAVEROOM:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0c16:0001 Gyration, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 004: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
david@DRDAVEROOM:~$

---

### Post by skymera on 2009-04-22
That shows us that Ubuntu is detecting your devices :)
At least that's one step.

As for getting them to work, i have no idea =O
Do these devices need drivers installed in Windows?

edit:
[http://www.linuxquestions.org/hcl/showproduct.php?product=2195](http://www.linuxquestions.org/hcl/showproduct.php?product=2195)
Does this help at all?

---

### Post by drdave69 on 2009-04-22
> **skymera said:**
> That shows us that Ubuntu is detecting your devices :)
At least that's one step.

As for getting them to work, i have no idea =O
Do these devices need drivers installed in Windows?
yes I believe so, but windows installs them automatically, and I can not locate the drivers anywhere.

---

### Post by drdave69 on 2009-04-22
Never mind....I have come to the conclusion that the keyboard/mouse is defective, after further testing on windows, I found that the same erratic behavior that I experienced in Ubuntu happens in windows also.
My solution: buy an new wireless keyboard/mouse that is made for Linux.
Thanks for your help skymera :)
Dave

---

