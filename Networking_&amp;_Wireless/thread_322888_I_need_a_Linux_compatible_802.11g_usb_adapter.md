---
title: "I need a Linux compatible 802.11g usb adapter"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by gh0st on 2006-12-21
Hi folks,

I am looking to buy a USB wieless adapter but I want to make sure I get something that will work with my Ubuntu box. I am looking for some suggestions on what to get really. Can I just get any Belkin or Netgear one and it will work??

If someone could point me in he right direction I would really appreciate it :) 

Thanks in advance

---

### Post by hal10000 on 2006-12-21
Here's a link on linux compatible wireless cards:
[http://linux-wless.passys.nl/query_alles.php?]("http://linux-wless.passys.nl/query_alles.php?")
Any card with green color is compatible.
Have fun

---

### Post by gh0st on 2006-12-21
Great, I'll check out the list thanks :-)

---

### Post by darrenm on 2006-12-21
D-Link DWL-G122 should be a safe bet looking around the web. Seems to use the Intersil Prism54 chipset which has open-source drivers.

---

### Post by gh0st on 2006-12-21
Thanks for the advice, I've used D-Link routers in the past and never had a problem with them so I've plumped for a D-Link DWL-G122. Only £25 off Amazon as well. Happy days :)

---

### Post by dissident_0 on 2007-01-11
I use DWL-G122 revC1 v3.0 and i am desperate, does not finish working. ](*,)

---

### Post by FLPCGuy on 2007-01-11
> **gh0st said:**
> Thanks for the advice, I've used D-Link routers in the past and never had a problem with them so I've plumped for a D-Link DWL-G122. Only £25 off Amazon as well. Happy days :)

DLink would be my last choice...nothing but trouble.

---

### Post by eng_bloody on 2008-04-16
i have Viewsonic 802.11g USB Adapter >> it doesnt work

it is my first time in  Ubuntu :(

what to do ?

---

### Post by hal10000 on 2008-04-16
If you don't know the chipset of your card then you may try the "lsusb"-command or the "usbview"-Program to find out more about you adaptor.

First try if you have the usbview program:
Do the following:
type ALT-F2 and type in usbview.

If this doen't work, then you need to open a command-line (ALT-F2 and "xterm" - withou quotes).
Into this xterm-window you have to type lsusb (note: this is a lower-case L, not an i).

Post the output of the comand-line here (you can mark it with your mouse and paste it with th middle mouse-button)

---

