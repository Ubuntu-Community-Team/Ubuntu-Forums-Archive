---
title: "automatically install wireless drivers"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by IAMTubby on 2015-01-04
Hello,
 Whenever I newly install ubuntu on a machine, the first thing I do is to install wireless drivers since they're not there by default. I connect my machine to a wired network and then use the following commands. 

How can I ensure that wireless drivers are installed by default?
In the event that I do not have a wired network to connect to, how do I go about installing these drivers?

```

sudo dpkg --configure -a
sudo apt-get install firmware-b43-installer
sudo apt-get install b43-fwcutter
sudo apt-get remove bcmwl-kernel-source
sudo apt-get purge bcmwl*
sudo apt-get install bcmwl*
```

Thanks.s

---

### Post by grahammechanical on 2015-01-04
Ubuntu 7.04 was the first version of Ubuntu that I installed and the WiFi adapter has always had a driver automatically installed. I guess it depends on the particular WiFi adapter that is installed in the machine.

To avoid needing a wired connection to install wireless drivers you might consider setting up an off-line repository. Keep in mind that this may only apply to open source drivers. Proprietary drivers, whether WiFi or video may not be in the Ubuntu repositories. We may need internet access to get them.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Regards.

---

### Post by Ko_Char on 2015-01-04
I have an old laptop that requires bcmwl-kernel-source. Wifi works in LiveUSB mode. 
If I install it, the wifi doesn't work. 
The workaround is to enable "Install 3rd party software" during the installation step. 
Then wifi will work out of the box.
It will however install additional codecs.

(I don't remember whether I've to enable updates. The last time I did was for 12.04.)

---

### Post by chili555 on 2015-01-04
```
sudo dpkg --configure -a
sudo apt-get install firmware-b43-installer
sudo apt-get install b43-fwcutter
sudo apt-get remove bcmwl-kernel-source
sudo apt-get purge bcmwl*
sudo apt-get install bcmwl*
```Is this installation always on a laptop with a Broadcom wireless device for which the STA driver is appropriate? Or different laptops? The STA driver is appropriate for some, b43 and firmware for others and there are a few for which no method works at all!

If the STA driver is appropriate, then you needn't waste time and keystrokes installing the firmware.

Why would you purge and then install bcmwl-kernel-source?

Ole Chili is very corn-fused here.

---

