---
title: "Vivitar DVR 870HD digital video camcorder"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by junglenut on 2010-01-07
Alright, so I have a Vivitar DVR 870HD I just picked up the other day. Retrieving the vids and pics off it wont be a problem since it all goes onto my SD card but my problem is that it has a webcam function and I'm utterly perturbed as to how to get it to work.

Its read as connected when I give lsusb. Cheese nor any other webcam program will pick it up though.

Anyone have any ideas? I'd be grateful for any help on this, guys.

---

### Post by Methuselah on 2010-01-07
It might not be supported.
If you plug it out and plug it back in while it is powered what does the **dmesg** command output near the end.

---

### Post by junglenut on 2010-01-07
[ 1012.927900] Linux video capture interface: v2.00
[ 1012.934027] zr364xx 4-1:1.0: Zoran 364xx compatible webcam plugged
[ 1012.934036] zr364xx 4-1:1.0: model 0595:4343 detected
[ 1012.934043] usb 4-1: 320x240 mode selected
[ 1012.934159] usb 4-1: Zoran 364xx controlling video device 0
[ 1012.934195] usbcore: registered new interface driver zr364xx
[ 1012.934202] zr364xx: Zoran 364xx
[ 1013.461085] usb 4-1: Failed sending control message, error -110.
[ 1013.461096] usb 4-1: error during open sequence: 5
[ 1059.624330] usb 4-1: USB disconnect, address 5
[ 1059.624461] zr364xx 4-1:1.0: Zoran 364xx webcam unplugged

---

### Post by Methuselah on 2010-01-07
Hmm...a driver is attaching to it and it is recognized as a webcam with the Zoran chipset.
Unfortunately errors seem to be generated.

---

### Post by junglenut on 2010-01-07
I'm stumped. Cant find anything on the net about it. I was worried it was too new to be supported when I bought it. Still gonna keep cracking at it until I get it to work ffs.:D

---

### Post by Methuselah on 2010-01-07
> **junglenut said:**
> I'm stumped. Cant find anything on the net about it. I was worried it was too new to be supported when I bought it. Still gonna keep cracking at it until I get it to work ffs.:D

Also, it might be supported in a subsequent release.
Do a google search for zr364xx and you might find more info.
This is the driver that is attaching to your camera.

---

### Post by no2498 on 2010-03-25
my aiptek dv 5100 uses the same driver
no need to load any thing plug it in i need to set mine to live

open a terminal type,  gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

it should have come on

retry it in cheese and ekiga softphone
if it breaks after a few times in cheese do not get of cheesejust do not open it

find and install wxcam
it opens faster and a better frame rate

---

### Post by djm123 on 2010-04-07
Need help on the MEDIA Center., please e mail me DIRECT at [EMAIL="hybriddave@verizon.net"]hybriddave@verizon.net[/EMAIL]
 
I have mp4 files...I need to know EXACTLY how to get these to DVD R...I think its in the media center...
 
Please reply ASAP to [EMAIL="hybriddave@verizon.net"]hybriddave@verizon.net[/EMAIL]
 
Thank you

---

