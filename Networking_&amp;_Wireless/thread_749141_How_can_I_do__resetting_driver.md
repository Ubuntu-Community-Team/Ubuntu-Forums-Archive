---
title: "How can I do  resetting driver?"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by kjman83 on 2008-04-08
The problem is I think I set up to ndiswrapper with another driver..
I did with sp34152.exe This one..
But My laptop's driver is sp37950.exe so I downloaded it.
 I did again sudo ndiswrapper -i bcmwl5.inf
 I can see that bcmwl5.inf is already installed(?) like this..
I want to know How can I remove the bcmwl5.inf(sp34152.exe version)from ndiswrapper, and do resetting bcmwl5.inf(sp37950 ver.)
 Please give an answer

---

### Post by dstew on 2008-04-08
You first have to extract the driver files from the .exe archive. Install the cabextract program, and run```
cabextract sp37950.exe
```That should get you a folder with the .inf and .sys files in it that ndiswrapper needs.

To remove the bcmwl5 driver from ndiswrapper, you first have to remove ndiswrapper itself from the kernel```
sudo modprobe -r ndiswrapper
```Then, remove the driver from ndiswrapper```
sudo ndiswrapper -r bcmwl5
```Note the command uses the driver name without the .inf extension.

To install the new driver, navigate to the folder that contains the new .inf and .sys files, and do```
sudo ndiswrapper -i sp34152.inf
```if that is the correct name of the .inf file that you got out of the .exe archive with cabextract. Check to see that it installed with```
ndiswrapper -l
```It the driver is installed into ndiswrapper, go ahead and install ndiswrapper into the kernel:```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

