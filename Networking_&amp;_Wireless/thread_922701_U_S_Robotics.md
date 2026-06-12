---
title: "U S Robotics"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by alaali on 2008-09-17
HI every body

I'm new ubuntu user and i have proplem with using wireless network :confused:

i use external wireless connection called U.S.Robotics but when i plug it in the USB port i got nothing.:(

so my friend toled me to post in the ubuntu form :)


THANKS
ALI AL AALI

---

### Post by DFlame on 2008-09-17
Lets have a closer look at this device. Plug it into the computer, then open Terminal.

In Terminal, use the command ```
lsusb
``` and please post the output :)

DFlame

---

### Post by alaali on 2008-09-18
thanks MR.Dflame for the fast response :)

the list of the USB port is 
Bus 004 Device 006: ID 0baf:011b U.S. Robotics 

thanks agine :) :)

Alaali

---

### Post by DFlame on 2008-09-18
After a bit of digging, it seems that you will need to use ndiswrapper to configure the device in question. I'd link you directly to the drivers you need but their site is currently down. However, you can read up on the process on the Ubuntu Docs:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

There are also a few stickies in this forum that may help you.

Dflame

---

