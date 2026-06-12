---
title: "[SOLVED] Heron iwl3945 not connecting to wep"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by fishyf on 2008-06-04
I have a problem with the iwl3945 driver. I am not alone, this problem is well known, there are many posts and many bug reports but it has never been fixed.

Here is my problem: Wireless worked fine in Gutsy using the ipw3945 driver. The purists decided to get rid of the working driver ipw3945 driver and replace it with non working iwl3945 and sure enough, in Hardy Heron, it didn't work. Well, it could connect to an unsecured wireless AP but not a secured one.

There were many solutions on the web involving editing files and modprobing and going back to previous versions of network manager to using ndiswrapper. Really google for iwl3945 and hardy.

I tired many solutions, but none of them worked for me until I came across [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

I finally got a connection. Wow. I was ecstatic. For about 20 minutes and then the computer froze while it disconnected and tried to connect again.

Brilliant. I love open source. But a non working open source program is not a good replacement for a working closed source program. I love Ubuntu, but Hardy is now unusable on my computer. I cannot unreservedly recommend Ubuntu to my colleagues.

I know you should say that I should spend further hours wasting my time with ifup, iwconfig essid key, iwlist scan, blacklist lshw -C wait, where's wlan0 gone, ifcutter, change the source and apt-get backports. But some people use a computer as a tool to get work done. To help them save time, not to be a huge time sink.

By the way, it has become hard to find useful information on these forums because not only do you have many topics concerning the problem but each topic has many pages. Sorry, I know this post will worsen that situation.

Is this just a rant. I guess it is, but I want the problem fixed. Maybe ranting will work. I want it fixed so that when you update to the latest version of all the software from the official repositories then everything works. I feel bad about making demands from people who mostly work for free, but that is countered by the amount of time I have wasted because somebody decided that the working driver wasn't pure enough.

I have wasted enough time. I will uninstall this crap and go back to Gutsy. And I have wasted days reinstalling everything and trying to get wireless to work. I have waited months for a straightforward fix. Now I will go and cry.

---

### Post by fishyf on 2008-06-10
Well, I have this love hate relationship with Hardy. Although I gave up on the iwl driver, I decided to give ndiswrapper another go.

So I did and it now works fine (apart from occasional lockups that I hope to fix soon). I followed the instructions at [http://ubuntuforums.org/showpost.php?p=4790682&postcount=10](http://ubuntuforums.org/showpost.php?p=4790682&postcount=10)

The particular driver I used can be seen with:

ndiswrapper -l
netw4x32 : driver installed
	device (8086:4222) present (alternate driver: iwl3945)

You need to download the driver from Intel's website and then install using ndiswrapper -i netw4x32.inf
Otherwise follow the instructions from the above link.


The actual wireless device that I have is given by

lshw -C network

       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:a7:b4:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.52+Intel,03/13/2008,11.5.1.15 ip=192.168.0.4 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

---

