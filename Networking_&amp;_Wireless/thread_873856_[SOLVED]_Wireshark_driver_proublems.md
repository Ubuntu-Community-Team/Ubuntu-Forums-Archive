---
title: "[SOLVED] Wireshark driver proublems"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by gary22 on 2008-07-29
Being a newbi to the Linux/ubuntu world I am having trouble getting the Wireshark program to function in a monitor mode. The problem I believe is the madwfi driver is not loaded properly or the program will not recognize it. 
I have the program loaded and working on a Windows desktop and failed on my Linux desktop. 
	I installed a D-Link DWL-650 wireless adapter and it is using the Ubuntu default driver. It functions properly using the Internet. Then I went to the Load Software Packets section and it indicates that I have the Madwfi tools loaded but I can not locate it under the Application or Network sections.
 Would appreciate any help that someone mite have in solving my problem.

Thanks Gary22

---

### Post by Ayuthia on 2008-07-30
> **gary22 said:**
> Being a newbi to the Linux/ubuntu world I am having trouble getting the Wireshark program to function in a monitor mode. The problem I believe is the madwfi driver is not loaded properly or the program will not recognize it. 
I have the program loaded and working on a Windows desktop and failed on my Linux desktop. 
	I installed a D-Link DWL-650 wireless adapter and it is using the Ubuntu default driver. It functions properly using the Internet. Then I went to the Load Software Packets section and it indicates that I have the Madwfi tools loaded but I can not locate it under the Application or Network sections.
 Would appreciate any help that someone mite have in solving my problem.

Thanks Gary22

Have you tried to see if you can access it if you run it from the terminal:
```
gksu wireshark
```
This will run it under admin mode.  That was how I have been able to access my ethernet cards.

---

