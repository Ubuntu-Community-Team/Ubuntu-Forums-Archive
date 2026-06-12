---
title: "Brother printer driver"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by I8NY on 2010-04-08
Okay i have a network brother printer mfc5860cn and i need a driver for it.  Ubuntu 32bit(different pc) works with the printer using the "brother-cups-wrapper-bh7" package.  I tried it on my 64bit Ubuntu pc and it worked before but doesn't work any more even after reinstall.  There is no 64bit driver from brother but the *[COLOR=Blue][source code]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/ink3_GPL_src_101-1.tar.gz&lang=English_gpl")[/COLOR]* is available to compile.  I tried to compile it but there is no make or configure file. So how do i compile the driver for 64bit ubuntu?

---

### Post by SkyNet2029 on 2010-04-08
Ok. So i downloaded that file (source) and extracted it.
Ended up with a whole bunch of folders for each printer driver available.
Inside of each folder is a script that needs to be run like this:

```
$sh ./SCRIPT
```

which will install the driver from the folder you have selected as matching your hardware.

Hope this helps.

---

### Post by I8NY on 2010-04-08
okay got it to run and i checked the printer properties and the device url is "usb:/dev/usb/lp0" not the network and won't print anything.

---

### Post by SkyNet2029 on 2010-04-08
Glad to hear you got it working. As for the rest of the configuration, perhaps the wiki page can help you out more. 

[https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

which has a link (number 4 on right hand column) that lists the proper device URL for
brother printer models.

---

### Post by I8NY on 2010-04-08
okay i set it up to use it over the network by adding another printer through LPD/LPR option and that didn't work.  I tried using it on a USB cable and that got the printer to wait for data but not print.

---

### Post by I8NY on 2010-10-09
fixed it. installed the 32bit version after forcing it to, then had to change the destination to "lpd://192.168.3.110/BINARY_P1" because it was looking for it on the USB ports.

---

