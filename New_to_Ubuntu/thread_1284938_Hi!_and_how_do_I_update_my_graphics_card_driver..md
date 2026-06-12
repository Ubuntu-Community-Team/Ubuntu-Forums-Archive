---
title: "Hi! and how do I update my graphics card driver."
date: 2009-10-07
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-07
Hello Folks!

For the first time today I have downloaded and installed UBUNTU. It all went like a dream and I am so pleased.:)

My computer, which is a reasonable spec, struggles with some of the more intensive screensavers. Is it possible to download a driver for my ATI card?:confused:

I look forward to your replies!

---

### Post by Zimmer on 2009-10-07
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
The Ubuntu documentation is your friend.... and starting off point.

If you run into issues then the forum is the place to search for more help...

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Flimm on 2009-10-07
Click System, Administration, Hardware Drivers, and see if Ubuntu offers any alternative or proprietary drivers.

---

### Post by fixerman on 2009-10-07
> **Flimm said:**
> Click System, Administration, Hardware Drivers, and see if Ubuntu offers any alternative or proprietary drivers.

It says..." No proprietary drivers are in use on this system". As I am a complete novice as far as UBUNTU is concerned I find the prospect of updating the graphics card driver daunting. Also I am not exactly a youngster so a bit slow on the uptake these days. So any help will be greatly appreciated.:confused:

---

### Post by seamushc on 2009-10-07
What is your graphics cards model?

---

### Post by halitech on 2009-10-07
the driver can be found here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

if you don't know what model you have, open a terminal and run```
lspci
```and post the results back here

---

### Post by fixerman on 2009-10-07
> **seamushc said:**
> What is your graphics cards model?

It comes out as RV350 (Radeon 9550).

---

### Post by halitech on 2009-10-07
> **fixerman said:**
> It comes out as RV350 (Radeon 9550).

forget about the driver from ATI then, it won't work in 9.04. Check here for info on getting the Open Source driver working

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

