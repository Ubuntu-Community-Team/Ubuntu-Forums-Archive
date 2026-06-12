---
title: "internet from Ubuntu: not working, but...too many variables"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by jaboace on 2008-03-26
This is what I am trying to do:

I salvaged this dell desktop and installed Ubuntu 7 on it. I am trying to connect to the internet via the ethernet port.
Here is how:
-The modem
             it's a Scientific Atlanta from Comcast. The main computer is connected via USB, and I connected the Ubuntu computer via the ethernet port on the modem.

-the ethernet cables
            right now I don't have a cable that's long enough so I joined two cables via a little box which has a port on either side.

-settings
           I manually replicated the IP Config settings on the main machine,including DNS servers, also tried DHCP.
-results
           using Network Tools,  I can see that interface eth0 shows traffic, with packets received, sent and no errors, but trying to ping addresses or connecting to websites yields only failures.

At this point I don't even know if what I am trying to accomplish is physically possible.


](*,)](*,)

---

### Post by dmizer on 2008-03-27
well, start by disconnecting the USB cable.  one connection or the other, but not both.

post the output of ifconfig

---

### Post by superprash2003 on 2008-03-27
also try pinging your modem and see if you are able to ping the modem or not

---

### Post by Ice99 on 2008-03-28
Okay how many ethernet ports does your modem have?
If it only has one, your modem is not a router.
Therefore you can't use it to network 2 computers together.

The modem has both USB and ethernet ports so you can choose either method to plug it into your computer.

---

