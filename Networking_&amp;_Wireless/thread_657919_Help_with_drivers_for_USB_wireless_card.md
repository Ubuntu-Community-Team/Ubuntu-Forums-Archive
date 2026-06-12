---
title: "Help with drivers for USB wireless card"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by crashMMVII on 2008-01-04
Hey guys,

I'm trying to connect to my wireless network in 7.10, but in the System > Administrator > Network box, the only options I see are "Wired" and "Modem" connections, no option for wireless. Does this mean that I don't have the drivers installed?

I'm assuming this is the case, and I've found the following entry for my wireless adapter on the NDISwrapper sourceforge page:

> USB: US ROBOTICS USR805421 802.11g Wireless USB Adapter
Chipset:Unknown
usbid: 0baf:011B
Driver: Official U.S. Robotics [http://www.usr.com/support/5421/5421-files/5421-na.exe](http://www.usr.com/support/5421/5421-files/5421-na.exe). Unpack it and install driver with USR5421X.inf. This doesn&#8217;t copy the .sys files (.sys files for RNDIS driver are part of Windows, so they are not needed in Windows; however, driver for USR5421 distributes .sys files but they are not installed by .inf file); so copy RNDISMPK.sys and usb8023k.sys files into /etc/ndiswrapper/usr5421x directory as rndismpk.sys and usb8023k.sys respectively).
Other: Works with snapshot of 2006-02-13.
Other: With 2.6.16 and later kernels, RNDIS devices are not initialized (when device is plugged in, nothing happens). To get it going, you need to set the variable bConfigurationValue in sysfs. An easy way to do this is to add 

BUS==&#8221;usb&#8221;, SYSFS{idProduct}==&#8221;001b&#8221;, SYSFS{idVendor}==&#8221;0baf&#8221;, \ PROGRAM=&#8221;/bin/sh -c &#8216;echo 1 > /sys/%p/device/bConfigurationValue&#8217;&#8220; 

to /etc/udev/rules.d/z25_local_rules file and restart udev. Replace idProduct and idVendor as appropriate; for USR5421, &#8216;lsusb&#8217; shows 001b (idProduct) and 0baf (idVendor).

Can anybody post a step-by-step (preferably as simple as you can make it) on what I need to do to install this driver so that I can access my wireless? Keep in mind that I have basically no knowledge of Linux.

Thanks a lot!
crashMMVII

---

### Post by jan quark on 2008-01-04
please post the results of the following commands you can type into the terminal
```
lspci -v | less
```

```
iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```

these help to gather more pieces of information about your network status

---

### Post by crashMMVII on 2008-01-04
For the first one, I got a very long list of things that I could't figure out how to log or copy it. As for the others:

iwconfig:
```
lo        &#8236;no wireless extensions.

eth0      &#8236;no wireless extensions.
```

ifconfig:
```
eth0      &#8236;Link encap:Ethernet*  &#8236;HWaddr* &#8236;00:04:61:4E:0A:A7*  
          UP BROADCAST MULTICAST*  &#8236;MTU:1500*  &#8236;Metric:1
          &#8236;RX packets:0* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;frame:0
          &#8236;TX packets:0* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;carrier:0
          &#8236;collisions:0* &#8236;txqueuelen:1000* 
          RX bytes:0* (&#8236;0.0* &#8236;b*)  &#8236;TX bytes:0* (&#8236;0.0* &#8236;b*)
          Interrupt:20* 

lo        &#8236;Link encap:Local Loopback*  
          inet addr:127.0.0.1*  &#8236;Mask:255.0.0.0
          &#8236;inet6* &#8236;addr:* &#8236;::1/128* &#8236;Scope:Host
          &#8236;UP LOOPBACK RUNNING*  &#8236;MTU:16436*  &#8236;Metric:1
          &#8236;RX packets:16* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;frame:0
          &#8236;TX packets:16* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;carrier:0
          &#8236;collisions:0* &#8236;txqueuelen:0* 
          RX bytes:1184* (&#8236;1.1* &#8236;KB*)  &#8236;TX bytes:1184* (&#8236;1.1* &#8236;KB*)
```

sudo iwlist scan:
```
lo        &#8236;Interface doesn't support scanning.

eth0      &#8236;Interface doesn't support scanning.
```

---

### Post by crashMMVII on 2008-01-04
I followed the directions quoted in first post as best as I could, but when I try and do "sudo ndiswrapper -l" I get this:

```

rndismpk.sys &#8236;: &#8236;invalid driver!
usb8023k.sys &#8236;: &#8236;invalid driver!
usr5421x &#8236;: &#8236;invalid driver!
```

---

