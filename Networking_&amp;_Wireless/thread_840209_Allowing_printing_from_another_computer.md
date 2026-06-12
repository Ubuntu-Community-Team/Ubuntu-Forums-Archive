---
title: "Allowing printing from another computer"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by Jamface on 2008-06-25
At last my Heron is up and running.  But I now can't print from the laptop which is client to this PC host.  My printer is listed on CUPS and is published, but I can't see how to set up printer sharing.

---

### Post by superprash2003 on 2008-06-25
which OS does your laptop run?

---

### Post by Jamface on 2008-06-25
Windows XP with SP2

---

### Post by superprash2003 on 2008-06-25
are you doing this through samba?please read [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by Jamface on 2008-06-25
My Ubuntu is using CUPs.  I have tried some of the tests you mention in your blogspot but I'm not sure how to test that the communication with the laptop is working.  The laptop network settings give the Ethernet adaptor local area connection IP Address as 192.168.1.3.  Is the address of the laptop?  When I include this address in the ping test it pongs successfully.

---

### Post by Jamface on 2008-06-25
When I open the window 'Connect to 802.1X Protected Wired Network the boxes are largely empty.  Does this mean that my connection to my laptop has not been set up?

---

### Post by plewisfdx on 2008-06-25
Set this up through System->Administration->Printing then on the left click "Server Settings" and check the box that says "Share published printers connected to this system"

Open a terminal on the server and type ifconfig.  Look for 192.168.1.x (2, 4, or something) and then on the laptop, try to browse the lan for printers.  If the browsing fails, type in the ip address found from ifconfig then a slash and the printer name.

on windows:  \\192.168.1.2\printername

---

### Post by superprash2003 on 2008-06-25
first try what the above poster says..
  i hope you are doing this through samba

---

### Post by Jamface on 2008-06-26
Many thanks, plewisfdx.  That seemed to do the trick although the Windows wizard said it could not find the printer driver on the server and asked me to install the driver from the web.  I don't think I quite understand all this as the Ubuntu machine must have or have access to a driver.  Does it mean that Windows has set up a driver on the host somehow rather than telling the host to use the driver it already has?

---

### Post by plewisfdx on 2008-06-26
> **Jamface said:**
> .. although the Windows wizard said it could not find the printer driver on the server and asked me to install the driver from the web.  I don't think I quite understand all this as the Ubuntu machine must have or have access to a driver.  Does it mean that Windows has set up a driver on the host somehow rather than telling the host to use the driver it already has?

This is true even in a totally windows environment.  The driver may be shared in a winxp -> winxp situation (I'm not sure), but if you have a vista computer accessing a winxp shared printer each computer must have the driver for that OS installed.  Ubuntu works the same.

So I think how this works is winxp computer says "print this" and uses its driver to send the correct commands to the ubuntu computer which takes that command (probably samba protocol, in this example) and translates it using its driver to send to the attached printer to print.  

Glad you got it working.

---

