---
title: "Why can't a simple wireless USB Adapter Work with Linux?"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by ericyomi on 2007-12-31
Can anybody help me?
I have been trying for weeks to get a wireless USB adapter to work on Ubuntu 7.10 Gutsy Gibbon. Despite all my effort, I have not been successful.
I am a Windows user and in Windows getting a wireless USB adapter to work is an absolute no brainer. Why does it have to be rocket science in Linux? Why can't it just be Plug & Play?

I tried everything that was recommended from most of the forums I came across, initially using Belkin's Wireless G Adapter Part# F5D7050. I gave up after 4 weeks and bought the D-Link DWL-122 adapter, which claims to have support for Linux. I get intermittent connection to my Netgear router. But even when there is a connection to the router, I can't access the internet. On rare occasions, I have been able to access the internet a few seconds after the adapter connected to the router.

Can anybody get me out of my misery?
But more importantly, why can't the good people of Linux make simpler to add a wireless adapter to Lnux-based machine?
Any help will be appreciated.

---

### Post by finneces on 2007-12-31
I just recently got my Fritz WLAN USB to work under Ubuntu. See if I can help.
> **ericyomi said:**
> 
I am a Windows user and in Windows getting a wireless USB adapter to work is an absolute no brainer. Why does it have to be rocket science in Linux? Why can't it just be Plug & Play?

Because the hardware manufacturers design the drivers only for windows.  Its changing slowly, though.  More and more linux support is available and I suspect that after the ASUS EEE makes it big, more and more companies will make better linux drivers.  Lets just hope!

> **ericyomi said:**
> 
I tried everything that was recommended from most of the forums I came across, initially using Belkin's Wireless G Adapter Part# F5D7050. I gave up after 4 weeks and bought the D-Link DWL-122 adapter, which claims to have support for Linux. I get intermittent connection to my Netgear router. But even when there is a connection to the router, I can't access the internet. On rare occasions, I have been able to access the internet a few seconds after the adapter connected to the router.


So I assume you were able to get the companies provided linux driver and were able to install that?  For my Fritz, the company only provedes a linux driver for 32 bit architechture.  In the end I had to install the windows 64 bit and use a linux wrapper for it.  I followed these instructions and it seemed to work: 
[http://wiki.ubuntuusers.de/WLAN/NdisWrapper]("http://wiki.ubuntuusers.de/WLAN/NdisWrapper")

Its only in German, sorry!
Its another option to try, let us know if it works!

---

### Post by ugm6hr on 2007-12-31
For the DWL-122:

This explains that native linux driver only allows open / WEP networks:
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

Entry No 3 in this shows how to get WPA with ndiswrapper, but seems to suggest you have to plug the USB device in after booting...
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-122](https://help.ubuntu.com/community/WifiDocs/Device/DWL-122)

Sounds like you've already tried a variety of forum suggestions for the Belkin, but the reason it hasn't worked is probably that there are a number of revisions of this device, each with a different chipset.  Maybe if you post the output from the following command (with the device plugged in), someone might be able to help:
```
lsusb -v
```

---

### Post by ericyomi on 2008-01-01
I reinstalled Ubuntu and used the Synaptic Package Manage to install the driver linux-wlan-ng, which is supposed to work with the device according to the manufacturer.

After restarting the machine, the adapter was able to connect to the router only for a few seconds. I opened the Network Tools window and was able to confirm that wlan0 was configured and that an IP address had been allocated. Unfortunately, after staring the Firefox browser and clicking on an hyperlink, the connection to the router dropped and was subsequently lost.

I am not sure what to do now, since if the Ubuntu-ready driver cannot do the job, I am not sure what will.

Any idea?

---

### Post by Predator[23rd] on 2008-01-01
Hi!

> **ericyomi said:**
> I opened the Network Tools window and was able to confirm that wlan0 was configured and that an IP address had been allocated.

that is good but not good enough. It confirms that your hardware is being detected - and "only" a configuration problem is left.

type in **ifconfig** and check for your wireless lan adapter's (should be *wlan0*) configuration. if it shows something else then wlan0 and you are not sure what it is, check with **lsusb** which "name" your wireless usb adapter has and compare it with your ifconfig results.

last: check the */etc/network/interface* file for a DHCP entry with wlan0 ...

hope it works out.

---

### Post by madsmaddad on 2008-01-01
My 3com 3CRUSB10075 worked right away, no problems. Even when I upgraded from feisty to Gutsy. 

I am still having a few problems with WPA2, but hope that these will be resolved shortly.

---

### Post by ericyomi on 2008-01-02
I ran the commands ifconfig and lsusb immediately after starting up my machine. Everything looked fine:
- wlan0 looked properly configured with an allocated IP address
- lsub listed my USB device
- The network connection on the task bar at the of the screen showed a healthy connection to the router with a 74% signal strength.

However, this all falls apart when I start my Firefox browser and visit a page on the Internet. At this point, the signal strength drops to 0% and the connection to the router is subsequently lost and the only way to get it back up is to restart the machine.

I suspect that the problem is driver-related, since the connection to the router seems to drop only when data transfer via the device is initiated.

Since, Ubuntu 7.10 Gutsy ships with a driver for Belkin wireless G USB adapter, is it possible to find which models have been tested with the driver? is there a website where this sort of information is provided?

I think it would help if Ubuntu developers could recommend USB adapters and other wireless devices which they know work out of the box. This will save people like me weeks of time wasting. This can't be that difficult and I wouldn't be surprised if such a page already exists.

Any help will be appreciated.

---

### Post by kevdog on 2008-01-02
Get the connection established but do not go into firefox.

Go and type in the terminal

lsmod

Post the results here.

---

### Post by ericyomi on 2008-01-02
Hi Kevdog,
I ran the command as you suggested, find attached the results.

---

### Post by GTvulse on 2008-01-02
> **ericyomi said:**
> Hi Kevdog,
I ran the command as you suggested, find attached the results.


You have a Ralink r73 USB adapter, soooo:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28rt73%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28rt73%29)

---

### Post by ericyomi on 2008-01-02
dradul,
Thanks for your suggestions.
I when through the steps outlined on the website you suggested. I ran into the following problems:

1. The file rt73.ko ends up in the folder /lib/modules/2.6.22-14-generic instead of /lib/modules/2.6.22-14

2. The device no longer connects to the router and in fact when I try to bring it up using the ifup command, it fails. However, the iwconfig command results show the rausb0 as the wireless connection. But it is not configured.

3. When I click on the network connection icon on the taskbar at the top of the screen I now get "Unknown wireless interface" in the pop-up menu.

Any idea why I am getting the problems listed above?

The great news is my Belkin Wireless G adapter now seems to work and for the first time I am posting to the Ubuntu forums from my Linux-based machine!

However, I would be grateful if anyone could help me get my D-Link Wireless adapter working on Ubuntu machine.

---

### Post by GTvulse on 2008-01-03
The module location is as expected. That's the name of the kernel you are running in Gutsy. If the kernel changes you may need to compile the module again, if the version name changes. 

Hmmm.... I suggest you go to System->Administration->Network check your wireless interface (it would be identified as rausb0) and check roaming mode. From then on, use Network Manager to manage your connection. iwconfig is a last resort thing at this point in time.

---

### Post by Yfrwlf on 2008-01-05
> **ericyomi said:**
> Since, Ubuntu 7.10 Gutsy ships with a driver for Belkin wireless G USB adapter, is it possible to find which models have been tested with the driver? is there a website where this sort of information is provided?

I think it would help if Ubuntu developers could recommend USB adapters and other wireless devices which they know work out of the box. This will save people like me weeks of time wasting. This can't be that difficult and I wouldn't be surprised if such a page already exists.

Any help will be appreciated.

You may just need some specific guides for your hardware, but here is more general information for you, if it might help.

[https://help.ubuntu.com/7.10/internet/C/wireless.html](https://help.ubuntu.com/7.10/internet/C/wireless.html)

Here's a collection of experiences with wifi hardware, so you can get an idea of what hardware may work out of the box with this Linux kernel.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Lastly, this project has the vision of trying to provide more information about what works and what does not out of the box in Linux.  Unfortunately, it's not done yet. ;)

[http://www.dohickey-project.com/](http://www.dohickey-project.com/)

---

