---
title: "Wvstreams is not installing."
date: 2009-06-21
forum: New to Ubuntu
---

### Post by StupendousMan on 2009-06-21
Hello all. I could use your help, please. I recently upgraded from Gutsy to Jaunty. When I try to install Wvstreams I keep getting an error message saying 'C++ Preprocessor failed sanity test'. I have tried to install vers. 4.2, 4.4.1 and 4.6 which all give me the same error message. How do I go about correcting this? Your help is appreciated. :)  Thanks!

---

### Post by polopete on 2009-06-22
ya i have the same problem, i have been trying to install my T-Mobile E160 mobile broadband modem, which at work with a live LAN connection and the same O/s (Kubuntu 9.04 AMD64), i can get working, but needed to update my system and install a few other dependencies, but at home, switching between windows :S and kubuntu daul boot, i have downloaded Debian and source packages and tryed both ways but i just cant get WVDail to install coz wvstream is missing, and when i tryed installing both .deb and tar.gz files i get error message as guy above me does,  wot i was wondering is....

would i need to do a full update before i can proceed with install these other things i need???

________________________________________________________________________

Intel core2duo E4500 @2.65, 4GB OCZ gold plated DDR2, Nvidia 9500gt 1gb, 320GB sata2, Huawei E160 Modem

---

### Post by GeorgeVita on 2009-06-22
Hi,
if your modem cannot be used with Network Manager and you need **wvdial** you may use System > Administration > Synaptic Package Manager to get it.
If you do not have an internet connection try:
**[http://ubuntuforums.org/showpost.php?p=7465501&postcount=3](http://ubuntuforums.org/showpost.php?p=7465501&postcount=3)**

Check the links! They are for i386/32bit

Regards,
George

---

### Post by polopete on 2009-06-23
thanks for the help [GeorgeVita]("http://ubuntuforums.org/member.php?u=638001"), i did as u said in your post and tryed installing the debian files in order(64bit versions btw), the 1st two where fine but the 3 others just wouldn't install.

i now have my modem working with the help of libusb-dev, usb_modeswitch and wvdial, in the end i took my pc to work and sudo apt-get mosta it, but thanks for the help.

---

