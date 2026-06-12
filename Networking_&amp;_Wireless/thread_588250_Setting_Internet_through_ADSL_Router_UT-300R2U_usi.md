---
title: "Setting Internet through ADSL Router UT-300R2U using USB port only"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by ajinkyakulkarni87 on 2007-10-23
I am using Ubuntu 7.10.
I am having UTStarcom's UT-300R2U ADSL Router( provided by BSNL Dataone (ISP) in Maharashtra, India.)


This router has 1 ethernet port and 1 USB port. I have connected other computer through ethernet port . So  I want to connect my computer though USB port.

Please tell me how to do this?

CD came with router contains CDCEther.c and CDCEther.h files along with make file but this driver requires linux kernel 2.4. During compilation this drivers gives lots of errors in Ubuntu 7.10.

Is there is any update available to CDCEther ? I think this module is replaced by usbnet module in kernel 2.6??? If so then how to configure?

My modem/router works fine in WindowsXp . Output of ipconfig is
Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.2

---

### Post by Lurkos on 2008-02-16
I have the same problem.
Meanwhile did you find a solution?
Can you send me CDCEther.c and CDCEther.h?
Thanks.

---

