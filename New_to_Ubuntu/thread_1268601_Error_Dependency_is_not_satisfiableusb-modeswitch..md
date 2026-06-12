---
title: "Error: Dependency is not satisfiable:usb-modeswitch."
date: 2009-09-17
forum: New to Ubuntu
---

### Post by pirate paul on 2009-09-17
Hi, I have been weeks at this.... I have now got vodafone-mobile-connect on my computer but cannot install it. I downloaded several usb-modeswitches last night. It says I have got the mode switches but what do I do with them.

I am on vodafone pay as you go, I need to top it up, on windows a box came up, I could put in a prepay voucher number, check my balance etc. I have to reinstall window> top up> reinstall Ubuntu, and reinstall cheese and add ons etc.

HOW DO I GET THE VODA BOX TO COME UP SO I CAN FORGET WIMDOWS AND GET ON WITH MY LIFE ?

                                                  Thanx.

---

### Post by Shazaam on 2009-09-17
Does this help?
[http://ubuntuforums.org/showthread.php?t=1031458](http://ubuntuforums.org/showthread.php?t=1031458)

---

### Post by pirate paul on 2009-09-17
The link is Greek to me.... I downloaded VMC, and mode switch, but I cannot figure out how to install them. I tried terminal> sudo apt-get install usb_modeswitch....... command not found...... sudo apt-get install vodafone-mobile-connect> command not found.

How do I install them........ I am not too good with computers, just learning.

                                                                     Thanx.

---

### Post by mapes12 on 2009-09-17
Hi

I have a TomTom SatNav and there doesn't appear to be a Linux alternative to the windows app I need to use to update it etc. This could be the same for your Vodafone app.

Therefore, I installed WINE from Synaptic then loaded the windows .exe installer to have the TomTom app up and running for me on my Ubu box via WINE. 

Here's a HowTo:

[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

---

### Post by Shazaam on 2009-09-17
> **pirate paul said:**
> The link is Greek to me.... I downloaded VMC, and mode switch, but I cannot figure out how to install them. I tried terminal> sudo apt-get install usb_modeswitch....... command not found...... sudo apt-get install vodafone-mobile-connect> command not found.

How do I install them........ I am not too good with computers, just learning.

                                                                     Thanx.
It depends on the file type. If it is an .exe (Windows file) follow mapes12 post. For others you will need to first install build-essential (again through Synaptic or apt-get).
Here is a good page that will help you get started...
[https://help.ubuntu.com/8.10/add-applications/C/install-file.html](https://help.ubuntu.com/8.10/add-applications/C/install-file.html)

---

### Post by thahirkoya on 2010-07-26
hello,
when i enter this command
sudo /usr/sbin/initmodem.sh
it shows usb_modeswitch command not found. But I have installed usb_modeswitch.
when  i type "whereis modeswitch"
The result was
modeswitch:

what will i do?

thanks.

---

