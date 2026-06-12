---
title: "Absolute Newbie: USB wireless how to??"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Waitati Energy on 2010-09-08
):P
Hi, I've had Ubuntu 10.4 Lucid Lynx since I naively upgraded from the earlier version (that I only had clumsy knowledge of). This has come with problems for me as I've adopted Linux by conviction, not knowledge, skill or interest in IT.
Now I want to get wireless connection to my computer. I bought first one belkin wireless USB adaptor that didn't work on my computer. I returned it for a:
 
Linksys (by Cisco) "compact wireless-G USB adapter",which I was told would be simple to make work. (I thought - plug in and connect! - why not?). But no.
 
Please, how? I'd love something intuitive, i.e. just a CD or file that installs the driver (it doesn't recognise the automatic install, or open the files I try to open individually when I install the CD). I go woozey when I see code, and I don't understand the jargon on the sites that claim to offer a way to do it.
 
I do understand that Ubuntu is for IT specialists and I'll accept this outcome soon.
 
But if there is a simple, straightforward way of making stuff work on my old second hand computer, saved from third world recycling/toxic reuse, using a Ubuntu OS I would love to hear of it, first of all to be able to access the web from my computer!
 
My apologies for being so utterly useless.

---

### Post by Waitati Energy on 2010-09-08
I should add that I did have some wireless capability until recently. The computer came with an old Dynalink Router and external USB wireless adapter. That never really worked - was very intermittant, and we got a Belkin 'Advanced Wireless Router' F6D4230-4 v1 , which, coupled with the external Dynalink wireless adapter, gave us slightly more stable internet connection. All this because we have the computer in another room to the one in which our telephone line is.
Anyway, for some reason it stopped working completely, thus the reason for the purchase of a new (better??!) Compact Wireless - G USB Adapter.

---

### Post by bredman on 2010-09-08
WiFi is one of the most common problems with Linux, but is usually easy to sort out.

First, we need some information...

Open a terminal (press CTRL-ALT-t)

Type in the following command
lsusb

Send us any line that refers to Wireless or WiFi, we especially need the identifier code which looks like 1234:5678

Type in the following command and tell us the result
iwconfig

In case you are wondering, the commands are
1. List the hardware plugged into the USB bus
2. Show the WiFi configuration

---

### Post by Peter09 on 2010-09-08
As bredman has said but also:
 
Have you checked the menu 
 
System->Admin->Hardware 
 
to see if there are any drivers waiting to be enabled, be sure that you have a hardwired link connected because it may do a search for your wireless adaptor drivers. Otherwise, as already indicated, we will need to know the model of the USB device and from there we can advise on how to get good drivers.

---

### Post by zeroseven0183 on 2010-09-08
You can also try to install USB Modeswitch
```
sudo apt-get install usb-modeswitch
```

---

