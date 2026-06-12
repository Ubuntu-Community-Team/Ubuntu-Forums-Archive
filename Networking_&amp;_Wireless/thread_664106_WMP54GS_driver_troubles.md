---
title: "WMP54GS driver troubles"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by yipeskop on 2008-01-10
I'm Using Ubuntu 7.10 (64-bit) and I'm trying to get my WMP54GS wireless card to work, and I already know how to setup Ndiswrapper, but the problem is where ever I download the driver from I only get a .exe file, no .inf or .sys file. (I even tried ripping it from the cd but no .inf file). does anyone know where I can get the .inf and .sys files from? :confused:

---

### Post by wieman01 on 2008-01-11
Check my Ralink tutorial. The mentioned files are probalby inside the .EXE. .EXEs are generally ZIP archives, so you can unpack it either by executing them through Windows or by means of 'unzip' using Ubuntu.

---

### Post by yipeskop on 2008-01-11
I couldn't extract the file on Windows or Ubuntu, but while I had the file on Ubuntu I noticed the .inf file was there all along it's just Vista is stupid and decided not to show the .inf file...
so thx anyways, I have it working now :)

---

### Post by wieman01 on 2008-01-11
Quick question: Which driver did you have to blacklist?

---

### Post by yipeskop on 2008-01-11
wcm43xx I think, and actually when I tried installing the ndiswrapper with the driver it wouldnt work it installed correctly but wouldnt associate itself with wlan0 only eth1 :( (and I havent looked at your guide yet)

---

### Post by wieman01 on 2008-01-12
> **yipeskop said:**
> wcm43xx I think, and actually when I tried installing the ndiswrapper with the driver it wouldnt work it installed correctly but wouldnt associate itself with wlan0 only eth1 :( (and I havent looked at your guide yet)
"eth1" is perfectly fine. Do you get scan results:
> sudo iwlist scan

---

### Post by yipeskop on 2008-01-12
hmm... i really dont know why but it's magically working now. thx for your help :)

---

