---
title: "Brother MFC-290C will not print from Hardy"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by PhilOHara on 2009-07-15
Hello I have upgraded from my old brother DCP115c to a MFC-290c today
I am running hardy 64 bit AMD. I thought I had force installed 32 bit arcitecture drivers successfully from Brother solutions centre following there instructions best I could ok but I am still unable to print. Any one able to help out.
Thanks Phil
PS I am not to hot with the linux commands.

---

### Post by cozmicharlie on 2009-07-15
Are you trying to print via a usb connection or via a network?

Did you follow the instructions from here?
[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-290C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-290C)

When you go to Administration>Printing is your new printer listed?

---

### Post by PhilOHara on 2009-07-16
Hi yes using USB and after checking today I had loaded the incorrect LPR driver, so I am printing now.
However I have stumbled again, I loaded the scanner driver BRSCAN3 for 64 bit and the scan key tool as directed but no luck with the scanner.
When i open Xsane image scanner it searches for the device and shows the following error "failed to open device brother3:bus2:dev1 error during device io.
Any suggestions here?
Thansk Phil

---

### Post by plucky on 2009-07-16
> When i open Xsane image scanner it searches for the device and shows the following error "failed to open device brother3:bus2:dev1 error during device io.
Any suggestions here?

Did you apply the instructions given on the Brother website install instructions```
Ubuntu 9.04
    1. Open "/lib/udev/rules.d/50-udev-default.rules" file.
    2. Edit "0664" to "0666" in "libusb device nodes" section.

    Before the edit---------------------------------

    # libusb device nodes
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0664"


    After the edit----------------------------------

    # libusb device nodes
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0666"


    3. Restart the OS.
```


Good Luck

---

### Post by laughzilla on 2009-12-27
hi :)

i just followed the above instructions, and my ubuntu 9.04 box still can not see the device when i'm trying to scan using Xsane. it just tells me there is not any device available.

also, the brother software linux driver page does not have a driver specifically listed for the Brother MFC-290C printer/fax/scanner/copier. and i can not seem to find one at any other site, either. 

does anyone know where i can find the linux driver for this device? 

if it does not exist ... then what is an alternative driver i can use for this device to work properly?

thanks :) 

duffbeer

---

### Post by plucky on 2009-12-27
> i just followed the above instructions, and my ubuntu 9.04 box still can not see the device when i'm trying to scan using Xsane. it just tells me there is not any device available.

Did you install the printer cupswrapper and lpr drivers?

Does the printer work?

Have you installed the scanner driver "brscan3"?

Open a terminal and post output of ```
dpkg  -l  |  grep  Brother
```

> also, the brother software linux driver page does not have a driver specifically listed for the Brother MFC-290C printer/fax/scanner/copier. and i can not seem to find one at any other site, either.

does anyone know where i can find the linux driver for this device? 

Check the page again as I can see the MFC-290C driver for both the printer and scanner. [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Download the .deb files,not the rpm files.

The installation instructions are also available on the website.

Good Luck

---

