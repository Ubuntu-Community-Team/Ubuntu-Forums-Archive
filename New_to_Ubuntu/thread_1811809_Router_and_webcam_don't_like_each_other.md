---
title: "Router and webcam don't like each other"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Bob1975 on 2011-07-25
Hello, I hope somebody will be able to help me.

I have a Belkin Wireless G Plus MIMO USB router and want to use a webcam. When I plug in the webcam (I've tried 2; a Logitech C270 and a Technika cheapy job from Tesco, both do the same thing) the computer disconnects from the internet and won't reconnect; bit of an issue as I want the webcam for Skype! Even  allowing for that, I can't get the webcam to work anyway. There's  obviously a conflict between the two, but I haven't got the first clue  on how to resolve it.

Any help much appreciated.

---

### Post by frankbooth on 2011-07-25
Are you 100% sure it's the router? Have you tried without it?

A router shouldn't be able to detect whether you have a webcam or not. Maybe it's a problem with the USB port?

---

### Post by Bob1975 on 2011-07-25
Thank you for your response.

In all truth, I'm not knowledgeable enough to know what it is! I can only describe the symptom, which is that the computer looses it's connection to the internet.

I have tried both the webcams in USB ports both on the front and back of the computer with the same thing happening each time.

Is there any way to check if the USB ports are the root of the problem?

---

### Post by ubudog on 2011-07-25
Not sure about your original question, but to find out if the USB port is a problem, just try plugging it in to another.  

Also, while the webcam is plugged in, post the output of:
```
lsusb
```
Run that command in a terminal.  (Applications>Accessories>Terminal)

---

### Post by amjjawad on 2011-07-25
> **Bob1975 said:**
> Hello, I hope somebody will be able to help me.

I have a Belkin Wireless G Plus MIMO USB router and want to use a webcam. When I plug in the webcam (I've tried 2; a Logitech C270 and a Technika cheapy job from Tesco, both do the same thing) the computer disconnects from the internet and won't reconnect; bit of an issue as I want the webcam for Skype! Even  allowing for that, I can't get the webcam to work anyway. There's  obviously a conflict between the two, but I haven't got the first clue  on how to resolve it.

Any help much appreciated.

Are you connected to the router via USB port?
If yes, when you unplug it and plug the Camera, what will happen?

+1 for 
```
lsusb

```

---

### Post by Bob1975 on 2011-07-25
Ok. Tried several things. First here's what I get from the lsusb

  	 	 	 	p { margin-bottom: 0.21cm; }  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 005: ID 046d:0825 Logitech, Inc.  
 Bus 001 Device 003: ID 050d:905c Belkin Components Wireless G Plus MIMO Network Adapter  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 



I've then tried these below: -



1) Tried both cameras in several USB ports both on the front and back of the computer. This resulted in the internet connection being dropped each time and required a reboot.


2) Rebooting leaving the camera connected in a USB port. The computer boots fine but will not connect to the internet.


3) Delete original VPN connection entry and re-enter details. Will not connect until computer is rebooted, without the camera plugged in


I'll get back in a bit about leaving the camera plugged in and the router out. Forgive the delay it's taking quite a few re-boots and my dogs are giving me the "take me for a walk or I'll chew something expensive" look!

---

### Post by amjjawad on 2011-07-25
> **Bob1975 said:**
> my dogs are giving me the "take me for a walk or I'll chew something expensive" look!

Take your dog for a walk. Don't worry, we'll be here :)

I don't see anything wrong in the output of "lsusb" unless someone else has a better idea?!

What release of Ubuntu are you using?

To find out if you are in doubt:

```
cat /etc/issue

```

What's the version of your Kernel?

```
uname -a

```

---

### Post by Bob1975 on 2011-07-25
Started computer with the router disconnected and the webcam it works. I checked just by starting Skype and using the "Test" window in the Options. Sure enough there was my mug gurning back at me. Still won't connect to the web with both connected though.

As previously, I've tried this with both webcams and in several USB ports, finding the same result.

---

### Post by Bob1975 on 2011-07-25
Ubuntu 10.04.1 LTS \n \l

and...

Linux Home 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

Does that help?

---

### Post by ubudog on 2011-07-25
Are you plugged in to the router via USB?  If so, do you HAVE to use USB?  Can you try with Ethernet?

---

### Post by Bob1975 on 2011-07-26
Hmmm I may have been using the wrong terminology, should I have said wireless usb network adapter rather than router?

Either way, yes, the wireless wotsit is plugged in on a usb. I'm fast considering ditching it and running a cable. Cables work, I like cables!

---

### Post by androssofer on 2011-07-26
> **Bob1975 said:**
> Hmmm I may have been using the wrong terminology, should I have said wireless usb network adapter rather than router?

Either way, yes, the wireless wotsit is plugged in on a usb. I'm fast considering ditching it and running a cable. Cables work, I like cables!

+1 for cables... haha.

try putting wireless and webcam in usbs at the back(1s at the back tend to be built into the motherboard). have u been moving the wireless aswell as the webcams during ur re-shuffles? or just webcam(s)?

guess 2: plug in cable. update. hope updates fix sumthing...

---

### Post by 3rdalbum on 2011-07-26
My guess would be that your computer isn't putting through enough power to run both devices at the same time. If you can beg, borrow or scrounge a self-powered (NOT bus-powered) USB hub and plug one or both of the devices into it, this should either confirm or deny my theory. The self-powered USB hub shouldn't have any trouble powering a webcam and a wifi adapter.

Running a cable is still a good idea - less susceptible to attack or bad signal conditions. You're also less likely to run into driver problems.

---

### Post by amjjawad on 2011-07-26
> **3rdalbum said:**
> My guess would be that your computer isn't putting through enough power to run both devices at the same time. If you can beg, borrow or scrounge a self-powered (NOT bus-powered) USB hub and plug one or both of the devices into it, this should either confirm or deny my theory. The self-powered USB hub shouldn't have any trouble powering a webcam and a wifi adapter.


At some point I agree with this. However, I'm not sure if that's the case with you. Why don't you try that if it's possible or ...

> Running a cable is still a good idea - less susceptible to attack or bad signal conditions. You're also less likely to run into driver problems.

---

### Post by amjjawad on 2011-07-26
> **Bob1975 said:**
> Hmmm I may have been using the wrong terminology, should I have said **wireless usb network adapter** rather than router?


Yes!

---

### Post by Bob1975 on 2011-07-26
> **3rdalbum said:**
> My guess would be that your computer isn't putting through enough power to run both devices at the same time. If you can beg, borrow or scrounge a self-powered (NOT bus-powered) USB hub and plug one or both of the devices into it, this should either confirm or deny my theory. The self-powered USB hub shouldn't have any trouble powering a webcam and a wifi adapter.

Running a cable is still a good idea - less susceptible to attack or bad signal conditions. You're also less likely to run into driver problems.

I'm quite happy to go with your diagnosis, as I don't know anyone with a self-powered USB hub. Time to "borrow" some cable from work!

Many thanks to all who've offered their assistance and knowledge to this inept but happy eedjit!

---

### Post by amjjawad on 2011-07-26
You welcome anytime ;)

Just keep us posted and if you need anything, let us know :)

---

### Post by ubudog on 2011-07-26
Good luck!  Let us know if you have any more questions.  :-)

---

