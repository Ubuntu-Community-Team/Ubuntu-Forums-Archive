---
title: "wusb54gs running ubuntu 8.10"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by zenshadow on 2008-12-01
Im new to unbuntu 8.10 as well as linux . can anyone help me out?  i cant get my linksys wusb54gs ver1 to work with ubuntu 8.10. i read that i should be able to plug it right in and work but thats not the case.

---

### Post by Xriva on 2009-01-10
I did get my Linksys wusb54gs external USB wireless to work. 

USBID = Bus 005 Device 010: ID 13b1:000e Linksys
(Ubuntu Hardy Heron)
Computer = Dell OptiPlex GX280

I installed and used:

    ndiswrapper-utils
    ndisgtk            (ndiswrapper graphical interface)

There are many good "how-to" instructions on the Internet.

Here's one thing I had to do that **wasn't listed anywhere:**

---------------------------------------

I had three driver files:

          rndismp.sys  - hard to see but fist letter is an " r "
          usb8023.sys  
          wusb54gs.inf

Following the instructions:
  1. created an wusb54gs folder in /etc/ndiswrapper
  2. that folder contained a "conf" file created by ndiswrapper, it also
     contained a copy of wusb54gs.inf

**[COLOR="Blue"]But it would not work until I manually copied the two "sys" files into that new folder.[/COLOR]**

---

