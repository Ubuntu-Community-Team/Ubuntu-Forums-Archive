---
title: "Need gnome-ppp driver for usb acm0 modem"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by jkohler2 on 2008-10-07
I have a Zoom usb modem model 3095, using ubuntu 8.04 on my Acer 5315 laptop.  Gnome-ppp can address the following /dev/modem, /dev/ttyS0 through S3, but no /dev/acm0 to connect to my usb modem.

Not knowing the modem is there, gnome-ppp has no way to connect to the modem, get the phone off-hook, dial, or handshake.  

I am commandline challenged.  Is there any Ubuntu update that I can find with the Update Manager, to get it working?

Thanks,

John

---

### Post by cariboo on 2008-10-08
You seem to be able to type :) so you aren't command line challenged. Open up a terminal and type:

```
lsusb
```

and post the output in your next post. The above command will tell us whether your modem is detected.

Jim

---

### Post by jkohler2 on 2008-10-09
> **jkohler2 said:**
> I have a Zoom usb modem model 3095, using ubuntu 8.04 on my Acer 5315 laptop.  Gnome-ppp can address the following /dev/modem, /dev/ttyS0 through S3, but no /dev/acm0 to connect to my usb modem.

Not knowing the modem is there, gnome-ppp has no way to connect to the modem, get the phone off-hook, dial, or handshake.  

I am commandline challenged.  Is there any Ubuntu update that I can find with the Update Manager, to get it working?

Thanks,

John
Hi Jim,
Thanks for the message.   I typed the command you gave me, and got this:

john@john-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0803:3095 Zoom Telephonics, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-laptop:~$ 

Does that mean gnome-ppp knows there is a modem on bus 5 device 3?  What does that mean?

John

---

### Post by jkohler2 on 2008-10-26
> **jkohler2 said:**
> Hi Jim,
Thanks for the message.   I typed the command you gave me, and got this:

john@john-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0803:3095 Zoom Telephonics, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-laptop:~$ 

Does that mean gnome-ppp knows there is a modem on bus 5 device 3?  What does that mean?

John
I found a modem driver for this particular usb modem, the Zoom 3095 will work from Gnome-ppp after the driver is downloaded from linuxant, uncompressed and installed in Ubuntu 8.04 with a debian command dpkg....
dgcmodem_1.08_k2.6.24_21_generic_ubuntu_i386.deb.zip 

After downloading into the terminal window, and decompressing, it has to be copied to a file called /tmp, and then it can be installed with the "dpkg."

A little confusing to me, but doable.

John

---

