---
title: "Dell wireless"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by wu-stix on 2008-08-03
Man I have tried everything suggested on these threads and nothing has worked to get wireless working on my laptop.  I looked at the ubuntu help and they say i should see wireless n the network settings but it isn't there.  I have a dell vostro 1500.  I loaded the windows wireless drivers program (ndiswrapper) but the driver at dell is .exe and it needs a .inf (i think) file.  Any help would be very much apreciated.

---

### Post by superprash2003 on 2008-08-04
have you tried this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) ?

---

### Post by Ayuthia on 2008-08-04
> **wu-stix said:**
> Man I have tried everything suggested on these threads and nothing has worked to get wireless working on my laptop.  I looked at the ubuntu help and they say i should see wireless n the network settings but it isn't there.  I have a dell vostro 1500.  I loaded the windows wireless drivers program (ndiswrapper) but the driver at dell is .exe and it needs a .inf (i think) file.  Any help would be very much apreciated.

In order to extract the .exe file, you will either need to unzip the file or install cabextract.  I can't remember how Dell does theirs.  Usually a .exe file just needs cabextract, but I have seen a few from Dell that just needed to be unzipped.

---

### Post by lordhaworth on 2008-08-04
I had loads of trouble at first too with a Dell, im at uni some of the time and my net only worked there when i used the manual connect (or something like that - im not on my ubuntu comp now) and you have to type in all the connection details yourself - after i did that once it worked fine. It has always worked with my internet at home but isnt exactly what id call perfectly reliable

---

### Post by rizitis on 2008-08-04
> **wu-stix said:**
> Man I have tried everything suggested on these threads and nothing has worked to get wireless working on my laptop.  I looked at the ubuntu help and they say i should see wireless n the network settings but it isn't there.  I have a dell vostro 1500.  I loaded the windows wireless drivers program (ndiswrapper) but the driver at dell is .exe and it needs a .inf (i think) file.  Any help would be very much apreciated.


command > lspci
and show us here the results.
after we will try to help you here

or

if you know how to do it and you have the correct file of .exe drivers at your /home just give the command 
> unzip R123456.EXE   (or whatever the name of the download is)

 then you will find the .inf 

or

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

---

### Post by wu-stix on 2008-08-04
> **superprash2003 said:**
> have you tried this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) ?

Thanks, I followed the instructions and got it working in 5 minutes. Awesome.

---

