---
title: "USB modem with Network Manager?"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by jdpipe on 2008-09-24
Hi all

I recently had some help from a friend who showed me how I could connect to the internet from Ubuntu using my Nokia 3G mobile phone. This process required a new copy of the wvdial.conf file and some messing around with 'route' to get the connection up.

My question is: is it possible to make this connection somewhat automatic using NetworkManager, and is it possible to configure such a connection using only GUI tools, or does setting up a mobile-phone-as-USB-modem necessarily require some command-line action?

Cheers
JP

---

### Post by shanix on 2008-09-24
The feature is supported in the Network Manager 0.7 which will be included in the 8.10 release. If you would like to update the application to 0.7, you can do so by adding the following to the Software source:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main


Please also provide the info on the device by running the command:

lsusb

---

### Post by Redptc on 2008-09-24
I use GnomePPP, which is in Synaptics, and was straight forward to connect. It 'remembers' the settings and has a red phone as an icon so you can click the icon to make it start up each time. All GUI; no terminal action!

Telstra has Browsepacks that are not badly priced so I use the phone when away from home. I also find that Telstra's 3G is widely available in rural NSW and my connection works in some surprisingly remote areas. Fast too!

I have a different phone but that shouldn't matter much.

---

### Post by kdpem on 2008-09-24
I am new to Linux and am totally lost. I would like to use this OS but can't get past the usb phone thing. No sense putting Ubuntu on my main machine if I can't connect to the net. I use a motorola v3 usb phone as my connection on windows but no driver is available for Linux.

The fact that people are connecting using network manager is of no help to a newbee because enough information about what is needed is not in any of the posts I have read.

My phone company is useless when it comes to Linux and how to use there phone. Motorola may be giving information on how to use it but I have not found it, or maybe they have, and I don't understand what they are giving.

I have read where people are connecting using ppp, what do I need to know to connect this way?

Would someone make this information useable to a newbee or should I just stick with easy to use windows and forget learning linux?

Like I said, If I can't connect to the net, it would be foolish to mess with learning a new system.

Kdpem

---

### Post by Plumtreed on 2008-09-24
First off I had better explain that I am fairly new at this Ubuntu OS but I can tell you what I did to get my phone connected. My phone is a different brand, my PC is probably different and, by the sound of things, we are in different countries and therefore exposed to different ISPs.

If you connect with Windows you will probably be able to connect with Ubuntu! 

Network Manager is usually already installed and operating on your Ubuntu system. It is in the process of being 'improved' and, while a newish version is available now for testing, it may be used in the next release of Ubuntu.I didn't need it because this Gnomeppp, which does a similar sort of thing, did the job!

What version of Ubuntu are you running? Do you know how to go into 'Synaptics' to download GnomePPP?

---

