---
title: "How to apply ndiswrapper"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by lakelovers on 2008-03-22
I read a lot of the Dell wireless 1350 posts. I gather that using the ndiswrapper is the way to go, but I have found no info on how to apply it. I googled the problem and found one reference that says the Windows driver has to be installed first then the "wrapper." The google reference says to install the driver in the Ubuntu partition. Ubuntu will not accept the 1350 Windows driver, unless I just don't how to do it. I'll appreciate any help you can provide. I need very simple directions.

---

### Post by dstew on 2008-03-22
Do you currently have internet access, using a wired connection?

---

### Post by kevdog on 2008-03-22
Perhaps this wiki page may help -- Im assuming you are referring to a broadcom chipset (which I may be wrong):
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by lakelovers on 2008-03-23
I do not have internet access on the laptop. I'm posting this through my desktop. I might be able to connect directly through the DSL box. Not sure. I looked at the WifiDocs and it appears that I have to have an internet connection to download the extraction program in to the lap top to get things going. It's all very complicated for my non-tech brain. Is there a mini wireless for laptops that works out-of-the-box for Ubuntu. It's probably easier for me to buy compatible unit.

---

### Post by mrsudo on 2008-03-23
find the appropriate .inf file from your windows partition or from the install cd.  
install ndiswrapper using either the livecd which should have it, or a seperate .deb file.
install ndiswrapper
$ sudo ndiswrapper -i /path/to/file/.inf
$ sudo modprobe ndiswrapper

---

### Post by dstew on 2008-03-23
If you can get wired access by plugging into your router it will be much easier to set up your wireless.

---

