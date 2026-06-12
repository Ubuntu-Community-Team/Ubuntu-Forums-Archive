---
title: "bluetooth on inspiron e1505 to connect with LG phone?"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by mas2265 on 2008-08-30
Hello,

I've never used Bluetooth on my Dell Inspiron e1505 laptop with Ubuntu 8.04 before, but I now have a new phone that allows for it, so I wanted to see if I could connect the two via Bluetooth.

I at least think this computer has the needed hardware, and there is a page for bluetooth in the bios setup. (I don't know for sure though.)

I haven't been able to get past the 'hcitool scan' part.  I get "Device is not available: No such device".

There is a Bluetooth Preferences dialog available under System->Preferences.  I think I have bluez stuff installed that is mentioned elsewhere.

Where might I go from here to see if it'll work and hopefully allow it to work?

Thanks!

---

### Post by Mr Mookie on 2008-09-19
Not a single reply for some help and it's been two weeks. :( Sorry the community has been veering off a bit lately.. 

I've had similar issues with bluetooth..

I found the following link helped alot..

[http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu")

---

### Post by mas2265 on 2008-09-20
Thank you for the post. :)

I was able to find/edit hcid.conf and running 'bluetooth restart' appeared to run without error.  But, when I would tell my phone to try to detect new devices, it couldn't find any, with the phone around the laptop's keyboard.

Ah well...I think I'll try the usb cable for the phone.

---

### Post by fragman on 2008-09-23
try this link  [http://ubuntuforums.org/showthread.php?t=705103&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=705103&highlight=bluetooth)

it did help me.

---

