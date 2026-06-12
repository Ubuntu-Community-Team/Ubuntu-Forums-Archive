---
title: "Problem with Reliance Netconnect LG LXU-800 USB Modem"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by raju50 on 2010-09-21
This is with reference to [http://ubuntuforums.org/showthread.php?t=1224347](http://ubuntuforums.org/showthread.php?t=1224347)

I have my reliance netconnect working perfectly fine. But everytime I restart I need to run a terminal to type sudo -s, password and then modprobe usbserial vendor=0xeab product=0x9357 and then it gets automatically connected. 

I can't understand following section of the page mentioned above:
Built in modules can have module params passed on the kernel command line: can you try booting with:

usbserial.vendor=**0x0eab** usbserial.product=**0x9357**

You will need to press ESC during to grub pause upon restart/power on.
Arrow down to the kernel you wish to boot.
press "e" (for edit)
Arrow down to the 2nd line (the command line)
Press Enter to begin editing
Arrow to the end of the line and add:
usbserial.vendor=**0x0eab** usbserial.product=**0x9357**
When done press enter. Then press "b" to boot" 			 		

You have to '**extend**' the line with all parameters ending to '...quiet splash'
and make it '...quiet splash usbserial.vendor=0x0eab usbserial.product=0x9357'



I couldn't get how to do it. Please explain in simple steps. I have dell vostro 1510 and ubuntu 10.04(as the only OS). Thanks in advance.

---

