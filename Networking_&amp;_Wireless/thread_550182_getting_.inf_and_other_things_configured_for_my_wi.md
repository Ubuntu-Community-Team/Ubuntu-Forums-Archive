---
title: "getting .inf and other things configured for my wireless LAN connection"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by mohit052 on 2007-09-13
1.i have a windows driver for a wireless network connection for the internet connection. 
2.I also have the ndiswrapper installed
3.I also have orange installed(to extract cab files)

Now,Please Please some one tell me how to go forword with making my wireless device detected by my system. The device is SUB-362(EXT) by syno. They dont have driveres for linux.

---

### Post by devilmyarse on 2007-09-13
What kind of windows driver do you have?
 
To use NDISWRAPPER you need the .sys and .inf files for the wireless card off your drivers disc. If there are no *.inf files on ur windows driver disk you will need to install the drivers onto a windows operating system then browse to the directory where it has installed the files and then copy the *.inf and the *.sys files in the directory. Usually the .inf files is called the name of the chipset used.
 
for example on a broadcom chipset it is bcrmdis.inf (or something similar).
 
once you have these files you can install the drivers by typing this into a terminal
 
```
sudo ndiswrapper -i 'nameofyourfile.inf'
```
 
You can then check whether or not it is installed by typing this into terminal
 
```
sudo ndiswrapper -l
```
 
This should tell you whether or not the driver has been installed succesfully.
 
(this is all i can suggest at the moment without having any more information)

---

