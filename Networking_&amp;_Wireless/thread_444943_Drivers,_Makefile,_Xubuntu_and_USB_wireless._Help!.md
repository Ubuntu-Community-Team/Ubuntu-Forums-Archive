---
title: "Drivers, Makefile, Xubuntu and USB wireless. Help!"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by StageCraft on 2007-05-15
I just started "using" Xubuntu. However I have yet to be able to connect to the internet. I have a bw-54u11 usb wireless and I have a driver for it I think because there is a Linux folder on the install CD but I don't know how to install the driver.

The instructions say to "make clean" "make" and "make install" and I'm fairly sure that these are Terminal commands. I have tried to open the terminal but all it seems to do is restart the whole operating system and I have no idea why that is. Anytime I try to open the makefile itself all it does is open it in mousepad so thats no help.

I know there are quite a lot of problems and questions here but if anyone can help me out that would be great. I don't want to have to keep going back to windows any time I have to do anything and from all sources the Ubuntu community is said to be the most helpful so I know you'll come though

Thanks

---

### Post by x64Jimbo on 2007-05-15
If there's one thing I can almost guarantee, it's that the Linux drivers on the CD will be incompatible or at the very least really, really out of date. 
Your best bet is probably going to be running the windows driver in ndiswrapper. They tend to update their windows drivers much more frequently, and you are much more likely to be able to get advanced features like WPA2 support working.

---

### Post by StageCraft on 2007-05-15
ndiswrapper, so I have heard, can be installed off the CD. Would I then be able to use the .exe of the driver or would I have to find it on my windows partition?

---

### Post by StageCraft on 2007-05-16
I have done it. I cant get on my own WPA protected network but I can get on my neighbours wireless so it all works fine

---

### Post by x64Jimbo on 2007-05-16
> **StageCraft said:**
> I have done it. I cant get on my own WPA protected network but I can get on my neighbours wireless so it all works fine
Weird. Only thing I can really think is that your own WiFi might be WPA2 and the device might only support WPA-PSK, which is actually pretty common. You may want to check your router's settings.

---

