---
title: "How do I load a wireless driver during installation?"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by oldcpu on 2007-06-16
At the point that it fails to detect my network, it tells me to go back to the network hardware detection step and choose a driver or something.  But when I go back to that step, it tries to auto-detect my connection again.

So just how do I choose a driver for my wireless?

According to this site:

[http://linux-wless.passys.nl/query_part.php?brandname=I-O+Data](http://linux-wless.passys.nl/query_part.php?brandname=I-O+Data)

My USB wireless should have been detected.

---

### Post by chili555 on 2007-06-16
Please let us see the CLI commands:```
sudo lshw -C network
lsmod | grep -i prism
```Thanks.

---

### Post by oldcpu on 2007-06-16
Bash says that lshw is not a command.

No output for `lsmod | grep -i prism`.  `lspci` did not even show my wireless network card.

I am sure the USB ports and USB wireless card is fine.

---

### Post by chili555 on 2007-06-16
Are you certain you did```
sudo lshw -C network
```correctly? That's a lower case L there not a capitol I or a 1. l as in list. Let's also see:```
lsusb
```with the device inserted.

---

### Post by oldcpu on 2007-06-16
> Are you certain you did `sudo lshw -C network` correctly?
Yes.

I take it that that command is only available after I have installed a certain package?

`lsusb` detected it.
```
Bus 001 Device 002: ID 04bb: 0924 I-O Data Device, Inc.
```

---

### Post by chili555 on 2007-06-16
> that command is only available after I have installed a certain package?It should be present on any system out of the box.

There are conflicting reports as to what driver this card needs. Let's start easy and go from there. Please open a terminal and do:```
sudo tail -f /var/log/messages
```Leave it open so you can note, on paper, any kernel messages after the next step. Open a second terminal and do:```
sudo modprobe prism2_usb
```In the first terminal, did you see your I-O Data get registered or recognized in any way? If not, please try, in the second terminal:```
sudo modprobe hostap
```Any action?

---

### Post by oldcpu on 2007-06-16
Nothing from Terminal 1.  Terminal 2 returned with
```
FATAL: Module prism2_usb not found.
```  Nothing from the second command in Terminal 2.

---

### Post by kevdog on 2007-06-16
What kind of usb wireless device are you using anyway??  Can you provide some more details?? Thanks

---

### Post by oldcpu on 2007-06-16
> What kind of usb wireless device are you using anyway?? Can you provide some more details?? Thanks
Can you name me more than one kind?

---

