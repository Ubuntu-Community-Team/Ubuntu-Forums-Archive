---
title: "for all those been having troubles with wireless connections"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by mxyzptlk on 2005-10-31
I must said in the beggining that i just upgrade to Breezzy (i was hoary)
and the first thing i realized was this:
usb wlan adapter already detected, so i was happy but as in hoary no internet no ping, finger, etc at all.

first thing you all must know (some of you already do) is that regardless of the brand of your wlan device the most important thing is the chip. In my case i have a mmmmm... err......i dont remember the brand all i know is that it has an ATMEL chip inside, like some devices (belkin for instance) do.

why is that important, because you need the properly driver to install your device, and you have to ensure that it has a Linux driver in it 

yes yes i know ndiswrapper is a powerful tool but it doesnt work with all devices.

so once you have the linux driver you need a couple of things to install it.

One: you must install apt binutils in order to have a tool for decompile and compile the kernel of your driver and you have to install make package

two: once you have download it in the right folder (/desktop/driver/ or whatever) in this place you have to execute the command "make"

and sorry for the caps YOU NEED THE LAST VERSION OF WIRELESS_TOOLS FOR YOUR DEVICE. and you have to install it with "make" command.

maybe the order is not the adecuate but thats what i did now i have internet and everything with my usb wlan device and it works fine.

hope it helps

remember WIRELESS_TOOLS for your device, if it has a linux driver and if it is not compile in gcc download binutils and make packages, execute wireless_tools in the folder you unpack it.

after a fresh reboot everything works.

one more thing just in case. if your device is not activated plz do it.



the truth will set you free
mxyzptlk

---

