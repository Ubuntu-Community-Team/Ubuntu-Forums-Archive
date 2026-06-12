---
title: "Ubuntu does not detect my Nokia phone"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by SwatKat on 2009-11-25
Hi

The title says it all. How do I make Ubuntu detect my Nokia phone connected through usb?

---

### Post by ukripper on 2009-11-25
> **SwatKat said:**
> Hi

The title says it all. How do I make Ubuntu detect my Nokia phone connected through usb?

post output of lsusb:
```
lsusb
```

---

### Post by 3rdalbum on 2009-11-25
What do you want to do with the phone? Do you want to get data off it, or "tether" it (use it as a modem).

It may also help people here if you mention what model number your phone is.

---

### Post by SwatKat on 2009-11-25
> **ukripper said:**
> post output of lsusb:
```
lsusb
```

swat@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0421:00f0 Nokia Mobile Phones 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
swat@ubuntu:~$

---

### Post by SwatKat on 2009-11-25
> **3rdalbum said:**
> What do you want to do with the phone? Do you want to get data off it, or "tether" it (use it as a modem).

It may also help people here if you mention what model number your phone is.

I want to transfer media from my computer to my phone . Its a Nokia 5220 Xpress Music.

---

### Post by samigina on 2009-11-25
Try with Wammu, search in the Ubuntu Software Center.

Edit: in the wammu documentation says that it works with bluetooth

---

### Post by ukripper on 2009-11-26
Yes you can use wammu it also supports usb connection. I use it with Sony P1i phone to sync contacts and music.

---

### Post by SwatKat on 2009-11-26
Thanks ukripper and samigina :P. But it turns out Ubuntu does detect my phone. Its just that I had selected the usb cable connection type as pc suite which would work fine if I actually had Nokia PC suite in Ubuntu  . So anyway, I just had to change my phone connectivity settings and all is well now.

I do want to use wammu, but have trouble configuring my phone. It takes forever to automatically search for a phone and in guided configuration I'm  asked to enter the device name of usb port. What should I enter here?

---

### Post by samigina on 2009-11-27
Plug your phone again, open a terminal (accessories/terminal) and type "dmesg" without the colons. Paste here the output, there we will see what USB port are receiving your phone.

Another way is simple: Open (without plug your phone) System/Admin/Log files viewer/ then plug your phone and you will see the changes, something like "new usb... atached to".

---

### Post by SwatKat on 2009-11-27
> **samigina said:**
> Plug your phone again, open a terminal (accessories/terminal) and type "dmesg" without the colons. Paste here the output, there we will see what USB port are receiving your phone.

Another way is simple: Open (without plug your phone) System/Admin/Log files viewer/ then plug your phone and you will see the changes, something like "new usb... atached to".

Okay, here are the changes after plugging my phone.

```
Nov 27 21:07:42 ubuntu kernel: [  658.854391] scsi 5:0:0:0: Direct-Access     Nokia    Nokia 5220 Xpres 0000 PQ: 0 ANSI: 4
Nov 27 21:07:42 ubuntu kernel: [  658.854780] sd 5:0:0:0: Attached scsi generic sg2 type 0
Nov 27 21:07:42 ubuntu kernel: [  658.871370] sd 5:0:0:0: [sdb] Adjusting the sector count from its reported value: 1950721
Nov 27 21:07:42 ubuntu kernel: [  658.871379] sd 5:0:0:0: [sdb] 1950720 512-byte logical blocks: (998 MB/952 MiB)
Nov 27 21:07:42 ubuntu kernel: [  658.874361] sd 5:0:0:0: [sdb] Write Protect is off
Nov 27 21:07:42 ubuntu kernel: [  658.886369] sd 5:0:0:0: [sdb] Adjusting the sector count from its reported value: 1950721
Nov 27 21:07:43 ubuntu kernel: [  658.889366]  sdb:
Nov 27 21:07:43 ubuntu kernel: [  659.070543] sd 5:0:0:0: [sdb] Adjusting the sector count from its reported value: 1950721
Nov 27 21:07:43 ubuntu kernel: [  659.073353] sd 5:0:0:0: [sdb] Attached SCSI removable disk

```
 I cant figure the device name :-|. I tried (ahem) scsi 5:0:0:0 and sd 5:0:0:0. But I'm told that such a device does not exist.

---

### Post by samigina on 2009-11-27
mmhhh it looks like Ubuntu takes your phone like a external drive, not really like a phone, if you open you "computer" theres no new devices? must be there your phone memory...

Can you try with the Bluetooth connection?

---

### Post by SwatKat on 2009-11-27
> **samigina said:**
> mmhhh it looks like Ubuntu takes your phone like a external drive, not really like a phone, if you open you "computer" theres no new devices? must be there your phone memory...

Can you try with the Bluetooth connection?
Yes, It does mount my phone's memory card as a filesystem. I can access the memory card to transfer stuff from my pc to phone and thats about it. I cant install apps to my phone or sync calender n stuff. Its a bummer. Unfortunately, its an ancient PC and I dont have a bluetooth adapter handy. But I appreciate the help, thanks:P.

---

### Post by kkady32 on 2009-12-17
try
  $hcitool scan 
for me is
   34:7E:39:2A:4C:01	Nokia 2330c-2

so i findet the port = 34:7E:39:2A:4C:01 that is usually to set bluetooth connection

another useful commands are:
 $gammu identify 
 $gnokii --identify

---

### Post by serban on 2012-01-25
> **SwatKat said:**
> Thanks ukripper and samigina :P. But it turns out Ubuntu does detect my phone. Its just that I had selected the usb cable connection type as pc suite which would work fine if I actually had Nokia PC suite in Ubuntu  . So anyway, I just had to change my phone connectivity settings and all is well now.



SwatKat, I spent more than a month to figure out why Ubuntu does not recognize my N8 (so I can transfer photos manually). I gave up some 3-4 times, lost hope, blamed Ubuntu, etc. I AM AN IDIOT!!! You are right, the USB setup in the phone was the problem. Thank you!!!

---

