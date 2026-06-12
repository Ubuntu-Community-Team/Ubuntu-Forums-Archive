---
title: "How To Install Netgear WNDA3100v2 in 14.04?"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by imacamper on 2014-04-20
I must be missing something simple.  I've read many posts and others are successful. I was running 13.10 in VMWare Workstation 10.  I've since upgraded to 14.04 LTS but no difference.  

I'm trying to install my Netgear WNDA3100v2 USB wireless adapter into my Ubuntu VM.  I've assigned the adapter to the VM and ubuntu sees it.  Here's a dmesg snip:

```
[  245.808717] usb 1-1: new high-speed USB device number 3 using ehci-pci
[  246.114403] usb 1-1: New USB device found, idVendor=0846, idProduct=9011
[  246.114471] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  246.114481] usb 1-1: Product: BCMUSB 802.11 Wireless Adapter
[  246.114486] usb 1-1: Manufacturer: Broadcom
[  246.114490] usb 1-1: SerialNumber: 2426
```

And lsusb:

```
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
```
I've tried both the native b43 driver and ndiswrapper using the files from this thread:

[http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)

However in both cases, iwconfig never shows a wlan0:

```
# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions. 
```

I have ensured that when using ndiswrapper, b43 modules are not loaded and vice versa.  What can I check to get this working?

Thanks for your help.

Cheers,

Drew

---

### Post by praseodym on 2014-04-20
Hi,

b43 will not work, there is no native Linux support for Broadcom-USB-sticks. Try this driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

---

### Post by nigel5 on 2014-10-26
The 'how to' that follows worked for me when I installed 12.04 and again when I upgraded to 14.04.  Try it!  [http://memphiscodingadventures.wordpress.com/2013/04/10/fatal-module-ndiswrapper-not-found-installing-windows-wifi-drivers-for-ubuntu-12-10/](http://memphiscodingadventures.wordpress.com/2013/04/10/fatal-module-ndiswrapper-not-found-installing-windows-wifi-drivers-for-ubuntu-12-10/)

---

### Post by fourdoops on 2015-07-06
I'm trying to follow this tutorial on 15.04 and can't find the "Windows wireless drivers" program mentioned in the last step. Do you know where the executable for it might be?

---

### Post by chili555 on 2015-07-06
> **fourdoops said:**
> I'm trying to follow this tutorial on 15.04 and can't find the "Windows wireless drivers" program mentioned in the last step. Do you know where the executable for it might be?Did you install it?```
sudo apt-get install ndisgtk
```

---

### Post by praseodym on 2015-07-07
You can run it from terminal via
```

gksudo ndisgtk
```

---

### Post by Forrest_Betton on 2015-10-08
i have a similar problem with ubuntu 14.04, but additionally, my ethernet connection is not being detected.  

I have been trying, unsuccessfully, to follow the thread [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)
to correct this, but is there an alternative method to downloading the Synaptic Package Manager App in the mean time?

---

### Post by chili555 on 2015-10-09
> **Forrest_Betton said:**
> i have a similar problem with ubuntu 14.04, but additionally, my ethernet connection is not being detected.  

I have been trying, unsuccessfully, to follow the thread [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)
to correct this, but is there an alternative method to downloading the Synaptic Package Manager App in the mean time?That thread is only 249 posts long! Which post? Which procedure??

I'd rather get your ethernet going first and then proceed. 

I suggest you start a new thread and tell us about the ethernet including:```
lspci -nnk | grep 0200 -A2
```

---

### Post by chili555 on 2015-10-09
> **Forrest_Betton said:**
> i have a similar problem with ubuntu 14.04, but additionally, my ethernet connection is not being detected.  

I have been trying, unsuccessfully, to follow the thread [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)
to correct this, but is there an alternative method to downloading the Synaptic Package Manager App in the mean time?That thread is only 249 posts long! Which post? Which procedure??

I'd rather get your ethernet going first and then proceed. 

I suggest you start a new thread and tell us about the ethernet including:```
lspci -nnk | grep 0200 -A2
```

---

