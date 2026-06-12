---
title: "Linksys WUSB54GC no longer working!"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Echo35 on 2007-04-21
I'm repairing an old laptop and had to resort to buying a USB WiFi adapter, since the laptop had a broadcom chip in it originally. I bought a WUSB54GC from Staples, and after some hacking (according to the guide at [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)), it worked wonderfully well. So then 7.04 came out, and I formatted the laptop (downloading the update was taking much longer) and got 7.04 set up well. The only problem I am having is the WiFi. The network manager detects it, and even shows the access points, let's me click on them, and attempts to sign in, but to no avail. Something similar happened last time, so I figured I'd try the hacking guide again. It works ok until I get to the "make" part. I run "make" and get this:

$ sudo make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
/home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2065: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable ‘device’
make[2]: *** [/home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/mwalko/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

I have all the kernel headers and everything. I even tried a few different approaches to installing the ralink driver, but they all end up like this. What am I missing here? It was working before, so is it just something with 7.04? Also, how come the adapter's light blinks, and all the access points show and everything, but it can't log into any of them? This is extremely confusing.

---

### Post by p110011 on 2007-04-21
Yup, I am in the same situation. 6.10 edgy I compiled rt73 and it worked. Now I have enabled broadcast  essid so my usb stick can see the network but it just won't log in. Everything else is just working. I'm happy with that, but I want the wireless too.

---

### Post by cjv on 2007-05-02
It's no difficult getting that driver to compile under 7.04.

I'm talking by memory:

In rtmp_main.c search for the two lines where get_wireless_stats are used and comment the hole lines
In rtmp_info.c search for a struct definition called iw_stats (I'm not sure) and add (at the end, for example) an entry like this:

 .get_wireless_stats = rt73_get_wireless_stats,

Then the driver compiles and -I guess- works, but I couldn't manage it to work in WPA, so I'm not using it.

Does this driver provide WPA support on Edgy or earlier versions?

---

### Post by CFBauer on 2007-05-08
I'm working on WPA in Feisty as well.  RT73 worked fine with WPA in a previous distro I've used.  No luck yet, though.

[This person](http://ubuntuforums.org/showthread.php?t=254678&highlight=The+requested+wireless+network+requires+security+capabilities+unsupported+by+your+hardware[) is having issues too.  I tried the suggestion and no luck.

edit: My stick can see my network, but I get "The requested wireless network requires security capabilities unsupported by your hardware." when trying to connect.  My drivers are loaded with ndiswrapper just fine, there's no option to choose WPA, which worked in Windows and in my previous distro.

---

