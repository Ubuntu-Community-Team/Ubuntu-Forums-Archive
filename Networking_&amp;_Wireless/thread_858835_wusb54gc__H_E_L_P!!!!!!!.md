---
title: "wusb54gc  H E L P!!!!!!!"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by atlamm66 on 2008-07-14
ok i am using windows xp right now and i have just installed ubuntu on this pc as well...
 i really like the os system but as of right now i can only us xp because it has internet.

i have never used ubuntu and i am VERY new at it.but i know windows like the back of my hand.

after installing ubuntu i went in and tried to setup the linksys wireless usb adaptor with the drivers it came with...when i open the linksys folder where the drivers are the exe file is there(this is in the ubuntu os) i click on the exe file and nothing happens.
so i went online and tryde to figure it out by forums ect. but i got REALL REALLY lost....i have no idea what to do. alll i want is to be able to use my wireless usb on ubuntu so i can use ubuntu only and not windows...CAN SOMEONE PLEASE PLEASE PLEASE help me....i need a FRESH F R E S H  step by step way of installing the usb network on ubuntu from a bone cleard ubuntu os. PLEASE HELLLLLPPPP.

---

### Post by chili555 on 2008-07-14
I'll be glad to try to help. First, when you opened the Linksys folder, and all there was was an .exe, that just means there is no supplied Linux/Ubuntu driver. Save the install CD, because we may find some use for it later.

First, let's identify just what we have. Linksys, like many other manufacturers, is imfamous for changing the actual chipset without changing the model number. Please insert the device and open Applications -> Accessories --> Terminal and type in:```
sudo lshw -C network
```After giving your password, it will take a few moments to think and will give us some information about your device. Please also let us see:```
lsusb
```Thanks!

---

