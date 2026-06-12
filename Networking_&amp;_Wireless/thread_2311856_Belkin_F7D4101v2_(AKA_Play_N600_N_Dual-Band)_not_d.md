---
title: "Belkin F7D4101v2 (AKA Play N600 N Dual-Band) not detected"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by celticwiseman2 on 2016-01-30
Hello,

I'm having trouble getting my wireless adapter working. I've read the stickies and attached is the output from the wireless-info.txt file. The adapter is not listed. Ethernet is fine.

[ATTACH]267034[/ATTACH]

I've tried -


[LIST]
[*]Downloading the driver from the official site, extracting the files from the .exe using Wine and then trying the NDISwrapper. Driver installed but didn't detect hardware 
[*]Downloading the generic "Broadcom_bcm43xx_USB_32_64bit_v2" drivers and doing the same as above - no difference. 
[/LIST]
 
I'm on 14.04 and kernel 3.19.0-47-generic.

Any help would be gratefully received! Thanks :)

---

### Post by QDR06VV9 on 2016-01-30
See if this helps...[http://askubuntu.com/questions/394159/belkin-n600-usb-wireless-adapter-on-ubuntu-12-04](http://askubuntu.com/questions/394159/belkin-n600-usb-wireless-adapter-on-ubuntu-12-04)
Credit to chili555

---

### Post by celticwiseman2 on 2016-01-30
Thanks runrickus - I've tried this. 

Where chili555 says -
"It ought to report: bcmn43xx32 : driver installed     device (050D:615A) present"

I get - 
"bcmn43xx32 : driver installed"

No mention of the hardware, nor any flashing lights on the USB itself.

---

### Post by QDR06VV9 on 2016-01-30
This is the one I meant to send(Very Sorry) Too many tabs Open..lol
[http://ubuntuforums.org/showthread.php?t=1797795](http://ubuntuforums.org/showthread.php?t=1797795)
He has a file on the first page that needs to be downloaded..

---

### Post by celticwiseman2 on 2016-01-31
No need to apologise - appreciate the help you're giving :)

Same as before though, "bcmwlhigh5 : driver installed" and that's it. No Wifi.

---

### Post by QDR06VV9 on 2016-01-31
So it is being a stubborn one Huh?
It has been reported With Ubuntu 14.04 you can run this in the terminal:
```
sudo apt-get install ndisgtk
wget www.mediafire.com/?od9wpw6ccrnyhaa
unzip A6200_Linux_drivers.zip
sudo ndisgtk
```

Then when ndisgtk is running, choose the file ending in "ing" that was unzipped. It should be bcmwlhigh5.inf. Once that is installed you can select a wifi network from the Network menu-bar item.
Fingers Crossed:D
Kind Regards
Source: [http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04](http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04)

---

### Post by celticwiseman2 on 2016-01-31
That didn't work either, same issue - driver installed fine but no dice with the detection of the adapter. I've tried a few different USB ports as well, so I'm coming to the conclusion I should get another adapter. It obviously works fine in Windows.

Thank you very much for the help in trying to get this resolved but I should call it a day and buy an "out-of-the-box" job.

---

### Post by Vladlenin5000 on 2016-02-01
> **celticwiseman2 said:**
> That didn't work either, same issue - driver installed fine but no dice with the detection of the adapter. I've tried a few different USB ports as well, so I'm coming to the conclusion I should get another adapter. It obviously works fine in Windows.

Thank you very much for the help in trying to get this resolved but I should call it a day and buy an "out-of-the-box" job.


Exactly!

---

