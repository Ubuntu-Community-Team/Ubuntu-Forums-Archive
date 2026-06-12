---
title: "Just installed 10.10 - ATI driver issues"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by ThisisRuge on 2011-05-07
Hi folks,

I just installed Ubuntu 10.10 and it runs pretty smooth so far - albeit at a native resolution of 1280x960 when I have a 1920x1080 monitor.

I've been trying to install the drivers for my ATi Radeon HD6850 card. I've tried two methods:

- Manual download from ATI and installation via terminal using the following command

```
sh ./ati-driver-installer-11-4-x86.x86_64.run
```And receive this error:

```
Created directory fglrx-install.tDCyJd
Verifying archive integrity...Error in MD5 checksums: 8cc60cd93c2557bfa745e403bed1dc0d is different from 7bb24aafba55dffa58e85afc7f7012a8

```

I then tried using the Additional Drivers tool and received this error about 1/2 way through download and installation:

```
SystemError: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.7.0-0ubuntu4.3_amd64.deb Hash Sum mismatch
```

My concern is that I am not sure how else to get these drivers. Furthermore, as someone very new to Ubuntu will I be experiencing these types of difficulties with later installs of software and/or hardware? My background is all Windows so please excuse the noobness of this question but my background is one where I can download a driver, double click it and install it....

Any help would be greatly appreciated :)

---

### Post by synapsys on 2011-05-07
I found this installation guide that says you need to build a .deb first and then install it. Here's the link:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by rx007 on 2011-05-07
I found you have similar problem from here. maybe this might help :)

[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

this is originally from this thread.

[http://ubuntuforums.org/showthread.php?t=756864](http://ubuntuforums.org/showthread.php?t=756864)

---

### Post by ThisisRuge on 2011-05-07
Thanks for the replies guys.

I seem to have this recurring problem whenever I download stuff from terminal:

```
Hash Sum mismatch
```I know I stated this earlier but I got this doing the first step from [synapsys]("http://ubuntuforums.org/member.php?u=850688")'s link. I really hope that some time i can actually install these drivers. Seem to be hitting a road block each time I do it :(

Would it be easier for me to just move to Ubuntu 11?

---

### Post by chromatica86 on 2011-05-08
Just download your driver from here.
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)
Right click, properties, permissions, tick the "allow executing file as program" box then close.
Now open it. Select run, and you should be good to go from there.

I just installed the driver for my 3870 this way on 10.10 64bit.

---

### Post by ThisisRuge on 2011-05-08
> **chromatica86 said:**
> Just download your driver from here.
[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)
Right click, properties, permissions, tick the "allow executing file as program" box then close.
Now open it. Select run, and you should be good to go from there.

I just installed the driver for my 3870 this way on 10.10 64bit.

Everytime i run the file it creates folders (eg. "fglrx-install.fUqZSc") and does nothing... :(

---

### Post by FlameReaper on 2011-05-08
Try running it from the terminal and copy the messages that appear.

---

### Post by alphacrucis2 on 2011-05-08
> **ThisisRuge said:**
> Everytime i run the file it creates folders (eg. "fglrx-install.fUqZSc") and does nothing... :(


Follow this link:

[ATI binary driver HOWTO.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") 


Use the buildpkg method so that the package management system knows you have fglrx installed. I would also make sure you have purged any old fglrx before starting. ie sudo apt-get remove --purge fglrx* before installing via the buildpkg method.

---

