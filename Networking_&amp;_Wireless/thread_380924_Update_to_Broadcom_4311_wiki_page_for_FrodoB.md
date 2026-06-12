---
title: "Update to Broadcom 4311 wiki page for FrodoB"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by EricBuntu on 2007-03-10
Hey,

The wiki page for the 4311 Broadcomm card needs to include using bcm43xx-fwcutter. I'm assuming that the original author had already done that after following another HOWTO and forgot to include it, but after doing a fresh install, I discovered that it IS a necessary step.

For reference see this page's fwcutter section for how to do it, I think it should be included in that wiki page though so it'll get you completely up and running from one source:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by teaker1s on 2007-03-10
bcm43xx-fwcutter- not required as cabextract or unzip used. One of the issues with writing a wiki is there are several ways of performing the same function

---

### Post by EricBuntu on 2007-03-10
No, I'm pretty sure you still need to extract the firmware from the driver as it didn't work until I did that additional step with that guide. You have to use cabextract or unshield to get the driver out of the package, then you have to use fwcutter to get the microcode (that HAS to be loaded to the device for it to function) out of the driver and into a loadable form.

---

### Post by teaker1s on 2007-03-10
As I see it, this uses native kernel driver and  bcm43xx-fwcutter
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
 
Ndiswrapper we extract the driver/firmware from the windows driver
I would request that you pm frodoB and ask for clarification, I would also request you ask frodoB to update the wiki if appropriate.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8
sudo ndiswrapper -i nameofdriver.inf 

```
 your comments and interest  in making the wiki as accurate as possible are welcomed

:popcorn:

---

### Post by EricBuntu on 2007-03-10
Yup, I PM'd him right after the thread post and pointed him to it. Just trying to make sure I'm not crazy, as I followed that guide verbatim, and it didn't work, then I extracted the firmware to the correct directory, uninstalled/reinstalled the driver with ndiswrapper, and voila. I'm just worried that everyone who tried that wiki had already gone down the road of extracting fw first, and so didn't realize that you had to do it for ndiswrapper as well? I'm not absolutely positive I'm right (as I did do some hand waving and gnashing of teeth as is usual for a broadcomm wifi card), but at the end, this is where I ended up. I suppose I could delete the firmware, uninstall the driver, reinstall the driver and see if that works....

---

### Post by teaker1s on 2007-03-10
From prior multiple clean installs I have had no problems, that said it's always best to verify these things. 
Please confirm that you have blacklisted and removed native modules/driver-otherwise fw-cutter will allow kernal to load native driver.
This may give the impression that ndiswrapper is using fwcutter firmware, when its not

your interest and comments are appreciated

Daniel

---

