---
title: "dell truemobile 1180 wireless usb adapter"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by xizillia on 2008-10-05
Hi 
I am relativley new to linux and i would like to get my Dell truemobile 1180 wireless usb adapter to work so i can get on the internet without being right next to the router. I downloaded the driver and change the file extension to .inf instead of the .exe and it didnt work when i tried to instyall in in the wireless network drivers app. is there anyway i can get this to work and i would like as much info as possible as I am new to linux. 
Thank You

---

### Post by nixscripter on 2008-10-06
You will have to actually run the EXE installer on a Windows machine (or give [_Wine_]("http://www.winehq.org/") a try -- it's in the Ubuntu package manager). The INF and SYS should be installed, and those are the two files you need for ndiswrapper.

---

### Post by Ayuthia on 2008-10-06
The file does need to be the .exe.  If it is from Dell, there is a good chance that you can just unzip the file.  However, what nixscripter said should work too.

---

### Post by xizillia on 2008-10-06
thank you guys soo much i will give them a try

---

### Post by opt1k on 2009-11-20
after you plug in your card from the terminal run this

$ sudo modprobe prism2_usb prism2_doreset=1

it works after that

---

