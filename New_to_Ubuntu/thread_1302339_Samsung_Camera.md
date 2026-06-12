---
title: "Samsung Camera"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by DD70 on 2009-10-27
Hi
I am all new to this Ubunto system and I am having lots of problems. Some I amd my friendly guru have fixed. This one i thought i mifght try to solve with your help.
Tried to connect my camera, a Samsung digital ES55

Followed the instructions as per systems help and support bu all the camera say is "conecting to USB" 
The camera is not being recognised by the computer in a USB drive
Please help:(

---

### Post by anewguy on 2009-10-27
Please do the following and post back the results:

- plug in your camera to a USB port

- open a terminal window (applications/accessories/terminal)

- type:

sudo lsusb <press enter>


Just copy and paste the output back in a reply here.

Dave :)

---

### Post by DD70 on 2009-10-27
command not found

Dave now it seems to work. Any way it did this time

---

### Post by MelDJ on 2009-10-27
sudo lsusb <press enter>
means type sudo lsusb 
after typing press enter

---

### Post by anewguy on 2009-10-27
> **MelDJ said:**
> sudo lsusb <press enter>
means type sudo lsusb 
after typing press enter

I guess the "-type:" on the preceeding line wasn't a hint?

dave :)

---

### Post by DD70 on 2009-10-27
[sudo] password for owner:
Ihad typed in 1(one) instead of uppercaseI
Sorry
I

---

### Post by DD70 on 2009-10-27
It would appear after, playing around that it. I connect the camera to a usb port then reboot the pc. After rebooting switch on the camera it then recognises the camera and does what it is supposed to do.
But it wont pick up the camera simply by plugging in to a vacant usb

---

### Post by no2498 on 2009-10-27
install fspot
it finds the card if its in the cam
if no card you need a diff program for the cam

---

### Post by DD70 on 2009-10-29
fspot is installed as default. this is the problem it doesnt default to fspot as it should. it just doesnt pick up the camera unless i reboot as i stated in a earlier post

---

### Post by DD70 on 2009-11-01
Dave. Finally got the message you posted in my post re anti virus.Read out now is 

owner@owner-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f9:0204 Brother Industries, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
owner@owner-desktop:~$ 
I guess that the Brother reference is to do with my multi function printer scanner which is working fine

---

### Post by Prince.Paul.K on 2009-11-01
After plugging you camera in try

dmesg | tail

Post the results to have a better idea, if you are plugging it in the front usb, try it with the back usb ports and see..

---

### Post by anewguy on 2009-11-22
I am *SO SORRY* this is so late - I was going back through my past posts and saw you had replied here and I never replied back!  I hope you're still here!

If the lsusb you provided is with the camera plugged in, try it again with the camera plugged in but this time use "sudo lsusb".  If a new device (your camera) shows up then it is a permissions problem and we can work on that.

Again, I'm so sorry!

Dave :)

---

### Post by DD70 on 2009-11-23
owner@owner-desktop:~$ lsusb
Bus 001 Device 002: ID 1fab:1001  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f9:0204 Brother Industries, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
owner@owner-desktop:~$ sudo lsusb
[sudo] password for owner: 
Bus 001 Device 002: ID 1fab:1001  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f9:0204 Brother Industries, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
owner@owner-desktop:~$ 


I also replied to your message wih a little more detail

---

### Post by anewguy on 2009-12-08
Hummmmmm, doesn't seem to be a permissions problem as the same device is seen whether you are su or not.

Not sure why it is behaving the way it is.  Wish I could help you more!

dave :)

---

